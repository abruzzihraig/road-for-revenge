### Summary Of Kakku Front-end Technology
According to the demand of AUS government, we need to give it a technology summary for the last financial year to get funding for the next year. So my boss gave me the task to write something for summarizing the Front-end technologies we used in the last year. It is sincerely recorded in the following article.

During the year 2016 - 2017, our Kakku Front-end team created a series projects that have full of fantastic technologies. The most representative projects in those work are the three – KISS Insertion, Kakku Microsite Builder, and Kakku Publisher Portal. We will mainly focus on the first two projects in this summary.

KISS Insertion:
The project KISS Insertion is one of our core products. In brief, it is a project that will inject advertisement to a browser of the user whose smart device is connected with our KISS server. If a user has accessed in our KISS server and is going to look through a website which is using HTTP instead of HTTPS, our KISS Insertion scripts will be injected into this website, then drawing or loading a specific advertisement as our advertisement configs in KISS server.

Currently KISS Insertion it supports four kinds of advertisements, which include Image, Video, Icon, and Peel.

We used to have an old version of the project KISS Insertion, but it has terrible code maintainability and bad performance. The Video advertisement cannot auto play on a user device, and the Peel advertisement is just an animation composed of four images switching to mock, which means it has deficient performance about 4fps. Except for that main issues, for other types of advertisements, there also were a bunch of bugs cannot easily be fixed due to the terrible code maintainability. So we finally decided to create a new KISS Insertion instead of refactoring the original one.

In this year, it took us some time to create the new KISS Insertion. We introduced a stack of popular and advanced front-end technologies to this project. It mainly includes the following parts:
- TypeScript(using TypeScript we got strong type and high code maintainability, it reduces errors could occur during we modify a part of existing code)
- Pure DOM API(we don’t use jQuery anymore as the native DOM API is robust enough for our insertion handling. This reduces our final code size 20% or more)
- Canvas(totally drawing a complex flipping animation by mathematics and CanvasAPI instead of the poor image animation. The new performance is improved up to 60fps)
- CSS hardware acceleration(make all of our advertisement animation smoother up to 60fps)
- Stylus(a kind of CSS preprocessor could organize CSS with a better way for reusing and mixing)
- Webpack(we use Webpack to do everything about workflow, it speeds up our development environment and makes everything automatically, especially for the last stage compiling and bundling)

Along with the feature video autoplay of iOS 10 comes, we finally made the Video advertisement could auto play in popular platforms Windows, Mac, iOS, and Android.

It is a huge upgrade for KISS Insertion, no matter what for performance or code maintainability.

Kakku Microsite Builder:
This project we called it KMB is created in late this year. It is a revolutionary product for our company. It will basically free people who want to build their personal or their company’s website. Ideally, you don’t need to have any knowledge about coding to create your website via this builder. The builder in technically it is a kind of WYSIWYG(what you see is what you get) editor. You can operate the builder with some simple interactions like dragging or selecting to create and adjust the website you want, and you can review it at the same time.

For this revolutionary product, it has incredibly complex technical requirements. We are still working on the early stage, but we have already got some significant achievements:
- WYSIWYG editor(the website builder that users can interact with)
- Time Traveling(save different snapshots for undo and redo)

Here are what technologies we used for implementing these amazing work:
- TypeScript(mentioned in KISS Insertion)
- React(using React can make us focus on the state change in a complex application. It reduces the code DOM manipulation written by us and uses its virtual DOM to batch update state changes to the real DOM. It greatly improves the performance of our builder such rich interactive application)
- MobX(as a state store, MobX it has fewer boilerplates than Redux. It is friendly to our small front-end team. The key feature of MobX is TFRP(functional reactive programming), it could simplify our code as much as it can. Since it is a state store, it is possible to make us implement the amazing functionality Time Traveling for our builder)
- MST(MST is mobs-state-tree. It is an opinionated and transactional architecture for MobX. It is designed as what architecture we want to design for our models in the builder. MST is based on an immutable and memory shared tree, which means we can store different snapshots as much as we want. It wouldn’t take much memory, and that’s why our Time Traveling can be such fast)
- Webpack(mentioned in KISS Insertion)
- Stylus(mentioned in KISS Insertion)

We are still working on another core portion of KMB – parser for generating structured data to a real website. It will come soon in 2017.
