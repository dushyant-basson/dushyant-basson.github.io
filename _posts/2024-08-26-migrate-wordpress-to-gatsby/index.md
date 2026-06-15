---
author: "Dushyant Basson"
date: "2024-08-26"
slug: "migrate-wordpress-to-gatsby"
tags:
- wordpress
- gatsby
- markdown
title: "Migrated website from WordPress to Gatsby"
---

## Why?

In 2019, after diving back into programming, I had converted onizu.com from a static architectural portfolio to a Wordpress driven site, having the blog section and other pages. The previous versions of the site didn't have any CMS. Since I had been away from programming for over a decade, Wordpress was a comfortable choice to quickly set up a new site as I had worked with it. Though Wordpress is a powerful and feature-rich environment, over the period of time, there were a couple of things that were making me feel a lack of control on the website.

I didn't have the time to write my own theme. So I used some pre-designed theme and tweaked it. This served my needs for a while. However, since I had been designing websites professionally in the past, the lack of control over the complete UI structure started bothering. 

Another thing that bothered me was the Wordpress engine and the database that needed to be hosted & maintained for a few static pages. I had not been writing blogs much either.

## Why Gatsby?

Now I could have taken the time to learn and write my own Wordpress theme instead of learning & implementing Gatsby, given that I had worked with PHP & MySQL in some projects. I had been using ReactJs for some apps and was quite happy with the dynamism it provided in the frontend. Learning that Gatsby had some good support for querying data from Markdown files using GraphQL, I got excited by the idea of migrating the posts from WP to Markdown files and setting up the blog system in Gatsby. And the fact that it is based on ReactJs, I could now leverage the dynamism of JS into the pages.

So here I am writing this post in Markdown, knowing that it would be queried from its directory and listed on the blog by the system in place. Got to say it is fun to write and format text in Markdown comparatively.

## Migration

The first step was to see if the existing blog posts could be exported from Wordpress in Markdown format. I made use of some amazing utilities like [**exitwp**](https://github.com/some-programs/exitwp) and [**wordpress-export-to-markdown**](https://github.com/obedparla/wordpress-export-to-markdown) to achieve that, which much deserve a mention. The process requires exporting the Wordpress data in XML format and then these utilities work with it to produce corresponding Markdown files and even download the images in the posts (though I had to manually export some images). I then cleaned up the resulting Markdown data (not all the formatting had come proper from the conversion) and organised it in the desired directory structure. 

The next step was to set up Gatsby plugins and GraphQL queries to read and process the markdown files. As mentioned earlier, the Markdown post files did need to be cleaned up and re-formatted, including the frontmatter part (the slug, title, tags, etc.). I kept the paths & slugs consistent with the previous site so as to keep the SEO data intact. Next I set up the **`createPage`** API of `gatsby-node.js` to dynamically generate pages for each post (and other static pages). This more or less was it for the blog system to be up and running. 

Then it was all the layout formatting and styling. I did have to manually implement the media queries in the CSS files to make the various layouts responsive, which was something that was taken care of by the 'themes' in Wordpress.

For the other sections of the website, the built-in system of Gatsby for generating pages and routes based on files & sub-directories in the **`pages`** directory was fun to use as I didn't have to manually create and maintain a routing system.

## Finally

The result is a _database-less_ website with all the data organised in the desired structure in the form of files. 

I must mention again that Wordpress is a great CMS out there if you need it, and it has had a good amount of development over the years.
