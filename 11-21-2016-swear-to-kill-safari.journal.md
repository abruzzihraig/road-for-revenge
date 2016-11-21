### Swear To kill Safari
'Safari is another Internet Explorer' is not a joke. I paid a whole day for a weird issue on iOS Safari. And now I still don't have any clue on it. I almost get insane.

The issue mainly occurs on my Boss's iPhone 6 Plus. When use his iPhone 6 Plus to access my website, and fetched an artwork list then try to open one of them with the image editor, the website will break and reload suddenly. It initially didn't show on my iPhone 6S. I guessed that's because my iPhone 6S has a more powerful hardware than iPhone 6 Plus, and maybe the iPhone 6 Plus breaks due to lack of RAM.

However, I borrowed iPhone 5 and iPhone 5C from other colleagues to try to test the issue, and they both didn't get crashed unexpectedly. The result totally confused me: Why the iPhone 6 Plus will break more frequently but iPhone 5 won't?

As I mentioned above, iPhone 6 Plus will break almost every time. But that doesn't mean the iPhone 5, iPhone 5C, and iPhone 6s won't crash. They just occur the issue with a lower frequency.

The most complicated problem is that the issue occurs randomly. When I fetch more than 100 artworks data(each item only includes some necessary data), all devices will have a high frequency to crash. The iPhone 6S is relatively safe.

When I try to fetch 20 artworks data, the device iPhone 5, iPhone 5C and iPhone 6S won't break except for the iPhone 6 Plus.

When I try to get only five artworks, all of them will be fine. Of course, it is a relative 'fine.' There is no way to prevent the crashing entirely.

Don't think the weird issue just occurs in the process when fetching artwork data. When we try to fetch 20 artworks and every device looks fine, then pick up one of them and open it with the Image Editor, you will see the iPhone 6 Plus will totally break. As for iPhone 5 and iPhone 5C will have a medium frequency to crash. Only iPhone 6S will live longer.

In Chinese, we call the issue bug of mystery. I know when open image editor, it will load a JSON object with a base64 dataUrl, it will occupy more memory in a browser. Most of the time the iPhone 6 Plus crashes on this step. After edited the final artwork and ready to save and close the image editor, the image editor will export dataUrl from the canvas. And that would be another memory-waste operation. It will make some iPhones crashed as well.

It sounds like the memory runs out, right? But after my friend Dolphin helped me to reduce the memory usage with Blob object and window.URL instead of base64 dataUrl. The crash issue still occurs randomly. I even want to buy my boss another new iPhone. Why does the fucking Safari on iPhone 6 Plus have such thorny problem? Why doesn't Apple care about its shit? I nearly took seventy percent of the time to find and to fix the issues on Safari in this project.

Am I wrong to make the content rich? Why you Apple with your shitty Safari always obstructs we front-end guys to build a website better? Why you always have so many issues on your platform and turn a blind eye on it?

I will witness you collapse at someday.
