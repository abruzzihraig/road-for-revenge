Chook Talks With Duck
Our tester came up with an unreasonable requirement when she tested our work. She thinks as a user she expects that the size of drag&drop zone should be changed by a specific image size. What a silly thought I cannot believe it was put forward by our 'professional' tester. So I wrote an email to try to explain why it is an unreasonable requirement and why we should not implement it:

>For drag&drop zone. I think we don't need to make its shape related to a particular image size, which is unreasonable in component architecture. Before we reflect on whether a feature or an improvement will look better, we should think if it is reasonable first.

>At this scenario, the drag&drop zone as a better uploading component will improve the user experience. But it is basically an uploading component first. We should keep every component as possible as pure so that we could easily to maintain and reuse them in the future. That means the business logic should not pollute those components which have a single purpose, such as the uploading component.

>The shape of drag&drop zone is designed for helping user drag and drop their files handily. That's why the zone is big enough. If the size of the zone depends on a particular image size, it will bring us more issues on the stability of the project. For example, drag&drop doesn't know what the size it will accept from users' choice. If the size is small, it will make user inconvenient to drop the files. If the size is too large(I noticed there would be images has the size of 800x160), keep the same behavior will be unexpected and unreasonable in design. That's why we shouldn't implement the 'improvement.' Because If the further image size is accepted, then the rule of this improvement will be totally failed. And users may also feel confused with its changeful size.

>That's why I don't think it's a tradeoff or an improvement on user experience. Before we analyze the look and feel of a requirement from user's perspective, we should think about if it is reasonable first. The user finally will understand why we did like those rather than totally matched their thoughts at the beginning.

However, I received the reply like below:

>I understand. Thank you for your explanation.

>I would still like to run this by Kaveh/Yee at a later time as a design consideration for the future.

Am I talked with a duck? Why I need to take so much effort to try to persuade someone who doesn't care about my serious thought. Am I only a worker who always listens to the orders from others even the orders are incredibly foolish?

Only God knows what I am doing in this babyish but infighting company. And only one thing I can do is continue to stay in jail.
