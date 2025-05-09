1. Shift-left Security: consider security engineering from the beginning when designing a product or system.
2. Administrative Segmentation: avoid giving admins complete root access because they might become an internal threat group. One thing we can do is implement Shamir's Secret Sharing principle. Split the role of one admin to three different users. Now it takes 3 people to cooperate instead of one person with root access.
3. Threat modeling and threat intelligence
4. Table-Top tactics: get stakeholders together and discuss how to respond to different threats.
5. Continuous Patching and supply chain: When patching new updates, test on the lowest development environment to make sure that everything works fine with the new update. Continuous supply chain is validating all dependencies to make sure that they behave as expected and that they haven't been tampered with.
6. Encryption
7. Logging and chaos testing: Logging is essential to security. Chaos Testing is when we purposefully break parts of the system to see how it will react. It is making it fault tolerant.