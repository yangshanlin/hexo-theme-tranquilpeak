# User documentation #

This documentation will help you to install tranquil-peak-hexo-theme and configure it to use all features which it provides.  

If you want to report a bug or ask a question, create an issue.

## Summary ##

- [Installation](#Installation)
- [Hexo configuration](#Installation)
    * [Archives configuration](#Installation)
    * [Enable RSS feed](#enable-rss-feed)
- [Tranquil Peak configuration](#tranquil-peak-configuration)
    * [Sidebar](#sidebar)
    * [Author](#author)
    * [Customization](#customization)
    * [Miscellaneous](#miscellaneous)
    * [Enable pages](#enable-pages)
        * [Enable all-categories page](#enable-all-categories-page)
        * [Enable all-tags page](#enable-all-tags-page)
        * [Enable all-archives page](#enable-all-archives-page)
        * [Enable about page](#enable-about-page)
- [Front-matter settings](#front-matter-settings)
- [Running](#running)  
    
## Installation ##

1.1 Download the latest version ready for production utilisation here : [tranquil-peak-hexo-theme-v1.0.0-production]
(https://github
.com/LouisBarranqueiro/tranquil-peak-hexo-theme/releases/download/v1.0.0/tranquil-peak-hexo-theme-v1.0.0-production.zip) or choose an other version here : [all releases](https://github
.com/LouisBarranqueiro/tranquil-peak-hexo-theme/releases)
2. Rename the folder in ```tranquil-peak``` and place it in ```themes``` folder of your Hexo blog

## Hexo configuration ##

1. Modify the theme in ```_config.yml``` by changing ```theme``` variable  to ```tranquil-peak```
2. Complete ```theme/tranquil-peak/_config.yml``` with your informations by following directives in comments

### Archives configuration ###

You can choose the style of listing for archives, category and tag pages by adding this lines in ```_config.yml```  

``` yaml
# Archives
## 1: Enable pagination
## 0: Disable pagination
archive: 2
category: 2
tag: 2
```

- **0** : Disable pagination  
- **1** : Enable pagination  

Example :  
A category page look like this with ```category: 1``` :  
![archives 1](https://hexo-tranquil-peak-demo.herokuapp.com/2013/12/25/gallery-post/archives-1.png)  

The same page with ```category: 0```:  
![archives 0](https://hexo-tranquil-peak-demo.herokuapp.com/2013/12/25/gallery-post/archives-0.png)  

### Enable RSS feed ###

1. Execute ```npm install hexo-generator-feed --save``` in your Hexo blog folder  
2. Add this lines in ```_config.yml``` :  

``` yaml
feed:
    type: atom
    path: atom.xml
    limit: 20
```
- **type** : Feed type
- **path** : Feed path (Default: atom.xml/rss2.xml)
- **limit** : Maximum number of posts in the feed (Use `0` or `false` to show all posts)

If you want more informations on this plugin : [hexo-generator-feed](https://github.com/hexojs/hexo-generator-feed)

## Tranquil Peak configuration ##

### Sidebar ###

The sidebar is powerful and easily configurable.
DON'T modify variables name ```sidebar```, ```title```, ```url``` and ```icon```.  
Others variables name which refer to the name of a menu or a link can be edited. Example : ```menu```, ```home```, ```categories```, etc...  
You can add groups of links and links much as you want  
You just have to respect the indentation : `groups of links` -> `link` -> `title, link, icon`  

``` yaml
sidebar:
    menu:
        home:
            title: Home
            url: /
            icon: home
        categories:
            title: Categories
            url: /all-categories
            icon: bookmark
        tags:
            title: Tags
            url: /all-tags
            icon: tags
        archives:
            title: Archives
            url: /all-archives
            icon: archive
        about:
            title: About me
            url: /about
            icon: question
    author_links:
        # github:
        #     title: GitHub
        #     url: https://github.com/
        #     icon: github
        # stack_overflow:
        #     title: Stack Overflow
        #     url: http://stackoverflow.com/users/
        #     icon: stack-overflow
        # twitter:
        #     title: Twitter
        #     url: https://twitter.com/
        #     icon: twitter
        # facebook:
        #     title: Facebook
        #     url: https://www.facebook.com/
        #     icon: facebook
        # google_plus:
        #     title: Google +
        #     url: https://plus.google.com/
        #     icon: google-plus
        # linked_in:
        #     title: Linked In
        #     url: https://www.linkedin.com/profile/
        #     icon: linkedin
        # mail:
        #     title: Mail
        #     url: mailto://
        #     icon: envelope-o
    rss:
        rss:
            title: RSS
            url: /atom.xml
            icon: rss
```

- **title** : Title of your link displayed
- **url** : URL of the link. If the URL is internal, domain name is not necessary
- **icon** : Name of the font awesome icon class without the `fa-` (Go to [font-awesome icons](http://fontawesome.io/icons/) to find class name of icon)

### Author ###

``` yaml
# Author
author:
    email:
    bio:
    job:
    location:
    picture:
```

- **email** : Your mail address. This address will be used if you activate gravatar option
- **bio** : A short biography. Display on your about card
- **job** : Your job
- **location** : Your location
- **picture** : Your profile picture. Overwritten by your gravatar image if gravatar option is enabled

### Customization ###

``` yaml
# Customization
gravatar_image: 1                
thumbnail_image: 1               
read_more_message: Continue readiing
go_to_message: Go to the website 
cover: cover.png                 
favicon:                         
image_gallery: 1                 
```

- **gravatar_image** : Enable gravatar image. Using mail address of ```author.email```. (disable: 0, enable: 1). Overwrite `author.picture` everywhere in the blog
- **thumbnail_image** : Post thumbnail image (disable: 0, enable: 1). Display the first photo
- **read_more_message** : Message displayed after the <!-- more --> tag or after 300 characters
- **go_to_message** : Message displayed after the <!-- more --> balise or after 300 characters for post with link layout
- **cover** : Your blog cover picture located in folder `source/assets/images/`
- **favicon** : Your favicon located in folder `source/assets/images/`
- **image_gallery** : Display an image gallery at the end of a post have ```photos``` variables

### Miscellaneous ###

``` yaml
# Miscellaneous
google_analytics:
```

- **google_analytics** : Your Google analystics web property ID : UA-XXXXX-X

### Enable pages ###

Tranquil Peak provides you 3 pages to display all posts by tags, by categories, by date and an about page. To enable one of this pages, 
follow this guide.

#### Enable all-categories page ####

To enable ```all-categoies``` page :  
1. Run ```hexo new page "all-archives"```. A new folder named ```all-categories``` will be created in ```source/```  
2. Replace ```source/all-categories/index.md``` content with :
 
``` markdown
title: "all-categories"
layout: "all-categories"
date: 2015-04-27 11:51:00
---
```

New page will be reach at : ```/all-categories```

#### Enable all-tags page ####

To enable ```all-tags``` page :  
1. Run ```hexo new page "all-tags"```. A new folder named ```all-tags``` will be created in ```source/```  
2. Replace ```source/all-tags/index.md``` content with :
 
``` markdown
title: "all-tags"
layout: "all-tags"
date: 2015-04-27 11:51:00
---
```

New page will be reach at : ```/all-tags```

#### Enable all-archives page ####

To enable ```all-archives``` page :  
1. Run ```hexo new page "about"```. A new folder named ```all-archives``` will be created in ```source/```  
2. Replace ```source/all-archives/index.md``` content with :
 
``` markdown
title: "all-archives"
layout: "all-archives"
date: 2015-04-27 11:51:00
---
```
New page will be reach at : ```/all-archives```

#### Enable about page ####

To enable ```about``` page :    
1. Run ```hexo new page "about"```. A new folder named ```about``` will be created in ```source/```  
2. Replace ```source/about/index.md``` content with :
 
``` markdown
title: "about"
layout: "about"
date: 2015-04-27 11:51:00
---
```

The click on a link with ```href="/about"```  will be blocked and handled by a javascript function to animate and display a card with your informations 

## Writing posts ##

### Front-matter settings ###

Tranquil Peak introduce 2 new variables to configure precisly the style of your post : ```thumbnailImage``` and ```coverImage```.  
  
Example :  
``` markdown
thumbnailImage: image-1.png
coverImage: image-2.png
photos:
    - image-3.jpg
    - image-4.png
```

- **thumbnailImage** : Image displayed in index view
- **coverImage** : Image displayed in large at the top of your post in post view. If thumbnail image is not configured, cover image is also used as thumbnail image.
- **photos** : Images displayed in an image gallery at the end of the post. If thumbnail image is not configured and cover image too, the first photo is used as thumbnail image.

If your images are located in ```source/_posts/{YOUR_POST_TITLE}/```, you just have to enter the name of the image without domain name and path like written just above.

## Running ##

3. Run ```hexo server``` and enjoy!