---
layout: post
title: "Maven dependency version properties"
description: ""
category: programming
tags: [maven]
---
{% include JB/setup %}

Writing maven pom files can be tedious.
I rarely want to spend another minute more than I need to doing it.
Thus it makes sense to figure out how to do it as efficiently as possible.

Efficiency is not only related to automation and reuse.
What workflows the individual developer prefers also goes into consideration.

This post is specifically about doing updates to the projects dependency versions.

Making upgrades brings new features and bug fixes to the project.
They can enhance security or performance or allow the developer to remove code that is no longer needed.
It can also require migration due to deprecations and changes to the transitive dependencies.
Migration can entail code changes, dependency management and quite excessive troubleshooting.

To successfully upgrade a dependency.
The developer must find out that there are one or more new versions available.
Do the upgrade.
Verify that no unintended behavior changes appear and that the application builds.

For finding out there are new versions available I have found some different tools.
One is invoking `versions-maven-plugin:display-dependency-updates`.
Another is doing a search in the browser on the depency GAV on Maven Central or Maven Repository.
A third is to use an editor capable of doing queries for repositories defined in the maven settings.

Changing the values in the pom can be done manually or with a tool.
Manual editing is required when migration is needed.
Using VSCode I can to both operations in one.

The majority of updates (given that they are done frequently as they are in any security aware installment) are patch updates and are preferably automated.
Automation can be done as described in this post <https://www.baeldung.com/maven-dependency-latest-version>.
With subsequent test builds and checkins.

Using a capable IDE and plugins to find and update versions are important to avoid wasting time.

I often see the practice where the `<properties>` section is used.
This can be `<version.my-beloved-3pp>1.2.2</version.my-beloved-3pp>` and then refered in the dependency `<version>${version.my-beloved-3pp}</version>`.
This can seem efficient when there is no BOM and you would like to avoid editing the same version in two or three places.
However, this makes it impossible to use the IDE to find and edit versions in one operation.
It also prevents use of `versions:use-latest-versions` with configuration to update in several places at once.
It also requires the pom maintainer to put information about a GAV in more than one place in the pom.
How the keys are named differ from author to author which makes mistakes more frequent.

Hence I prefer to not use properties.

{% include share.html %}
