# futres_website

This repository contains the source files for generating the [FuTRES website](http://futres.org/).
To make changes to content, fork this repository and edit the files in the ```content``` directory corresponding
to each of the sections on the [FuTRES website](http://futres.org/).  When you are done, make
a Pull Request and John will review change suggestions and use the following process to make it live.

## Process for making changes go live

 * Pull this repository into ```{MYREPOS}/futres_website```
 * Pull futres.github.io repository into ``` {MYREPOS}/futres.github.io```
 * ```cd {MYREPOS}/futres_website``` 
 Make changes as needed to the files contained here (using Hugo syntax/methods)
 * Execute ```hugo``` command on command-line 
(note that the config.toml file specifies the location of the output files, which in our case is ../futres.github.io/ )
 * Push changes into both ```futres_website``` and ```futres.github.io```
