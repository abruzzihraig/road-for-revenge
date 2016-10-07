### Do Not Set FLAG
At first, I have to celebrate that finally I got the platinum trophy at tonight. During nearly 300 hours the gaming time, I was really enjoyable. DarkSouls taught me lots of things. The most impressing point to me is that it taught me how to figure out a way to defeat any invincible enemy.

I will never forget the happy and the nervous memories. Treating any enemy equally is a philosophy of the series of DarkSouls, it also warns us we have to be serious to any challenge in our future life.

Another thing is I made a flag today. And it obviously is a bad result to me.

My boss was discussing with our clients these days in Tokyo. He showed our project KDP to them to sell. In the morning, he sent an email to us, and he said he felt we haven’t minified our front-end code in the demo server.

Then I replied confidently that we have already minified code since the first released version. I vowed it with multiple web optimised features that we’ve already done. I even said I thought our project has an industry standard on web performance. I showed him two more optimising ways like CDN or make 3rd-party libraries chunked, and I told him I think the current performance is enough for this phase or just the demo. No one need to worry about it.

After I showed my knowledges off, I tried to rethink why he thought the code hadn’t been minified. I saw the final file after handled by UglifyJS and some other optimised plugins, it was nearly could not be read. However, I noticed there were so many variables hadn’t been mingled. It is so weird.

I took much time on it to find why the variables cannot be mingled by UglifyJS. Finally I knew from the document of UglifyJS that it cannot mingle code from ‘eval’ expression in Javascript. Yes, our final compressed file used the ‘eval’ expression with a property ‘devtool’ on the webpack config. The property ‘devtool’ shouldn’t be there when we using ‘dist’ mode to compile the final code for production environment.

That’s a totally mistake was made by myself. It made me so ashamed, especially when I saw the actually minified and mingled code after I fixed the problem.

So I decided to say sorry to my boss about that. Hope he could forgive my stupid words.

This experience taught me do not make a flag if you haven’t to investigate a problem. Otherwise, if you are wrong, the shame will always be with you.
