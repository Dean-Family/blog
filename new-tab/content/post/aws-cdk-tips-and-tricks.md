---
title: "Aws Cdk Tips and Tricks"
date: 2022-09-02T22:45:10-07:00
tags: ["aws", "cdk"]
draft: true
---

After coming to use the Cloud Development Kit (CDK) for Amazon Web Services (AWS) for a variety of use cases I came to believe that the CDK is both incredibly powerful and a bit tricky. Most of the trickyness comes from a few reasons which should be detailed in another post. This document will focus instead on the best ways of dealing with these nuances of the CDK. It will grow over time as I find more things to add.

## [Pipelines](https://docs.aws.amazon.com/cdk/api/v2/docs/aws-cdk-lib.pipelines-readme.html)

Pipelines are my favorite feature when it comes to the CDK but it is not without it's complexity costs.

1. If you pipeline is broken during it's synth phase it will not fix itself. The pipeline doesn't get any new configurations because it can't get to the update pipeline step. So, no matter how much  you commit, nothing changes. You can fix it by deleting anything in external accounts by hand,  optionally deleting the stack and resources from the pipeline account and then rerunning the cdk  deploy command (usually  `npx cdk deploy`).

1. Local bundling is great, and makes working in all Typescript projects great!

1. Speaking of local bundling, beware of jsii code generation putting Typescript in your other languages. I have experienced this most when working with local bundling and all the docs tell you to use Typescrypt functions for pathing.

1. Use trunk based development. It will get complicated and break otherwise.

1. When using Cloudformation exports in a multi account deployment, it will *not* go from your pipeline to your deployment because Cloudformation exports do not go between accounts. I suspect that the reason I did this was because I was doing something wrong in the code, but I still am not sure.

