### Long May The Gettext
I have to say the GNU Gettext is the best i18n solution I have never seen before.

Actually, at the end of my last work, my team had already used the Gettext to handle multiple languages then. But I didn’t do anything core about it, so I just remembered that is a kind of multi-language solution.

This week my task is to integrate a i18n solution to our project. Since I have already known the Gettext is the well-known standard, so how can I stand using a silly flow by writing different languages on an Excel?

So that in the afternoon, I tried to add two loaders about Angular Gettext to the Webpack flow we have already used. One loader for extracting language keys from our code, another for compiling language map files into the original code. That is easy to understand the whole cycle.

The files we need to edit are called PO files. Any PO file could be one of languages that used to a project.

And there is another important file named POT. The POT file is a template that created by extracting all of essential key words from the code. Anytime you defined a new word in code need to be translated, the POT file would be updated automatically by the Webpack flow. That’s the loaders’ credit.

The rest thing you need to do is just to update PO file from the template POT, then the PO file will add some new fields could be translated. When you edit the new fields and save it, the Webpack will do us a favour to compile them into our code again. So that you can see the change immediately on a browser.

The whole process is friendly without any pain. There is another incomparable feature is that you even could use a true human translating in the editor Poedit. That means every key word you are translating could be used for fetching a list of translation suggestions from cloud. Even if more suggestions are hidden unless you get a pro version. I think that is enough for translating.

How perfect solution for the multiple languages, I wish anyone who has the same requirements about internationalisation could try it. Then you will be grateful and satisfied.
