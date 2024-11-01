---
title : "Introduction"
date :  "`r Sys.Date()`" 
weight : 1 
chapter : false
pre : " <b> 1. </b> "
---
**CI (Continuous Integration):** CI is a method to automate the build and test sections. CI wait for any changes in repository and then trigger build and test. It means integrate new code changes continuously. CI ensure that new codes are repeatable built and tested without any extra effort after commit new codes. By merging changes frequently and trigger automatic building and testing process, we can minimize the possibility of code conflict, even with multiple developers working in the same repo.

**CD (Continuous Delivery):** CD is a practice that work in conjunction with CI to provide an automatically way to deploy the artifact from CI to our staging or testing environment without any human intervention.

**CI/CD** combines steps from CI & CD to build a optimized development process.
With CI/CD configuration, we got these positive effects:
1. Allows developers to commit smaller changes more often, instead of waiting for a release.
2. Automated, continuous building ensures that codebase remain stable and any issue will be detected as soon as possible.
3. It's easier and faster when any issue happen. Developer will be notice that a build is failed. Logs, build flow are also provided for debugging step.

With above advantages, we should consider CI/CD for our application to save time and effort.

![ConnectPrivate](images/cicd_flow.png) 