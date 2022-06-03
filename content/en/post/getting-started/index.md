---
title: CI/CD
subtitle: Principles, implementation, tools

# Summary for listings and search engines
summary: 

# Link this post with a project
projects: []

# Date published
date: '2022-05-06T00:00:00Z'

# Date updated
lastmod: '2022-05-06T00:00:00Z'

# Is this an unpublished draft?
draft: false

# Show this page in the Featured widget?
featured: false

# Featured image
# Place an image named `featured.jpg/png` in this page's folder and customize its options here.
image:
  caption: 
  focal_point: ''
  placement: 2
  preview_only: false

authors:
  - admin

tags:
  - Academic

categories:
  - Demo
---

## Principles

The concept of continuous integration and delivery (CI / CD) is the basis of our testing. For those who don't know: CI/CD is a concept that is implemented as a pipeline, making it easy to merge newly committed code into the main codebase. The concept allows you to run various types of tests at each stage (execution of the integration aspect) and complete it with the deployment of the committed code into the actual product that end users see (delivery execution).

CI/CD is essential for software development using the Agile methodology, which recommends the use of automated testing to quickly get working software up and running. Automated testing gives stakeholders access to newly created features and provides quick feedback.

I recently set up CI/CD pipelining for an as-of-yet-under-wraps project that targets local professionals who are having trouble finding work. Next, I'll share what I've done and share my thoughts on CI/CD.

Content

We will look at the principles of CI/CD.

The first principle of CI/CD: segregation of stakeholder responsibilities.
Second principle of CI/CD: risk reduction.
Third principle of CI/CD: short feedback loop.
Environment implementations in CI/CD.
Tools for CI/CD.
Let's get started.

First CI/CD Principle: Stakeholder Responsibility Segregation
One of the main benefits of CI/CD is the timely involvement of various stakeholders in any project.

Developers and designers (Devs) create the experience and logic of the product, presented in user stories, and are responsible for making the features work, proving it through unit tests.

Quality Engineers (QE) are responsible for maintaining product quality, reviewing features as they are completed (see the definition of Done), and introducing end-to-end (E2E) features/acceptance tests to ensure that the customer will receive a product that works without errors.

Business Analysts (BAs) and Product Owners (POs) are responsible for acceptability (e.g. business value) as evidenced by interacting with actual users and creating user stories. They coordinate and analyze the results of acceptance tests to validate user stories and possibly create new ones based on feedback.

Operations (Ops)/DevOps engineers are responsible for making the product available to users. Working in the CI/CD space, they scale concepts as needed and develop code logistics so that code from developers can move into production and users can access it.

Users are responsible for the use of the product. It is understood that the product must be useful and justify the effort.

Each stage of the CI/CD pipeline creates an environment set up for teams to take ownership of the respective test stage, ensuring process integrity.

Second CI/CD Principle: Risk Reduction

Each stage of the CI/CD pipeline is designed to mitigate risk in some way. Developers are responsible for logical and written tests to reduce the risk of breaking the logic. QEs are responsible for the integrity of the user stream and write tests to mitigate the risk of broken user streams/stories. BAs and POs are responsible for usability and take part in user acceptance tests to reduce the risk of creating unusable/unwanted features. Ops/DevOps are involved in CI/CD maintenance related to deployment operations (data schema analysis/data migration) and scaling to reduce the risk of product unavailability.

Because stages are designed to mitigate a specific risk, it is important to note that when configuring pipeline processing, each stage should also serve as a quality control gateway that prevents corrupted/unwanted features from passing through.

Third principle of CI/CD: short feedback loop

The reason for introducing CI/CD pipelines is the use of machines to work with people. This allows you to reduce the time spent on feedback on the developed functions.

But why is it better to use machines? Because humans don't scale like machines. Scaling reduces the time spent on software testing, allowing you to automate the deployment process. These procedures will take much longer if performed by a human.

However, in error-prone situations requiring human input, automation may not be desirable/impossible. For example, we can never automate a tester when it comes to usability. Another important example is the migration of production data. Automate code logistics (how code is packaged/moved between stages) as much as possible, but be aware that automation is ultimately meant to reduce the time it takes to get the code committed. If there are bugs that take longer to fix than to prevent, avoid automation and try to achieve a short feedback loop.

Environment Implementations in CI/CD

We'll look at the various CI/CD implementation environments and what happens at each stage, referring to the implementation in the projects I'm working on. Each environment is represented as a branch of the code control system repository.

Development

Our development team is small, so we use trunk-based development, where all commits fall into a single branch. This branch serves as a development environment and runs unit/system tests on all committed code. The current version of the development branch goes through quality control (qa branch) and the application is deployed so that all developers can review, test, and validate the code, enabling collaborative development.

Quality control

The product goes through the build process and unit/system tests are run again in an environment with application-level production configurations. Code is deployed to the QA version of our platform, and feature tests are run twice a day. When passing regression tests, the code in the qa branch is promoted to the uat branch.

Eligibility Check

We allow access to POs to assess whether features have been created as they were envisioned and communicated through user stories. When accepted through testing with a selected group of users, stories marked as accepted will be released to production at the next deployment.

Integration systems testing

In this step, we deploy the application to an environment that mimics a production environment and runs tests to verify that the software is working. We also run non-functional tests such as load testing and security testing to confirm that the application will be secure. When all the tests pass, we will finally reach...

Production

Users get the opportunity to rate released features.

Tools for CI/CD
Local

GitLab CI, TeamCity, Bamboo, GoCD Jenkins, Circle CI.

Cloud

BitBucket Pipelines, Heroku CI, Travis, Codeship, Buddy CI, AWS CodeBuild.

Government

hats, Nectar.

Our team uses GitLab as a code repository and CI leader due to local hosting requirements. In other projects, we use alternatives that offer local options - Bamboo from Atlassian, TeamCity from JetBrains, and GoCD from ThoughtWorks. We have not yet used Jenkins and CircleCI in our projects. (Leave a comment if you've ever used them and are satisfied with it.)

If you don't have a need for local hosting, there are plenty of other cloud based CI tools like Codeship, Buddy CI and Travis. For personal projects, a growing number of code repositories provide an all-in-one solution that gives access to CI tools. BitBucket recently launched its own free CI

