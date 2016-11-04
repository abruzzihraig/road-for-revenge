### Right Way To Use @font-face
It is a technical journal.

We all know that in CSS we can use @font-face to load the font which we want to use on our website. And fortunately, it is even supported by IE6. So that is always a useful function for our CSS code.

Since I worked in China, and there were few chances to use the feature on our product. That's because any Chinese font set is too large to use on a website. There is no one could accept to download a dozen of megabyte from font data before they can see the web page.

Once I used the feature in my graduation product, which is cutting Chinese font set off to the small subset to load. It will improve the download speed hugely. But I don't want to talk about it today. I just want to talk about the general usage.

Since two months ago. I've written a handy mixing function in Stylus for handling which font-family would be used for any of the multiple languages.

It looks like below:
```
$EN-fontset = 'OpenSans Regular', Helvetica, Arial
$JA-fontset = 'Noto Sans CJK JP', 'Hiragino Kaku Gothic Pro W3', 'Hiragino Kaku Gothic Pro', Osaka, Meiryo, 'MS PGothic'
$ZH-fontset = 'PingFang SC', 'Nato Sans CJK SC', 'Hiragino Sans GB', 'Microsoft YaHei', 'WenQuan Yi Micro Hei'

/*
 * i18n Font Family Mixin
 *
 * Usage:
 * body
 *   $i18n() // without parameters
 *
 * h1
 *   $i18n: 'OpenSans Bold'
 */
$i18n()
  if (length(arguments) > 0) {
    $en = arguments, $EN-fontset
    $ja = arguments, $EN-fontset, $JA-fontset
    $zh = arguments, $EN-fontset, $ZH-fontset
  } else {
    $en = $EN-fontset,
    $ja = $EN-fontset, $JA-fontset
    $zh = $EN-fontset, $ZH-fontset
  }

  &:lang(en)
    font-family: $en
  &:lang(ja)
    font-family: $ja
  &:lang(zh)
    font-family: $zh

  &:lang(ja)
  &:lang(zh)
    if (length(arguments) > 0 && match('Bold', arguments[0]))
      font-weight: 600 // Bold
    if (length(arguments) > 0 && match('Semibold', arguments[0]))
      font-weight: 500 // Semibold
    if (length(arguments) > 0 && match('Light', arguments[0]))
      font-weight: 300 // Light
    if (length(arguments) > 0 && match('Italic', arguments[0]))
      font-style: italic
```

And how I load those custom fonts by @font-face:
```
$fontSet = {
  'OpenSans Bold': 'opensans-bold-webfont',
  'OpenSans Regular': 'opensans-regular-webfont',
  'OpenSans Light': 'opensans-light-webfont',
  'OpenSans Semibold': 'opensans-semibold-webfont',
  'OpenSans Italic': 'opensans-italic-webfont',
  'OpenSans Light Italic': 'opensans-lightitalic-webfont'
}

for font, filename in $fontSet
  @font-face
    font-family: font;
    src: url('./assets/fonts/' + filename + '.eot');
    src: url('./assets/fonts/' + filename + '.eot?#iefix') format('embedded-opentype'),
    url('./assets/fonts/' + filename + '.woff2') format('woff2'),
    url('./assets/fonts/' + filename + '.woff') format('woff'),
    url('./assets/fonts/' + filename + '.ttf') format('truetype');
    font-weight: normal;
    font-style: normal;
```

You may feel the $i18n has a redundant logic, but never mind. You don't need to care about if it is elegant. Because the way I chose is already wrong.

In this usage, for each element which I want to apply a different font-family I have to add a mixin like `$i18n: 'OpenSans Semibold'`. Then the element will get a series of font set started with the `OpenSans Semibold`.

Is that weird, isn't it? At least I felt it so bizarre. But I didn't have time to figure out what is the right way to use then.

In this afternoon, after we released the weekly version, I finally could refactor the way I used.

After searching how Google Fonts display when zipped various font style in the same font family. I found it only use one font name as the name of @font-face, but load different font resource with diverse `font-style` and `font-weight`.

