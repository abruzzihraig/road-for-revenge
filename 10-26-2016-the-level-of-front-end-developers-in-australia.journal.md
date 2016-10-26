### The Level Of Front-end Developers In Australia
Even the Front-end world changes frequently. It still keeps outdated in Australia.

My friend Ryan asked me to help him analyze the interview questions from Kogan.com. He is applying for a Front-end job from the company.

Since Kogan is open for technical communities, so I have a good impression on it. Once I attended a meetup which organized by Melbourne React Community, and Kogan supported the space, supplied food and drinks for us.

When I got the interview questions from Ryan, I was surprised how easy the questions are. I even feel any front-end engineer in China has a little bit knowledge and experience could get the job.

There are four front-end questions. The first one is just like an 8-kyu-level challenge in Codewars.com. The second is about how to handle AJAX calls sequentially and parallel. That is so easy we even could find more than five different ways to make it progressively. The third question looks a little bit complicated because it related the knowledge prototype chain and object-oriented programming in ECMAScript 5. Does anyone remember what is ECMAScript 5? Even the description of the third question is so long. It is still easy to write. If we use the 'Function.apply' we even could have got extra points.

The final question is another joke. It describes a particular business situation on Kogan. The question asks us how to back and make the page which has a list view fixed to the previous position after users entered a specific item. How ironic question it is. Because I can see the issue is still in where we look up goods on Kogan.

The question is still not difficult to answer, and even we have to think about the browser compatibility. We could make the answer divided into two parts. One is to use History API for those browsers which upper than IE10. Another also needs to divide into two parts again. One for SPA architecture, another for traditional website multiple pages. For the SPA, we could save data globally to memory from list view before entered a specific item. If the architecture using multiple pages, we could use LocalStorage or SessionStorage to save the related data and scroll position.

Known even the Kogan make the simplest questions for the interview. I feel relieved:)
