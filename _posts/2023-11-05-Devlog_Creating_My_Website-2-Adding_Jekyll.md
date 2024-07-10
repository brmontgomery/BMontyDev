---
layout: posts
title:  "DevLog 1 - Getting Started on my Portfolio!"
---

<br />
![Jekyll Site Picture]({{ site.url }}\assets\images\2_Jekyll-Site.JPG){:.image.centered}

# Adding Jekyll
Welcome back to Part 2 of the "Creating My Website" series! In this installment, I figure out how to add Jekyll, a static site generator, so I can use it to generate my site more efficiently. The question is, will I find it to be worth the investment?

## What is Jekyll?
Let's start with a little background on what Jekyll is. 
Jekyll is a site generator for static sites (I'll go into that in a moment). It takes an inputof a series of Markdown down files structured within a file system in a particular way, HTML code and CSS files to compile, render, and output a full static site. 
Jekyll also utilizes a templating language called liquid to allow the site creator to write static code dynamically. This is achieved using neat global variable tricks, layouts, and allowing the site programmer to modularize their code and simplyuse includes where needed (A great example of Don't Repeat Yourself). 

### Difference Between Static And Dynamic Sites
Static and Dynamic websites differ in the ways in which they deliver content to the end user of the website. 

A static website has the same content for every user every time. Unless the source is updated, what each user sees will be identical. These types of websites are mainly meant for displaying information and are not good for intereacting with databases, handling user inputs that may affect the way the website behaves, or any application that has individualized content (Think a login page). 
That is not to say all of those things are impossible on a static website, just that it is often much more troublesome and requires creating a sort of hybrid page, often using third party applications.  

As such if we are planning to do those things, we should consider creating a dynamic website. Why? Well, let's take the example of a webstore. Some of the basic features that you would need in a webstore are an inventory and way to display it, a way to differentiate users, a way to add items to a cart and a checkout page, and a way to interact with a back end to process an order. 
Two properties that many of the features in this example share are individualized views of each webpage and interaction with resources on the backend of the website. These are the main features that set dynamic websites apart from their static counterparts and are possible without the use of additional tools being used within the site code. Without these features, many of your favorite websites would be designed with very different design principles. 

### What is Markdown
![Markdown Logo]({{ site.url }}\assets\images\2_Markdown-mark.jpg){:.image.centered}

In short, Markdown is a syntax meant to make writing for the web easier.

It is technically known as a lightweight markUP language, but the end result is the same. 
Markdown is often used for writing blogs due to the ease of formatting, but you will also find it used in popular applications like Microsoft Outlook and Teams, or even Reddit. Next time you want to make something *italicized* in an email, surround the text in asterisks ('\*') or underscores ('\_'). You may find it to be a little easier to keep your hands on the keyboard rather than reach for your mouse to hit the tiny button when you are formatting.
And lastly, Markdown in it base form is rather simple to use. A cheatsheet for the entire language takes up a single sticky note and can be memorized by day's end for the average computer user.
It certainly doesn't hurt to be aware of the existence of Markdown and learn it regardless of whether you plan to build a blog or not as it is well-supported in the computer world.

## The Jekyll Website File Structure - A.K.A. How It Works
![The Jekyll File Structure]({{ site.url }}\assets\images\2_File-Structure.JPG "The Jekyll File Structure"){:.image.right}

### The Root Folder
Inside the root folder are some important Jekyll files
- Config.yaml
This stores configuration data for your website. 
- .jekyll-metadata
If you are using incremental regeneration this file will keep track of which files have not been modified. 
- .jekyll-cache folder
In a similar vein, this folder keeps copies of generated pages so that it can serve the site faster in subsequent generations. 

*As the Wiki states, you may want to place both the .jekyll-metadata file and the .jekyll-cache folder in your .gitignore file.*
   
The root folder also contains your index.html/md file. This is the home page. See Part 1 for an in depth discussion on this page.
   
There are numerous other folders that provide functions for the Jekyll site.

The _data folder is where you can place formatted files that contain data for your site. You can consider this like a primitive form of a site database. It only holds predetermined data and cannot be edited from the served website. Data can be accessed via {% raw %}`site.members`{% endraw %} or {% raw %}`site.data.members`{% endraw %}.

The _drafts folder holds files that are not published when you serve your site unless you add the tag {% raw %}`--drafts`{% endraw %}. It's rather self-explanatory in my opinion.

My favorite folder (*don't tell the others*) isthe _includes folder. This is where you can keep resuable pieces of a website that can be added through the jekyll generation process. These files should be code units that should stay consistent across the site and would otherwise by copy-pasted across numerous pages. For this site, it reduces each file by nearly a hundred lines with just an {% raw %}`{% include file.txt %}`{% endraw %} where "file" is replaced by the name of the file in the includes folder.

The _layouts folder is another exciting one for my purposes. Layouts are templates that further abstract the code for a file so that a page only needs to have its category specified to be formatted the same as others of the same type. The liquid tag {% raw %}`{{ content }}`{% endraw %} is used to show where the unique content of a page will be placed in the generated version of a page.

The _posts folder is where you place completed posts with the format {% raw %}`YEAR-MONTH-DAY-title.MARKUP`{% endraw %}. These will be served into the _site folder upon generation and are considered the "live posts".

The _sass folder is where you define styles for your site. Beware that Jekyll is installed with a horrible theme called "Minima". Override that ASAP.

And finally, the _site folder is where your generated site files are served at the end of the generation process. This is the folder that gets uploaded to the github pages' source repo.

Be aware that I came into this knowing almost nothing about Jekyll. Not knowing the Jekyll layout information made the implementation much harder (until I found it on the Wiki) and it definitely shows in my repo edit history. 

*My advice: If you plan to implement a site with Jekyll, get familiar with Jekyll's layout. What takes 5 minutes now will save you much time in troubleshooting later.*

## Why Did I Want to Use Jekyll?
![Typing Takes a Lot of Time]({{ site.url }}\assets\images\2_brad-neathery-nPy0X4xew60-unsplash.jpg "Photo by <a href="https://unsplash.com/@bradneathery?utm_content=creditCopyText&utm_medium=referral&utm_source=unsplash">Brad Neathery</a> on <a href="https://unsplash.com/photos/person-wearing-brown-and-white-watch-nPy0X4xew60?utm_content=creditCopyText&utm_medium=referral&utm_source=unsplash">Unsplash</a>
  "){:.image.centered}

After spending far too much time troubleshooting the damn fiddly bits if the software, I have lost sight of the answer to this question. But from my newfound perspective, one reason to use Jekyll still remains abundantly clear. **Code reuse.**

Starting with the template, I found that I was copy and pasting a lot of code without making any tweaks whatsoever after the initial personalization. Brute forcing the situation wasn't a bad idea at the small scale of my website, but do this at a larger scale, and it will quickly becomea maintenance nightmare. 
One change to the website header and you suddenly would have to change the same line on dozens of pages, troubleshoot any pages where you may have created a typo and spend an hour rubbing your temples in frustration at previous you's stupidity. Yeah, not my idea of efficient programming. Let's see how I can reuse code instead...

# The Process of Conversion
The following is a recounting of my frustrating process of figuring out all of the ins and outs of Jekyll that the documentation did a poor job of explaining in detail.
Don't get me wrong, the documentation is useful as a catalog of features and will help up to a point with troubleshooting, but good luck if you find an issue that the documentation has no mention of (most of them). Stack Overflow, Reddit, or vlogs like this are your best chance at finding a resolution. 

## Installing Jekyll
After ragging on the Jekyll documentation, I would like to say that this is one section where it is mostly competent. As someone who has not used Ruby before however, I chose to find a blog to help me get through the install. (This was a good one: [Coffee Talk - Jekyll Install Tutorial](https://www.theserverside.com/blog/Coffee-Talk-Java-News-Stories-and-Opinions/jekyll-install-windows-example-blog-tutorial "Coffee Talk - Jekyll Install Tutorial"))

For anyone that doesn't wish to leave the page, here are the steps:
1. Install Ruby and devkit from [Ruby Installer Downloads Page](https://rubyinstaller.org/downloads/ "Ruby Installer Downloads Page") (Choose the most recent version for your architecture that includes the devkit.)
![Ruby Installer Download]({{ site.url }}\assets\images\2_Ruby_Installer_Download.jpg){:.image.centered}
2. Keep all options selected during the install. 
![Ruby Installer Options]({{ site.url }}\assets\images\2_Ruby-Install-Options.jpg){:.image.centered}
3. When you get to the option for running **ridk install** make sure that it is checked.
4. In the prompt that opens up, choose option 3 to install MSYS2 and MINGW development toolchain.
![Ruby Installer Options]({{ site.url }}\assets\images\2_Toolset-Install.jpg){:.image.centered}
5. Run the command line as administrator, navigate to the folder in which you plan to put your website, and install Ruby using the command:
	{% highlight html %}{% raw %}gem install jekyll bundler{% endraw %}{% endhighlight %}
6. To verify the install run:
	{% highlight html %}{% raw %}jekyll -v{% endraw %}{% endhighlight %}
7. If anything is missing run:
	{% highlight html %}{% raw %}bundle install{% endraw %}{% endhighlight %}
8. To create a new blog run the following after replacing the bracketed text with your own blog name:
	{% highlight html %}{% raw %}jekyll new [YOUR_BLOG_NAME_HERE]{% endraw %}{% endhighlight %}
9. CD into your new blog folder 
Here is where I did something slightly different from the blog(because I'm trying not to waste my time opening up command prompts when I could be coding).
10. Create a scripts folder to house your dev environment setup script.
11. Create a batch file with the following
	{% highlight html %}{% raw %}cd [YOUR_SITE'S_ROOT_FOLDER]
	bundle exec jekyll serve{% endraw %}{% endhighlight %}
Afterwards you should see the below:
![Ruby Installer Download]({{ site.url }}\assets\images\2_Serve-Success.jpg){:.image.centered}
This code initiates the development environment so that you can see changes in your new site's code by typing in the following URL in your favorite web browser:
	http://127.0.0.1:4000/
12.  In the root folder, feel free to change the _config.yml and gemfile to better suit your needs. 
If you do this, you will likely need to install new ruby gems using:
	{% highlight html %}{% raw %}bundle install{% endraw %}{% endhighlight %}

Please consult other sources and keep a backup of your ruby files in your git repo if you do not know what you are doing. These files are easy to screw up and difficult to replace without backups. See the Troubleshooting the Jekyll Install section for information on someof the issues I ran into on initial install. I may potentially have a solution for an issue you may have.

*Remember that the locally hosted version of the site (http://127.0.0.1:4000/) is not what is live and shown to the public. You will need to host the site (specifically the files in the site folder) somewhere for it to be seen on the internet. See the previous article for more info on hosts.*

## Troubleshooting the Jekyll Install
Feel free to skip this section if you did not have any problems with the serving of the website. The issues that I ran into are likely fixed in newer versions of Jekyll and as such are specific to the version of Jekyll I am running.

### Jekyll is Not serving because a Ruby Library is Throwing Errors
I ran into this error when I would run step 11 of the install process. 
As it turns out, my use of Github Pages got me into some hot water regarding my Jekyll and Ruby versions. 
I had originally installed Ruby Version 3.3.0, the newest one. When I ran bundle install to update Jekyll and all of the libraries I need for it, it installed Jekyll 3.9.3. NOT the latest version of Jekyll. Circling back to github pages, the reason bundle install pulled that older version of Jekyll is because the version of Jekyll that the latest Github pages gem requires is 3.9.3.

Ruby version 3.3.0 and Jekyll 3.9.3 do not play nicely however and threw this error:
{% highlight html %}{% raw %} C:/Ruby33-x64/lib/ruby/3.3.0/logger.rb:384:in `level': undefined method `[]' for nil(NoMethodError) {% endraw %}{% endhighlight %}
Normally, one would be able to go to the latest version of Jekyll and this would be fixed. However, as I was using Github pages, I was forced to downgrade to Ruby version 3.2.0. 

### Jekyll is not serving because webrick cannot be loaded.
Jekyll version 3.9.3 also has an interesting issue where the authors did not include a required gem in their gemspec. 
To fix this all you need to do is run 
{% raw %} `bundle add webrick` {% endraw %}
to install the missing dependency.

## Converting The Homepage
Now that I have downloaded and installed Jekyll, it was time to take my homepage and convert it to Markdown. From what we've learned so far it should be simple, right?

I hopped into the code for the homepage and began an editing spree.

The first thing I did was pull out bits of code I wanted to reuse and stick them into files directly in the root folder. 

If you read the above Jekyll layout section, you would know that this is not the best way to order your includes.
It also meant that when I attempted to add the files through the use of 
	{% raw %}`{% include header.html %}`{% endraw %}
It did absolutely nothing!

There is however a way to make this work, however. If you use
	{% raw %}`{% include_relative somedir/header.html %}`{% endraw %}
where the "somedir" is relative to the final generated resting spot of the page you are creating.

You can add this snippet from anywhere on the site. Good to know in case you have a random file that needs to be in a non-includes folder, but also much more finicky to use as the file path needs to be spot on in order for the file to be included, and Jekyll likes to move around files after the final include, so good luck keeping the paths straight.

The correct way to go about this is to send your code snippets to the includes folder, then include them using the first method I tried. This is because the Jekyll has an _includes folder filepath baked into its generation that is used without having to specify a specific folder on the site. No need to mess with filepaths when Jekyll manages that for you.

The second thing I did was add a layout for my homepage. At first I kept it barebones and just attempted to copy and paste the header and footer into the layout, then using the {% raw %}`{{ content }}`{% endraw %} section to add the parts of the page that make it unique. 

On the index.md file itself I added some front matter to specify the layout and name of the page.
	{% highlight html %}{% raw %}	---
	layout: Home
	title: "Homepage"
	---{% endraw %}{% endhighlight %}
Once I got the layout working, I replaced any previously abstracted portions of the layout that I would use sitewide so they could be reused in other layouts as well. By this point, it went better as I had figured out the layout of Jekyll and gained some understanding of why Jekyll was not generating with the included file content that I had been expecting.

The final thing I abstracted away was the layout. Previously I had been using the css and scss files from HTML5UP directly from the root directory. I noticed however that there were some major problems with this approach, the most annoying of which was, of course, the relative paths. 

This led to me often seeing an ugly, mostly white screen without any formattign, as the formatting css and scss file were not being loaded. 

Once the layout was abstracted however, and the normal filepaths being introduced, the formatting was returned to served versions of the homepage.

Unfortunately this was not the end of my woes, as even with Jekyll generating the pages with all of its content, I was still seeing issues with the markdown conversions into an actual webpage.

### Troubleshooting the Homepage
These Markdown formatting issues largely had to do with embedded links, images, and using the tab key to indent my paragraphs. 

Starting with the last issue in that list, I had to forego tab formatting (unless I want a codeblock) in my files as the generation code would pick up on anything in line after a tab as a code block. Oh well, I can live with that.

For links I had been using the failing code snippet shown below in code pages
	{% highlight html %}{% raw %} <link rel="stylesheet" href="{{ site.baseurl }}/assets/css/main.css" /> {% endraw %}{% endhighlight %}
In order to fix these bad links, I had to change the baseurl on the config.yaml file and change the code snippet itself to
	{% highlight html %}{% raw %} <link rel="stylesheet" href="{{ site.url }}/assets/css/main.css" /> {% endraw %}{% endhighlight %}

But this still didn't fix Markdown links. I had to eventually find out the correct way to format these through a formum post. Here is an example of this using the HTML5UP URL:
[HTML5 UP](https://html5up.net/ "HTML5 UP Homepage")

And after a long round of troubleshooting images, I found out that the below is the proper way to get images inserted into Markdown files with Jekyll:
![Adding Images Properly]({{ site.url }}\assets\images\2_Image-Adding.jpg){:.image.centered}

These images also needed to be included in the {% raw %}`assets/images/`{% endraw %} folder in order to be server properly.

Overall, these three issues too far too long to figure out the cause of, but through perseveranceI finally was able to generate a website through Jekyll and have its home page show up exactly as I wanted it.

And now I have... Exactly the same page that I first started with. Well, that was a lot of trouble to have "reusable code" that I'm not reusing. I should fix that. 

## Creating the first Blog Post
One of the main orders of business after I got the homepage up and running was to populate the blog section with viable blog entries! In order to do that I needed to create a new layout for blogs, and create some blogs written with Markdown.

I won't go into much detail on the creation and troubleshooting phases of creating the first blog post as I ran into, and solved many of the  issues I outlined above while troubleshooting the blog rather than the Homepage. However, I will invite you to marvel at how Jekyll is doing a remarkable job keeping my website consistent through just a few lines of code rather than a ton of copy and paste.

![Layout Code]({{ site.url }}\assets\images\2_Layout-Code.jpg){:.image.centered}
![Showing the New Blog Page]({{ site.url }}\assets\images\2_Jekyll-Blog-1.jpg){:.image.centered}

## Do I recommend Using Jekyll?
Jekyll has some quirks, but overall it is an awesome tool that I expect to save lots of typing in the future. When used right, it will be a powerful time savings tool. However, if you are having issues getting it to work for you, sometimes it is better to just do things the old school way and only utilize Jekyll's features for things like blog posts or project pages. That will require lots of tedious copy/pasting otherwise.

See the Jekyll wiki for more of the specifics on how to use it (and hopefully avoid most of the pitfalls I found).

In the next DevLog, I will be creating project pages and probably adding a number of my college projects to populate them.