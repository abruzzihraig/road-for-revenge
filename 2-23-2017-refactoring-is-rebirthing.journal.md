### Refactoring Is Rebirthing
Long time no stays on my chair a whole night. I paid my attention to how to refactor the code recently I wrote.

I combined the two independent animations on the peel insertion. Each animation is a huge class which includes a few canvases. At the early stage, I wrote them just for easy to control more states. But for now, I have already got each part that I could improve. So the two groups of canvases are combined to the only main canvas. All of the other canvases just keep off-screen and finally are drawn on the main one. It depends on what state the animation is.

I paid more time on how to make the functions as single as I can. I also made them more readable than before. It is a complicated question in the code, that is what kind of variable should be mutable or immutable. Also, to decide whether a variable is a property belongs to the main context or just belongs to a partial context, it is another thought-provoking issue.

It is still not the best, but I think it could get 90 scores at the moment. At least, if anyone who never saw the code before needs to understand or maintain it, it won’t be a high wall.

I actually enjoyed the time I spent on refactoring. How to construct the code and reduce the complexity is art and philosophy. But I’m not mean that I could be a good programmer who is indeed good at refactoring.
