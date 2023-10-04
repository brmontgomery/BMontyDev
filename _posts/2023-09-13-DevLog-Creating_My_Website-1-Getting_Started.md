---
layout: posts
title:  "DevLog 1 - Getting Started on my Portfolio!"
---

<br />
![DevLog Intro Picture](\assets\images\1_DevLog_Intro_Picture.jpg)
# Intro
For my first entry into the DevLogs I have chosen to create an article on the creation of the website that these will be hosted on. There’s not much more to be said, so let’s get cracking!

# Requirements
So, **What is it I need my website to do?**

Well, broadly speaking, I need it to act as both a window into my private coding life, and a resume to show to potential employers. 

Cool, sounds simple. **How does that translate into the content requirements of the website?**

To fit those needs I plan to create:
- Homepage – I need a page which draws people further into my site while providing them with an overview of what the site is and has to offer.
- Portfolio section – A page or couple of pages that showcase my projects and connects them to explore their repositories. Ideally I would be able to push visitors towards specific projects that I am particularly proud of.
- DevLog section – A section that acts as a repository for my devlogs. Possibly multiple pages that are sorted in different ways, and may be pinned. 
- About Me Page – I want employers to know who I am. I will include some basic information such as my general working area, notable employment history, and interests (mostly those that lie within the field of computer science).

For the DevLog and Portfolio sections, I plan to only get the bare minimum working. If I decide to add features to the sections, I imagine they would be good subjects for future articles with a deeper dive.
On top of that, I would also like to make sure that my website follows a few principles:
1. Each page has a clear purpose and sticks to that purpose.
2. Keep the aesthetics consistent (using a template should take care of this)
3. Keep it easy to navigate
4. No clutter
5. Make sure that information is organized as consistently as possible in a left to right, top to bottom order and with important info prioritized.
6. Keep load times down. (AKA don’t screw up the template)
7. Keep it mobile friendly (Learn from the mobile friendliness of the template to keep the website mobile friendly moving forward.)

# Getting Started
## Which platform to use?
The first thing I have to decide is what platform I wish to host my website on. Thankfully, this is not my first attempt to create my own website, so I am a little bit more aware of what the options are and their pros and cons than I was the first time. 

The main contenders I am looking at are Wordpress, Squarespace, Github pages, and Firebase.

![Web host logos.](\assets\images\1_Web_Host_Logos.jpg)

The first time I attempted to make a personal website (for a non-web-dev undergraduate class) I used Wordpress because it took little effort to make a minimal site for a class. While it had some perks with its simple startup and the ability to host your website for free, I found myself frustrated with the difficulty in customizing my website without forking over a significant sum of money. 

I want to host for free since money is tight while my wife is going through nursing school. So, as a paid service, Squarespace is out of the running.

That leaves Github pages and Firebase, which as far as I know are free to host on and are largely customizable without spending lots of money. There are many differences between Firebase and Github pages, but the main one to me is that Github pages forces you to create a static website and Firebase allows for dynamic pages. Firebase comes with some more bells and whistles like integration with the Google Cloud, database storage, and site previews.

At the end of my host search however, I wound up goingwith Github Pages as it fit my needs almost perfectly and would definitely work well with my preferred git workflow.

## Setting up the repository
In order to use Github, I must first set up a repository for the website. This requires that you already have and are logged into a Github account.

First hit new repository and give it a name.
Once the repo is created, go into the settings -> Code and Automation -> Pages.
Then under Build and Deployment -> under Source -> Select deploy from branch.
Use the dropdown menu to select a branch to deploy from.

From here you can optionally change title of the website in the _config.yml page that was created and select a domain for your site. I have elected to do both.

Make sure to check out your git repository within your computer and set up git tools on your favorite text editor(or the command line). It makes management of repositories and commits much easier.

## Choosing a template
To start with, I decided to jumpstart the process with a template from [HTML5 UP](https://html5up.net/ "HTML5 UP Homepage") and it was was the best decision I made that day.

I tried a few themes and eventually narrowed it down to the *Story* theme

![Story theme.](\assets\images\1_Story_Theme.jpg) 

and the *Editorial* theme.

![Editorial theme.](\assets\images\1_Editorial_Theme.jpg)

I wound up going with the *Editorial* theme as I felt it fit my needs more.

I put the theme in place on my checked out copy of the dev branch and committed it. Now it's time to customize it!

# Editing the Home Page
The first thing I did was edit the titles and welcome messages to match my site's name and welcome users to my site.

![Welcome Message.](\assets\images\1_Welcome_Message.jpg)

Further down the page I found the perfect place to draw interest to my projects and blog posts using the theme's tile feature.

![Tile Example.](\assets\images\1_Tile_Example.jpg)

I then cleaned up the left sidebar so it only featured active content and the social media links since I tend to stay off of that.

![Sidebar.](\assets\images\1_Sidebar.jpg)

I then chose to remove other pieces of personal information as I do not have a PO box or a (personal) professional email that I feel comfortable cluttering. 
Perhaps I should change that... Thoughts for another day I suppose. 

I did leave some things unedited at the end. I left the search bar in place, but unfinished, and left the footer untouched for the time being.

## It’s Alive!
Once the final changes were committed and everthing was ready, I clicked the link in the github settings to see my site and...

Voila! I give you a home page!

In the next DevLog, I will be destroying all of my progress that I made in this article to add the tools and features that are Markdown and Jekyll and discovering some pitfalls you can avoid.
