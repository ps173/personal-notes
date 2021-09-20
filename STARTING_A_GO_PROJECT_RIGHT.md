# Introduction

These are the points from this [video](https://www.youtube.com/watch?v=Ot9Em123Fz8&t=52s).  
I noted the points that i thought were important. Rest u can check the video again

# Starting

In a go project or any project always try to keep a readme and a license in it.

Next step is initializing the repo

1. GO to github and make a repo
2. Then run this command in command-line  
   $ `go mod init [repo-url]`

This creates a go.mod file which has the name of the repo u r using in it and also the version  
of go that u r using. You will probably need a something like replace which allows u to do concurrent  
package development.

# Cool stuff about go syntax

-   Use Capital letters to export stuff i.e. no export statements which is
    cool.
-   U can do go install to install current project to ur bin folder or go path
    so that it becomes globally available.
-   Remeber to name package and file to be same it is a good practice.
