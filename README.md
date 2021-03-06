
# Table of Contents

1.  [What is R?](#org88bf26b)
2.  [Install Git](#org6dff171)
3.  [Installing and using  R and RStudio](#org73ab150)

(short URL: [bit.ly/biostats18](http://bit.ly/biostats18))

This is the GitHub repository (repo) for Spg 2018 Biol 437/558

Instructor: Weixing Zhu S3-391

TA: Matthew Lundquist S3-359

If you are new to GitHub, you should check out this 
[blog post by Lauren Orsini](http://readwrite.com/2013/09/30/understanding-github-a-journey-for-beginners-part-1).
However, for this class you only need to know how to download content from the
repo.

For in-class activities, we  are going to use
the built-in capabilities of RStudio to interface directly with this
GitHub repository using the git version control software.

All lessons, examples, and assignments will be under labeled
sub-directories in the repository. For each folder, there will be
a `.org` file with all the information you need as well as any data or
supplementary material.


<a id="org88bf26b"></a>

# What is R?

R is a statical software environment for the analysis of data and the
production of graphics (R-project.org). Using R can be daunting for
the uninitiated because it is entirely command-line based. However, 
this is the greatest strength that R has because 
it is extremely flexible, customizable, and (for most things) fast. R
is also free and open-source, meaning that there are a lot of 
people out there that maintain the project and write 
specific statistical packages. There are plenty of other programs
(SAS, SPSS, MATLAB, Excel) out there that you can use to do data 
analysis but they are expensive and less customizable. 
There are other software environments out there too (Python, Julia)
for those who need a little more speed and flexibility. R brings to the table some very
powerful analysis and graphics production tools in a package that is pretty
easy to use (once you get the hang of it). It is an attractive program for
students and professionals alike and is continuing to grow in interest and
complexity. Skills in data analysis with R is now becoming a must for many looking 
for graduate or professional positions and is a great addition to a
resumé.


<a id="org6dff171"></a>

# Install Git

Whether you are using MacOS, Windows, or Linux, you will need to
download Git.

MacOS:

Download [Git for MacOS](https://git-scm.com/download/mac) and just
follow the prompts.

Windows:

Download [Git for Windows](https://git-scm.com/download/win) and
follow the prompts. The default settings should work fine.

Ubuntu: 

Open Terminal and type:

    sudo apt-get update
    sudo apt-get install git

Thats it, now you have Git!


<a id="org73ab150"></a>

# Installing and using  R and RStudio

These are the instructions for MacOS, but they should be similar to
what you need to do in Windows or Linux

1.  Download latest version of `R` from
    [cran.r-project.org](https://cran.r-project.org)
2.  Download the latest version of `RStudio` from 
    [www.RStudio.org](https://www.rstudio.com/products/rstudio/download/)
3.  Open RStudio.app 
    ![img](./screenshots/macos/RStudio.png)
4.  Navigate to `File > New Project...`
    ![img](./screenshots/macos/new_project.png)
5.  Choose `Version Control`
    ![img](./screenshots/macos/choose_vc.png)
6.  Choose `Git`
    ![img](./screenshots/macos/choose_git.png)
7.  Set `Repository URL: https://github.com/mlundquist/biostats-2018`
    and set the `Project directory name: biostats-2018` and 
    set `~/Desktop` (or whatever directory you want to
    use) then select `Create Project`
    ![img](./screenshots/macos/git_location.png)
8.  At this point RStudio should download everything from this GitHub
    repository into your project directory (bottom right).
    ![img](./screenshots/macos/project_directory.png)
9.  You can now navigate folders and open files directly in
    RStudio. For example: `Open example.r` and it will open
    in the built-in text editor (top left)
    `screenshots/macos/R_example.png`
10. Content will be added and updated in the
    repository frequently. To download the new content, you simply need to
    `Pull` the code from the repository. Do this by
    navigating to `Tools > Version Control > Pull Branches` 
    ![img](./screenshots/macos/pull_branches.png)

When in doubt, you can also get the files off of GitHub by downloading them
manually. To do this:

1.  Click on the folder that contains the file you are interested in.
2.  Click on the file you are interested in downloading.
3.  On the top right corner you will see a button that reads `Raw`.
4.  Right click on `Raw` and select "Save Linked File"
5.  Depending on your browser, it will either download automatically or you can choose where to download it on to your machine.
6.  You should now be able to read and edit the file.

[TA Blog](http://www.lundquistecology.com/blog.html)

[Biologist's Analytic Toolkit by Dr. Bill Stein](http://biotoolbox.binghamton.edu)

[MyCourses](https://mycourses.binghamton.edu)

