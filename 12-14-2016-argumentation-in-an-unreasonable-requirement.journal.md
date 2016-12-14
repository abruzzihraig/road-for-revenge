### Argumentation In An Unreasonable Requirement

>Just record a boring argument with our tester. The tester wants me keep an auto-generate ad title as {adType MM/dd/yyyy hh:mm} (e.g. “Small 12/23/2016 12:54“). And I nearly got insane with the silly requirement.

I'm totally opposed what you said.

It's not just about if we could implement it, and also it is how we design and maintain the product.

If for each requirement we just accept it without thinking and implement it directly, I could say I can implement everything by your requirements. I really want to spend a whole afternoon to argue with this obvious issue.

For the 1, please thinking why we have this auto-generated title? The title should be an important info which defined by users. And for preventing they stuck from the validation which could block them to go to the next page, then we add an auto-generated hash title as a placeholder for better User Experience. This is why it was brought here.

If it is a normal user, and he/she cares about their ads and they really want to manage the ads, they won't create any duplicated title because that would make them confusing someday. And that is also why we used the UNIQUE ID for generating those titles.

And now, you think the title is not user-friendly so require us to make it semantic. Yes, it is reasonable, but please note how the requirement steps up? And what is the basic reason for it exists? It is a UNIQUE and AUTO-GENERATED title as a PLACEHOLDER for preventing blocked users from the form validation, rather than making it user-friendly and making it as semantic as possible.

If a user really cares about the perfect semantic value format like "Small 2016/09/12 23:12:22", why they didn't create it by themselves? The placeholder just includes a part of the important and semantic information to help those users someday they actually need those information–those users who are lazy and don't really care about and manage their ads.

If they actually need the information someday, I don't believe they cannot get them from a title like {320x50-2016-09-12-23-12-22}.

And why I think it shouldn't include SLASH, COLON, and the SPACE among them? That's because I just do more fortifications for preventing changing our code if someday we get a new requirement which influenced by it. Have you seen any format like {Small 2016/09/12 23:12:22} as a filename in your file system? Have you seen the format in URL? Have you seen the format in any username or a form placeholder? The format {320x50-2016-09-12-23-12-22} is program-friendly, it could be parsed easily by any new requirement, and it also prevents some side effects without the special character. If we need to host them someday in a file system, it works fine, and each title by the same user is unique.



For the 2, this is an absolutely bad idea to me that to use the inaccurate words such as "Small" or "Large" to indicate different Ads type. What is the "Small" and what is the "Large"? They are relative units for measuring. Imagine if we have two Ad types like "300x200" and "200x300", could you tell me which is called "Small" and which is Called "Large"? If we add a new Ad Type "800x600", You said maybe we could make the "800x600" "Large" and change the previous "Large" one to "Medium", but can you feel the risk to change those code again and again with those new simple requirements?

If we have three types like "320x50", "300x250", "320x250", how could you distinguish them with those relative measure words?

I tried to think why there are "Small" and "Large" on our website, maybe someone just thinks it is better on User Experience, but it is unresponsible words for indicating Ad types. And it will make us got trouble in the future. Why don't we prevent it? Xibo told me there could be a mistake in a previous design that there were only words "Small" and "Large" in the form options. But in the current design, everywhere the "Small" and "Large" exist must be followed by a particular size like "(320x 50)". That is a right design.

As for different languages, for different region use different languages on the auto-generated title? Why we need to do that??? Why we have to make the thing difficult and ugly for this simple requirement. This is a PATCH rather than a wise solution.

This logic shouldn't depend on a specific UI context. The logic is independent although there is a size type below the title in an Ad Item. It is a principle how we maintain our product with new requirment–do not couple different logic and make them as independent as possible. Otherwise, one modification will bring lots of new issues.
