# FuTRES Website Source Files

This repository contains the source files for generating the [FuTRES website](http://futres.org/).
To make changes to the FuTRES website, simply edit the files in the ```content``` directory corresponding
to each section (e.g. about.md, team.md, etc...).  All content is written in Markdown, and you should 
be able to get a reasonable fascimile of your changes as you edit in github.  

When you are done making changes, you will need to wait 10-30 minutes and the netlify and github should have 
built the site and changes will be live at the [FuTRES website](http://futres.org/).

## OLD Process for making changes go live (For Developer use only)

 * Pull this repository into ```{MYREPOS}/futres_website```
 * Pull futres.github.io repository into ``` {MYREPOS}/futres.github.io```
 * ```cd {MYREPOS}/futres_website``` 
 Make changes as needed to the files contained here (using Hugo syntax/methods)
 * Execute ```hugo``` command on command-line 
(note that the config.toml file specifies the location of the output files, which in our case is ../futres.github.io/ )
 * Push changes into both ```futres_website``` and ```futres.github.io```
