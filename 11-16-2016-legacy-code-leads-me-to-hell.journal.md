### Legacy Code Leads Me To Hell

> I wrote a piece of email to my boss to answer his question about a bug. Since I was earnest about it, so I just want to migrate it to my today's diary.

Hi Yee,

This afternoon I tried to use English to explain why the video injection doesn't show on some websites. And I know you are totally confused with my poor English spoken, I feel so sorry, and that makes me feel uncomfortable. Even though it is hard to explain even use Chinese, I still want to explain it again to you, and it is also a practice to me that using English to answer a complicated question.

During 2013 - 2015, most of the popular front-end technical architectures are based on 'Multiple Pages Website.' It is a traditional technical solution to build a website. Even today, there are still millions of websites are using multiple pages. Such as those we found that didn't show our injected video ads.

We all know front-end project needs to optimize its performance. In general, it is about code compression, code combination and a series of related tasks we call them build flow. You will find that in a 'Single Page Application' we usually only have one final javascript file. Even though it might be large, we only need load the file once during users access the app(SPA).

However, multiple pages website cannot do the same way. That's because each page we want to redirect will reload all scripts again. That's one of the reasons why a multiple-page website will load scripts separately.

Another important reason is that in software architecture, the best practice to maintain a large project is dicing the code to different bulks. We call the bulks Modules. A module could be separated by business logic, object-oriented design, and a particular architecture(e.g. we use Component Architecture in KDP). So that for a front-end project, there are dozens/hundreds of modules under the hood. In SPA, they could be combined to a final script. As for multiple-page websites, they don't have the similar condition to use the same way, so they have to load multiple scripts in every page of themselves.

Then the Question comes, if they have to load multiple scripts, how could they solve so many critical problems like circular dependency, lazy load, and concurrency order.

To solve the problem, Javascript Communities published more than three Modular Standards during 2013 - 2015. They are AMD, CMD, and CommonJS. They all are similar Modular Standard and have been implemented by a bunch of Module Loader libraries.

So the multiple-page websites we can see, they might use any of Modular Standards. If a multiple-page website doesn't use any modular architecture, it would be an incredible nightmare.

These content above are necessary knowledge to know our issue about why there are some websites didn't show the Video Ads.

Except for the part of websites that didn't show the Video Ads just because of bad network. Other websites all use AMD modular standard.

In our Injection code, we modified a famous 3rd-party library called Hammar.js and imported it to our code. The Hammar.js supports AMD/CMD/CommonJS and a global object(refer to 'window' in browsers environment).

Unfortunately, the guy who wrote the shitty code didn't know anything about the Modular Standard. He changed the Hammar.js, but he didn't implement the module of AMD/CMD/CommonJS. That means he just stuck everything into a global object(window). It is an amateurish way, and it has been proved dangerous code by communities.

The code of Video Ads uses the Hammer.js. That's why we cannot see Video Ads on some websites which are using AMD standard. When we access them, the Hammar.js will find the current website is using AMD, but our code doesn't implement the related module. So our code cannot find anything from the undefined/empty module. Then it breaks without any error.

At the mean time, I was shocked with there is no any code to throw or catch the related error, that's why we cannot easy to find the reason. Also, another shocking thing is our injection code will repeatedly be invoked every 25 ms if the bug is triggered! Only primary school student could write code like that.

I saw the code and feel there are many bugs will come in the future. And we will waste our time and difficult to find those bugs again and again. To fix bugs on it is even harder than rewrite a new one, it also will take more time. Quality takes some time. Right architecture takes some time. Project workflow takes some time. But all of them won't take us dive into hell at someday when we meet issues. So don't be short-sighted and don't think the shitty code works well. This terrible thought will take a technical company to die, and it also shouldn't be spoken from a real software engineer.

thanks,
Yang
