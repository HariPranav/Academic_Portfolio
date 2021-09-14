---
title: Documentation For Projects
date: 2021-09-14T11:56:38.320Z
summary: Documentation is one of the key aspects to a project. It highlights the
  functionality and usage of the entire solution along with the drawbacks. Hence
  this blog serves as a guide to building and maintaining an effective, easy to
  use documentation tool.
draft: false
featured: false
categories:
  - Development
  - Tech
image:
  filename: featured.jpg
  focal_point: Smart
  preview_only: false
---
# Documentation For Projects

## What is the importance of Documentation ??

Documentation describes the version   ,configuration , compatibility and the various dependencies ,prerequisites  that a project requires to work .

Documentation helps other developers understand the various limitations and use cases of a project and how to use the various parts of the project to their advantage .

Hence in a nutshell Documentation provides a detailed guide to using a project and all companies big or small have documentation !!


## What is markdown ??

Have you used HTML ?? It sometimes gets so messy with all those tags when we just to need to have a **static** page with minimal functionality

Introducing Markdown !

The main functionality of markdown can be found below

https://markdown-guide.readthedocs.io/en/latest/basics.html

Lets see some basics to bootstrap a blog page

# Headings

![Headings](https://raw.githubusercontent.com/janosgyerik/writing-markdown-well/master/screenshots/headings-on-stackoverflow.png)

We use a single **hash** before text for the largest font  similar to **h1** in html

Similarly if we want a **h2** we use two hashes before the text we want !

# Images from the web or local machine

Use an exclamation mark followed by square brackets with the text and round braces for the url

![Images](https://raw.githubusercontent.com/HariPranav/BENIMAGES/master/images.png)

eg  : ![BEN Image](https://blockchainedu.org/static/media/ben-full-logo.3f23ec07.png)

# Hyperlinks

![Hyperlinks](https://raw.githubusercontent.com/HariPranav/BENIMAGES/master/links%20.png)
Square brackets with the text and round braces for the url



eg: [BEN_Website](https://blockchainedu.org/)

# MkDocs

MkDocs is a fast, simple and downright gorgeous static site generator that's geared towards building project documentation. Documentation source files are written in Markdown, and configured with a single YAML configuration file. Start by reading the introduction below, then check the User Guide for more info.

# Running MkDocs in Local Machine

In order to manually install MkDocs you'll need Python installed on your system, as well as the Python package manager, pip. You can check if you have these already installed from the command line:

    $ python --version
    
    $ pip --version
    

If you don't have python already installed download it from here

[pythonDownload](https://www.python.org/downloads/)

run

    $pip --version if it is not installed you can find it in the link below

[pipDownload](https://packaging.python.org/tutorials/installing-packages/)

Install mkdocs using pip

    $ pip install mkdocs

Run

 $ mkdocs --version

to check that everything worked okay.

If this does not work then python is not added to your path a neat hack around this is to run

    $ py -m mkdocs --version

# Creating a new project

    $ mkdocs new my-project
    $ cd my-project

    

Open a new terminal and open the "my-project" folder there you will find a file called index.md

Edit the file using a text editor then  run

    $ mkdocs serve

or
    $ py -m mkdocs serve

Your static site is now up and running
Open up your browser and go to

 http://127.0.0.1:8000, to view the webpage

Now let's add some content to it and host it on GitHub !!

# Pushing the site to git

Install git if you haven't from the link below

[git](https://git-scm.com/downloads)

Go to github and create a new repository with the same name as the project folder in this case **my-project**. This step is crucial as we need to deploy the site to the correct repository.

Sign in and create a new repository

 Add the name

And a short description

Leave the initialize a Readme as unticked and say create repository

Now open the command Line and

    $ git init .

    $ git commit -m "First Commit"

    $ git remote add origin PASTE YOUR URL 

Finally run

    $ py -m mkdocs gh-deploy

Now your site is deployed to git Hurray !!


# Publishing on Medium

Medium is a good platform to publish blogs and articles on various subjects , go to

[Medium_Website](https://medium.com/)

Sign in with your Gmail or create a new account and click on create a new story

The disadvantage with Medium is that , it does not have direct support for markdown files so we can use a third party website , go to

[MarkdownToMedium](https://markdowntomedium.com/create)

and follow the steps ,
- paste your markdown and convert into a GitHub gist and connect to Medium
- paste the link in  Medium
- import the link and your site is now published to Medium!!

Before publishing to Medium make sure that all the content from the markdown file has come in the correct order, as sometimes there are bugs at the time of importing gists from git.

# Decentralised Hosting on IPFS

## What is IPFS ??

A peer-to-peer hypermedia protocol
designed to make the web faster, safer, and more open.

 [IPFS](https://ipfs.io/)

## What is fleek ??


On IPFS , Fleek provides a beautiful way to integrate with Git so that whenever we make changes to our branches it can be directly
updated on Fleek!!!!

### Hosting on Fleek

Click on the link below to know more here we can directly login with our git account and host our  website.
Click on sign in and sign in with github , now add the repository containing your github page and your done!!.

[Fleek](https://fleek.co/)



Different CMS to host sites on fleek Link Below

[Fleek Blog posts](https://blog.fleek.co/)


We can make changes from time to time to update the webpage on git by pushing the pages to git , Fleek will automatically implement these changes from the gh-pages branch from git !!

The best part is that we can make multiple pages with a single GitHub ID!!

Awesome we now have our very own **documentation** website hosted on a **centralized** as well as a **Decentralized Service!!**
