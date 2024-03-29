[![Netlify Status](https://api.netlify.com/api/v1/badges/1865e135-1a60-4eca-8a60-b256b0e7cf9e/deploy-status)](https://app.netlify.com/sites/futreswebsite/deploys)

# FuTRES Website Source Files

This repository contains the source files for generating the [FuTRES website](http://futres.org/).
To make changes to the FuTRES website, simply edit the files in the ```content``` directory corresponding
to each section (e.g. about.md, team.md, etc...).  All content is written in Markdown, and you should 
be able to get a reasonable fascimile of your changes as you edit in github by using the "preview" button.  

When you are done making changes, you will need to wait a couple of minutes for your changes to go live.

How does this system work?  Pages on our site are first written in markdown, and when changes are committed to github, the build site netlify is notified, which then runs  "hugo" (a static site generator) to build the FuTRES website.   The site uses the "Kube" theme for Hugo, which we have written some additional small customizations to control rendering.

How to build site:
First, make sure you have Hugo installed locally.  Once that is done:
```
hugo server -D
```

Please note that you should make changes to the develop branch first and then make a PR to master to deploy to production site
