### Stuck By Handling SVG
I got stuck by inserting SVG into my website builder. It nearly took me a whole day to such work. You cannot easily insert raw HTML into React, but that is not the hardest part. The problem here is you won’t know what SVG format is by users uploading. If you just insert the whole SVG into your React, you wouldn’t control the style on the SVG itself. That means you need to extract those attributes from the original SVG string, then apply those attributes on the new SVG element that created from React.

I tried that way, but I always get some render issues during the SVG creating and attributes applying. So I tried a library which called React-SVG. It basically just receives an SVG file path, then uses another library SVGInjector to fetch the SVG file, then parse it and inject some styles to the new content. Using that way is more clear than the first way, but both of those libraries are not good enough for my requirement. I used a whole afternoon and even worked overtime until 8 p.m. to change some functionalities in the forked repos of these both libraries.

Before I did the work today, I thought the feature to control SVG as a kind of images should be easy, but it took me much time. That’s why sometimes estimate time consume is hard for our developers.