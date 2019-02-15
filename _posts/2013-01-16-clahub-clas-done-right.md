---
layout: post
title: "CLAHub - CLA's Done Right"
date: 2013-01-16 08:06
comments: true
categories: [Open Source, CLA, CLAHub]
---
<div class="error">IANAL: The post below is based on my experiences in dealing with Open Source projects from a contributor standpoint and as a benevolent dictator.</div>

### Background

First of all, what exactly is a Contributor License Agreement (hereafter referred to as __CLA__)?

Most of us that have been employed as Software Engineers by corporations are already intimately familiar with __CLAs__ although in the corporate world they are generally called a _"Intellectual Property Assignment Agreement"_. In many ways a __CLA__ is nothing more than that but specifically geared towards Open Source projects.

A __CLA__ is a legal document in which you state you are entitled to contribute the code/documentation/translation to the __project__ you're contributing to and are willing to have it used in distributions and derivative works. This means that should there be any kind of legal issue in the future as to the origins and ownership of any particular piece of code, then that __project__ has the necessary forms on file from the contributor(s) saying they were permitted to make this contribution.
<!-- more -->
The __CLA__ also ensures that once you have provided a contribution, you cannot try to withdraw permission for its use at a later date. People and companies can therefore use that software, confident that they will not be asked to stop using pieces of the code at a later date.

### What Needs To Be In A CLA

The __CLA__ needs to grant rights to a project’s owner (or owning body/organization) that enable the release of the software in question. In the simplest scenario, a __CLA__ is not, in fact, used at all; the contributor simply assigns the copyright to the project owner. When done properly, the contributor will need to sign a statement to that effect.

Thus the contributor needs to - at minimum - grant the rights that will be granted to the project’s owner in the distribution licence. When granting rights it is common to grant a very broad range of rights. This is in order to avoid the need to return to the contributor for authorization to take a desired action with their contribution, such as releasing under a different licence.

A __CLA__ should also contain personal information about the person that signs it, such as a complete name and mailing address. You should be aware of the potential implications that storing this information could have in terms of the data protection law in your country and ensure that you have a Privacy Policy in place to deal with this.

### Recording CLAs
It is very, very important to record the assignment of copyright or grant of rights for each contribution or from each contributor. This means an Open Source project __must__ track and record __CLAs__ submitted by contributors. It is generally best to have a __CLA__ signed and submitted to project administrators for permanent record prior to the contributor submitting his/her contributions. 

### Maintaining CLAs

Maintaining __CLAs__ can be challenging but overall it is not a difficult task. It does increase the effort required to make and accept third-party contributions. Most contributors will start small; i.e., they will provide a simple bug-fix, or a spelling correction. The temptation is there to bypass the requirement of a __CLA__ for small contributions. 

This begs the the question, _"Must a __CLA__ be in place for every contribution?"_

For small contributions, the risk of loss from legal action can be small. For larger chunks of code/documentation, incorporating major functionality, the risks would be much, much higher.

At the end of the day, it's really up to the project owners and stakeholders on which contributions they chose to accept with and without a __CLA__.

### So who uses a CLA

So what notable Open Source projects are using a __CLA__? Here are just a few. 

* [Canonical](http://www.canonical.com/contributors)
* [Fedora](https://fedoraproject.org/wiki/Legal:Licenses/CLA)
* [Android](http://source.android.com/source/cla-individual.html)
* [Mono](http://mono-project.com/FAQ:_Licensing)
* [Apache](http://www.apache.org/licenses/icla.txt)
* [NodeJS](http://nodejs.org/cla.html)

### Methods of Recording a CLA

There are many ways to record and maintain a __CLA__. Some projects require that you print out, complete and sign a document then mail that document back to them. Some projects allow for scanning in a signed agreement then emailing in PDF form to a specific email address while other projects have embraced contributors signing electronically.

Smaller Open Source projects have used electronic signature providers such as:

* [Echosign](https://www.echosign.adobe.com/en/home.html)
* [DocuSign](http://www.docusign.com/)

While larger projects have rolled their own online solution.

* [Canonical](https://forms.canonical.com/contributor/)
* [NodeJS](http://nodejs.org/cla.html)

You can also use [Harmony Agreements](http://www.harmonyagreements.org/) to assist you in selecting the right __CLA__ for your Open Source project.

### My experience with CLAs

For a year, I was the Director of Developer Relations at [Appcelerator](http://www.appcelerator.com) and part of my job was to be the default company representative and signer for the __CLA__ we had in place. We happened to use [Echosign](https://www.echosign.adobe.com/en/home.html) as our electronic signing tool of choice. As I haven't used Echosign (plus they've been purchased by Adobe since then) in over a year I won't go into details as to whether or not it's any good.

#### Appcelerator CLA Workflow

At Appcelerator a vast majority of our work was Open Source and was hosted in public repositories over on [GitHub](https://github.com/appcelerator). The workflow pretty much operated like this:

1. Fork the project.
2. Make one or more well commented and clean commits to the forked repository. 
3. Perform a pull request in github's web interface.
4. Project stakeholder would review the pull request and choose to accept/reject.
5. If project stakeholder chose to accept, stakeholder would email me to verify if we had a signed __CLA__ on file for the contributor.
6. I'd logon to Echosign and verify if there was a __CLA__ on file for said contributor.
7. I'd email the project stakeholder and let him/her know if there was or wasn't a __CLA__ on file.
8. Project stakeholder would accept the pull request if we had a __CLA__ on file or if we didn't they'd reach out to the contributor and get them to sign the __CLA__. 
9. Once the contributor signed the __CLA__ we had to go through steps 6-8 all over again.

As you can imagine, this was rather inefficient and created quite a bit of friction at times. Which brings me to [CLAHub](https://github.com/jasonm/clahub)

### CLAHub

I found about [CLAHub](https://github.com/jasonm/clahub) while perusing the [Octopress Sites Wiki](https://github.com/imathis/octopress/wiki/Octopress-Sites) and checking out other people's [Octopress](http://octopress.org) installs and themes. One of the sites I visited was the website of [Jason Morrison](http://jayunit.net/) who is the author of CLAHub.

I read through his [blog post](http://jayunit.net/2013/01/09/clahub-easy-contributor-agreements-on-github/) and fell in love with the idea and the concept.

__This is how Jason describes it:__

> With CLAHub and an open source project on GitHub you can:

> * Sign in with GitHub and create a CLA for your project.
> * Ask contributors to sign in with GitHub to electronically sign the CLA.
> * See on each pull request whether the contributors have all signed your CLA. This uses the handy Commit Status API, similar to what CI tools do.

As a bonus Jason has released it as Open Source under the permissive [MIT license](https://raw.github.com/jasonm/clahub/master/LICENSE).

To find out more about the project then please visit these links:

* [CLAHub Site](http://www.clahub.com/)
* [GitHub Code](https://github.com/jasonm/clahub)
* [GitHub Issues](https://github.com/jasonm/clahub/issues)
* [Jason's Original Blog Post](http://jayunit.net/2013/01/09/clahub-easy-contributor-agreements-on-github/)

One thing to note is that CLAHub currently only works for __public__ repositories and __NOT private__ repositories.

### Conclusion

If CLAHub had been available during my time at Appcelerator we definitely would have used it as it removes almost __ALL__ of the friction points listed above. 

If you're a developer with an Open Source project hosted on GitHub or an organization that's doing the same then you should really take the time to evaluate CLAHub as it just integrates nicely with the existing tools and methods that you are more than likely already using.












