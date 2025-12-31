---
title: Why and how I made this blog
date: 2025-02-15 00:28
categories: [Tutorial]
tags: [howTo]
---

## Intro  

### Why  
The inspiration for this blog came from the [NetworkChuck](https://www.youtube.com/watch?v=dnE7c0ELEH8&t=0000s) film, which:

- firstly, made me realize that there are many topics worth sharing and looking at from my own point of view  
- secondly, many things that are currently being worked on are worth noting and sharing with your loved ones, and at the same time, others may find some value in this content  
- and thirdly, the entries will serve as a way to organize knowledge and provide instructions for the future when I return to one of the topics, allowing me to verify my knowledge and way of thinking over time  

The way NetworkChuck built his blog is impressive, but I find it a bit too complicated, especially later when one of the scripts stops working, and troubleshooting the error becomes time-consuming. However, it would undoubtedly be an interesting and educational experience.  

For building my blog, I adopted the following assumptions:  

- a simple format  
- hosting on GitHub Pages  
- a local repository for the blog  
- writing posts in Obsidian (sometimes using existing notes)  
- synchronizing Obsidian with GitHub hosting  

All the tools and services I used are completely free, which provides additional motivation and relieves me of the pressure of tracking payments for a domain or hosting—especially since I intend to maintain this blog as a hobby.  

### How  
This [film](https://www.youtube.com/watch?v=m1RYsmOMPLs&t=0s) turned out to be helpful in achieving my goal. Although, currently, due to a configuration error with Ruby on my macOS, which I haven't been able to fix easily, I can't run the site locally for now—only on GitHub hosting.  

This doesn't cause me any inconvenience currently because I create posts as .md files in Obsidian and then, after synchronizing the directories, push them to the remote GitHub repository, and everything works fine.  

## Step by step manual  

We start with the [Chirpy](https://github.com/cotes2020?tab=repositories) repository, which is a theme based on [Jekyll](https://jekyllrb.com/) (a static site generator).  
- Go to the repository https://github.com/cotes2020/chirpy-starter 
![](media/chirpy1.png)
Click "Create a new repository".  

- In the "Repository name*" you must put your GitHub username and extension github.io: username.github.io  

> You must use this exact format, otherwise your site won't work. 

In my case, it is: `theherq.github.io`  

![](media/chirpy2.png)
Next click “Create repository” (this repo must be Public)    
- Next go to your repository named user.github.io and click "Action" tab.  
![](media/myrepo1.png)
Wait until you see green checkmarks.   
![](media/myrepo2.png)

- Now go to your "Code" tab and click green button "<> Code" and copy your address.  
![](media/myrepo3.png)

- Open your terminal and enter command `git clone https://github.com/username/username.github.io.git` replacing username in the address with your own username.  
- Now that you have your repository locally, open it in your favorite editor (in my case it's VS Code) and edit the `_config.yml` file:   
	- `timezone: Your/Timeone`   
	- `title: Your Blog Title`  
	- `tagline: Your Subtitle`  
	- `description: Your SEO Meta`  
	- `url: "https://username.github.io"` - it is your site address - don't confuse with repository address  
	- `github username: your-github-username`  
	There are many other settings you can change and customize, but the ones I listed above are the most important to get your blog up and running.  
	
	> `url:` and `github username:` are the most important
	> Remember about spaces after ":" e.g. `url: "https://username.github.io"` and about quotation marks at the website address.  
	
![](media/config1.png) 

The last thing left for you to get your blog online is to commit the changes and push them to the remote server.  
In the terminal (while in your blog repository, of course) type:  
- `git add .`  
- `git commit -m "Modify _config.yml"`  
- `git push`     

And that's it, you can go to your repository on GitHub, go to the "Action" tab and wait until the checkmarks turn green.  

After that you can visit your blog page at: https://username.github.io  

To create a new post on your blog, go to the `_posts` folder and create a new file in it, the name of which will be: `YYYY-MM-DD-YOUR-TITLE.md`   
> The file name format is crucial to the proper functioning of your blog.

At the very top of your post you need to place a Front Matter with the following elements:  
```
---
title: Your post title
date: YYYY-MM-DD HH:MM
categories: "[YOUR-CATEGORY]"
tags: "[YOUR-TAG]"
---
```
If you want you can also add `pin: true` which means this entry will always be at the top.  
  
That's all!  
I know there are much easier ways to create your own blog, but this one seems interesting to me because of its nerdiness.   
  
Enjoy it.  