So I changed my iteration logic on @font-face to:
```
$fontSet = {
  'OpenSans Bold': {
    filename: 'opensans-bold-webfont',
    weight: 700,
    style: normal
  },
  'OpenSans Regular': {
    filename: 'opensans-regular-webfont',
    weight: 400,
    style: normal
  },
  'OpenSans Light': {
    filename: 'opensans-light-webfont',
    weight: 300,
    style: normal
  },
  'OpenSans Semibold': {
    filename: 'opensans-semibold-webfont',
    weight: 600,
    style: normal
  },
  'OpenSans Italic': {
    filename: 'opensans-italic-webfont',
    weight: 400,
    style: italic
  },
  'OpenSans Light Italic': {
    filename: 'opensans-lightitalic-webfont',
    weight: 300,
    style: italic
  }
}

for fontName, font in $fontSet
  @font-face
    font-family: OpenSans;
    src: url('./assets/fonts/' + font.filename + '.eot');
    src: url('./assets/fonts/' + font.filename + '.eot?#iefix') format('embedded-opentype'),
    url('./assets/fonts/' + font.filename + '.woff2') format('woff2'),
    url('./assets/fonts/' + font.filename + '.woff') format('woff'),
    url('./assets/fonts/' + font.filename + '.ttf') format('truetype');
    font-weight: font.weight;
    font-style: font.style;
```

In this version you can see, we only need to specify the common font family 'OpenSans' but use different font-weight and font-style to decide which font will indeed be adopted.

The logic becomes clear to us. Then let's look how should we refactor the $i18n mixing function.

Since we don't need to specify any particular font-family as the first font on each element, so the `arguments` for us is only indicating which font we finally want to display.

Therefore the code could be reduced to:
```
$i18n()
  $en = $EN-fontset
  $ja = $EN-fontset, $JA-fontset
  $zh = $EN-fontset, $ZH-fontset

  font-family: $en // $en as a fallback for all the other languages
  font-style: normal
  font-weight: 400

  &:lang(en)
    font-family: $en
  &:lang(ja)
    font-family: $ja
  &:lang(zh)
    font-family: $zh
```

By the way, I suppose there is few people know the pseudo 'lang'. It is an excellent way to handle the internationalization in CSS.

So good so far. And then, we could match the value of $i18n to a correct font:
```
  if (length(arguments) > 0 && match('Regular', arguments[0]))
    font-weight: 400 // Regular
  if (length(arguments) > 0 && match('Bold', arguments[0]))
    font-weight: 700 // Bold
  if (length(arguments) > 0 && match('Semibold', arguments[0]))
    font-weight: 600 // Semibold
  if (length(arguments) > 0 && match('Light', arguments[0]))
    font-weight: 300 // Light
  if (length(arguments) > 0 && match('Italic', arguments[0]))
    font-style: italic
    font-weight: 400
```

How nice it is. The final function has been improved like:
```
/*
 * i18n Font Family Mixin
 *
 * Usage:
 * body
 *   $i18n() // without parameters
 *
 * h1
 *   $i18n: 'Bold'
 */
$i18n()
  $en = $EN-fontset
  $ja = $EN-fontset, $JA-fontset
  $zh = $EN-fontset, $ZH-fontset

  font-family: $en
  font-style: normal
  font-weight: 400

  if (length(arguments) > 0 && match('Regular', arguments[0]))
    font-weight: 400 // Regular
  if (length(arguments) > 0 && match('Bold', arguments[0]))
    font-weight: 700 // Bold
  if (length(arguments) > 0 && match('Semibold', arguments[0]))
    font-weight: 600 // Semibold
  if (length(arguments) > 0 && match('Light', arguments[0]))
    font-weight: 300 // Light
  if (length(arguments) > 0 && match('Italic', arguments[0]))
    font-style: italic
    font-weight: 400

  &:lang(en)
    font-family: $en
  &:lang(ja)
    font-family: $ja
  &:lang(zh)
    font-family: $zh
```

That's what we expected! May my trap guides your way.
