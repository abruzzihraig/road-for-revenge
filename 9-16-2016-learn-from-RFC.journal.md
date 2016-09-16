### Learn From RFC
We front-end team tried to integrate with API service today. But we failed, because there are some mechanisms I was not familiar, especially the authentication and authorisation parts.

We used OAuth 2.0 framework as the authorisation mechanism. That means we front-end team just need keep an access token to fetch any data from our resource server. I never used the OAuth before, even though I’ve known that is popular in everywhere.

I thought it should be easy, so I tried to analyse code from previous projects. I knew if we use OAuth, we have to write code according to a right format, but I didn’t know what is the actual interaction between an App and an Auth Server.

Nothing broke my mind when I was thinking how the authorisation is handled between an App and a server. I even found a perfect logic to explain how it works, and I also told that for my team member. Another backend colleague agreed with me as well.

However, I paid one hour to read the RFC document of OAuth 2.0 in the evening. Then I found I was totally wrong. Every parts I reasoned is incorrect. I made so many jokes on it. That made me really shamed.

I should have read the RFC document before I taught others. It just needs one hour to read the basic usage and the whole authentication architecture. Then I will get a right way to understand something under the hood.

Hope next time I do not make the same mistake for others.
