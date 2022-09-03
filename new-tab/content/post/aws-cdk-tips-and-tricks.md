---
title: "Aws Cdk Tips and Tricks"
date: 2022-09-02T22:45:10-07:00
draft: true
---

# AWS CDK Tips and Tricks

After coming to use the Cloud Development Kit (CDK) for Amazon Web Services (AWS) for a variety of
use cases I came to believe that the CDK is both incredibly powerful and a bit tricky. Most of the
trickyness comes from a few reasons which should be detailed in another post. This document will
focus instead on the best ways of dealing with these nuances of the CDK.

## [Pipelines](https://docs.aws.amazon.com/cdk/api/v2/docs/aws-cdk-lib.pipelines-readme.html)

Pipelines are my favorite feature when it comes to the CDK but it is not without it's complexity
costs.

1. If you pipeline is broken during it's synth phase it will not fix itself. You can fix it by
deleting anything in external accounts by hand, optionally deleting the stack and resources from the
pipeline account and then rerunning the cdk deploy command (usually  `npx cdk deploy`).
