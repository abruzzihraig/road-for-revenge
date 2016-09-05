### Shitty Work During Development
I was effective today, I was happy and nothing blocked me on my work until 5 p.m.

My last task is to implement a feature that could use two buttons to control the order of objects which drawing in a Canvas stack. It should be easy to achieve, I even thought it just need to take me 5 minutes.

But I was wrong. I met an annoying issue when I was trying to develop it. The problem is when a user selected an object, for example an image on the canvas, the object will be the front of all of objects. That was unexpected. Because if the user has already selected an object, then he/she won’t see the changes when the two layer buttons are clicked. The selected object will stay at the top of all of objects until the selection is cleared.

I don’t want users cannot see the changing process when they clicked the layer buttons then suddenly get a result they don’t want when the selection is released.

I have used the underlying library Fabric.js, and I know it shouldn’t have this behaviour as default. So I have absolute confidence to consider there are a couple lines of code control this logic in our plugin code. Actually, the plugin code is purchased from a plugin platform, and it has a bad quality. I have to read them painfully to add new features.

However, I nearly took 2 hours on finding where are those code. I don’t know what is the key API method on that, so I have to read the code line by line. It made me angry.

After this 2-hour boring barren work, I became to think if it is a default behaviour in the latest version of the underlying library Fabric.js. I tried a demo immediately on the JSFiddle, and it is indeed a default behaviour.

You cannot find the new change on their documents, and you may also won’t see how to control the behaviour by a parameter if no one posted an issue. What the fucking kidding, it took me 2 hours! I should be at home and doing my personal affairs.

The shitty work ruined my good mood.
