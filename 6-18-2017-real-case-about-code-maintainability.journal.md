### Real Case About Code Maintainability
I wrote an email this afternoon for a real case that I was stuck by a terrible code design. It basically expresses how I think about the influence of maintainability from a bad design.

Hi guys,

I just want to give you a real case for how a bad design wastes our time to maintain and debug.

Remember the multilingual parameters for KS Injection that Ruby handled? I said that is a terrible design but I cannot easily to figure out a real case for describing why it is dangerous at that time. And Ruby said we wouldn't change the URL format in the future, so don't worry about it.

But I don't agree with that human promise in programming all the time. The bad design will introduce more unpredictable issues, and today I met one of them. I also want Leila knows that is not my perfectionism. So please don't think I just don't want to make code messy. The maintainability is important in our work, a bad design may take a half work time or more when we debugging for those issues that shouldn't have occurred.

The logic of parameters from the backend is confusing.

1. Peel Insertion will inject an iframe URL from our backend. 
In default language, it has a format like http://xxx.com?id=asdf.
But in multilingual languages, it has a format like http://xxx.com?id=asdf&lang=en

Note in 1, it seems like a small difference, and maybe it doesn't matter for the whole system. but it actually makes the related code be complicated more like below:

2. Peel Page will get the parameter 'id' from the iframe URL above to fetch data of the peel page itself. And then, Peel Page will use another parameter 'lang' to decide what data should be used by the specific 'lang'.

3. As you can see, the default link it doesn't have a parameter 'lang=default', so Peel Page won't know if it should load data from 'default' Even though we can get another parameter 'forceLanguage' from the high-level overlay(but we cannot get it from Page Peel directly), the forceLanguage only exists in Preview Mode.

4. So at that time, I recommended to either remove the parameter 'lang' from the step 1 or give the default link a parameter 'lang=default'. But I got an answer that is we cannot.

5. Actually, as Kaveh said, all the parameters for Peel Page should only be controlled by front-end, that mean the front-end Peel Insertion should handle all the parameters for Peel Page. With that way, there even shouldn't have a parameter 'id' for those links from step 1. But the terrible design makes everything confusing.

6. So I compromised with that bad way, and I added a parameter 'lang=default' for the default link in step 1. Ruby and Kaveh asked me it is easy but why I don't want modify it. I said it is about maintainability but I cannot give you an example of how the modification will introduce new issues.

So the fix was like:
Inline image 1

Note in URL, the first parameter starts with the symbol '?', and the second starts with '&'. Since the 'overlayIframeContentUrl' it already has a parameter '?id=xxxx', so I just plus the '&lang=default' for the default link.

I know that is not precise, but make it strict in front-end means I have to write more code only for a design problem that should have been thought at the beginning when backend does it. And if I do more validations there, that will introduce more cases that I need to test and debug. It's another maintainability issue.

So far so good, we just used this patch way to fix the problem that we met. And it took me one day. Because figured out the confusing logic took me a lot of time.

However, today Yee has an urgent requirement for displaying peel insertion demo for our customers. And Yee gave me a new link for replacing the peel content. I thought that is easy, I just need to change the configurable property of 'INSERTION.overlayIframeContentUrl' for demo environment. It wouldn't take more than 3 minutes I supposed.

But I didn't remember that 'overlayIframeContentUrl' will be applied '&lang=default', and I also didn't notice that the link Yee gave me it doesn't have the first parameter like 'id=xxx'.

Guess what? I tested the change I made for the urgent requirement in Chrome and it worked fine, so I uploaded/deployed the new changes to the S3 demo site. But Yee said he cannot get the content. And I proved it again I said that must work fine, maybe Yee needs to clear cache or something. And Yee also let his customers do the same thing and they all failed.

So I tried the new demo website in Safari and Firefox, and I found different browsers have different behaviors. Finally, it took me much time to find the reason just because the normal link ends with a wrong string '&lang=default'. It shouldn't have this issue, but why it comes today?

I took 1 hour to figure out and fixed the urgent issue, and at the same time, I think it may cause some influences to our customers. I think you guys now understand what am I trying to say. The terrible design couldn't just use patches to rescue if we always ignore the root of an issue, and we shouldn't always using patches for those terrible and irresponsible design instead of solving the issue use a right way or refactoring. If we live in that unpredictable code from patches, we will use our half work time in the future day by day just for solving those bugs that look simple and can be fixed just by changing only one line code.


thanks,
Yang
