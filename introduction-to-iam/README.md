# Introduction to IAM

Identity Access Management is a branch of cybersecurity that aims to regulate access to other services (web applications, mobile applications, ERPs, ...) and protect them. Its main purpose is to grant specific access and permissions to certain people while maintaining the integrity, confidentiality and availability of the service.

IAM originated from the simple login form on early websites. From there the need for efficient task execution inside of applications led to the development of federated services. This led to the introduction of OAuth 2.0, a protocol that allows services to request specific user data (for example only contacts, generalities,..)  from another platform. This eliminated manual data entry and enabled seamless integration and personalized experiences. Users can authorize access with a single click, enhancing the digital ecosystem.

Then, as a further evolution.Entering the correct user and password associated, the website could give access based on your profile. That was the core principle. But this model soon showed his limitations. Imagine being a developer struggling to share code samples with hundreds of friends on a third-party coding platform one by one. Manually entering all contacts seemed tedious. That's where third-party integrations came in with the [OpenID Connect](iam-protocols/openid-connect/) standard. Very quickly websites evolved to do so. There weren't just static pages anymore; websites are now interacting with services like Facebook, Google, and Twitter.&#x20;



But the story doesn't end there. As users demanded even greater convenience and security, another innovation emerged: [Social login](iam-protocols/social-login.md). This technology allowed users to directly employ their social media profiles (e.g., Facebook, Twitter) to authenticate themselves on non-social media platforms. Gone were the days of struggling with multiple usernames and passwords; a single social media login sufficed as an identity provider for all your external services.
