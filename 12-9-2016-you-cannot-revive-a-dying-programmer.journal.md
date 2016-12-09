### You Cannot Revive A Dying Programmer
About Three months ago, I got a requirement for deploying our project from backend developers. The requirement is they need a separated config file which should not be included in the final bundle file. That means the separated config file cannot go through the build flow of Webpack to do some tasks such as compression and combination.

The requirement actually doesn't make sense all the time. I asked those guys many times why we cannot use different environments by adding some parameters in our build scripts so that we could just easy to compile the same project with different settings. However, those guys don't like anything about CLI. They don't care using which way to do it will be better.

Since I really don't want to do some silly works like this, so I put off the task until today.

At first, I just created an individual config file to hold those keys about API or region settings. All the configs have a fallback to the environment which registered in our computer before. So that if you don't have an external config file, the application will work with the setting which you specified in your computer—also they are written in different ENV config files.

But I changed my mind immediately. That's because the separated file might be able to make a cache issue—user may not get the latest config if there is a cache on the server. Since we've used Webpack, if we don't follow the rules of Webpack workflow, we might get some limitation there. For example, the final bundle file is easy to add a hash as a postfix to bust cache, but it's not easy to just give the same hash postfix to a separated config file, which also shouldn't go through the process of build workflow.

Even if I could find some ugly ways to make it possible that add the same hash as the postfix for the separated config file. If the backend guys just want to keep lazy and only change the separated config file without compilation in the "dist" folder, then they just deploy the code to the server again, all things will be broken.

So I just move the code of the separated config file to inline script in the index.html. Yet I still got an answer "no." They even didn't want to see my code and just kept their stupid solution as a bible. How can I do in the fucking team? There is always a dictator with his silly ideas to prevent me from doing something normal or better.

We may argue about one hour for the issue. I just put the scenario like what I mentioned above to those guys. And they seemed got what I worried. Then a guy told me, he could compile all code before he changes the config file so that we don't need to worry about if the cache doesn't update.

It sounds right uh? But if we have to compile everything before changing the individual config file, why we need the file itself? I was totally devastated because everything returns to my initial recommendation which from three months before. I asked them again, "why don't we use a standard way to handle the different environments like many other companies?" They just quibbled to me and gave me an answer "you have to do it like what we said."

Can you feel that? I just want to fuck the team and fuck the dying programmers. When can I get rid of those people? Only God and the warden knows.
