
# Table of Contents

1.  [Part 1: Install R, RStudio, and Git and clone this repo](#org53a491d)
2.  [Part 2: "Pull" data and set working directory](#org005ac77)
3.  [Part 3: Writing your first .R file](#orgaa41244)
4.  [Part 4: Inputting data](#org4e0ab25)
5.  [Part 5: Exporting data](#orgd986897)
6.  [Part 6: Basic calculations](#orgf8a6168)



<a id="org53a491d"></a>

# Part 1: Install R, RStudio, and Git and clone this repo

Please read the main
[README](https://github.com/mlundquist/biostats-2018) for where to
download R and RStudio and how to use the version control (git)
feature in RStudio.

Then create a R project in a directory of your choosing using the Git version control and 
entering in the url for this repository: `https://github.com/mlundquist/biostats-2018`.


<a id="org005ac77"></a>

# Part 2: "Pull" data and set working directory

Once you have your project set up, navigate to  `Tools > Version Control > Pull Branches` 
to get an updated version of the repo on your system.

You now need to point R to where your data is. You can do that using the `setwd()` command
or (more easily) using the built-in functionality of RStudio. Navigate to 
`Session > Set Working Directory > To Project Directory`. You should see the `setwd()` 
command pop up in the Console window (top left) with your project directory inserted. 
The command runs automatically, so R should now be pointed at your project directory. 


<a id="orgaa41244"></a>

# Part 3: Writing your first .R file

R is a program that lives almost exclusively in the command line. This
is great for streamlining your work flow: you type in what you want R
to do, press `ENTER` and off you go.

**But** once you press `ENTER`, that code is basically gone
and you better hope you didn't have any typos!

The **BETTER** way of working with R is writing a plain text document 
that has all of the R commands you will need and saving it with a ".R" 
extension. Any command that you want to pass to R should be written
down  in an .R file. You can save R commands in any format you want 
(.docx, .txt) but if you want to be able to use it directly in R or 
RStudio, you need to use the .R extension.

You can use any text editor you want. Some examples are Notepad 
(built into Windows), TextEdit (built into OSX), Notepad++, Atom,
Sublime Text, Emacs or Vim. The last four also have plugins designed 
to work directly in R from that particular program. I have used all 
of these and really can't suggest one over the other. (If you are
curious, I currently using Emacs).

You can also use the built-in text editor in RStudio. It is located by 
default in the top left quarter of the program window. In that box you 
can write your code and use a keyboard shortcut, `Ctl + Enter` in
Windows, `Cmd + Enter` in MacOS to evaluate that code right
in an R console session.

R scripts generally have two parts: `code you want to run`, 
and annotations to code using comments, `#`.

Here is an example script:

    
    ## Sample R script
    ## Author: Matthew Lundquist
    ## Date: 12-20-2017
    
    ## This is my first R program, it prints "Hello World"
    print("Hello World")

Save it as `my_first_script.R`


<a id="org4e0ab25"></a>

# Part 4: Inputting data

The next step is to actually use R to input and analyze your data. 
First we need data. In this case the data, `iris.csv`, is saved 
as a comma separated value (.csv) file. You can also save data as .txt
if you want. Data can be edited directly in those files using a text editor
but it is easier just to use a spreadsheet application like Microsoft 
Excel, Sheets, or Libre Office Calc and then saving them as a .csv.

If you already `Pulled` this branch, you should already have `iris.csv`.

Then you can copy and paste the following commands into your `my_first_script.R`

    
    ## Inputting data in R from .csv file
    
    ## Read in iris.txt and name it iris (make sure first row is
    ## recognized as column names
    
    iris <- read.csv("iris.csv", h = T)
    
    ## Call the data to make sure it is inputted correctly
    
    iris
    
    # We can navigate the data using $ in R
    names(iris) # This tells us what each of the columns are named, these are X-values
    
    length(iris$Sepal.Length) # How many Sepal.Length observations dow e have? (Notice it is case-sensitive)
    iris$Sepal.Length # This will show all of those Sepal.Length observations 
    
    ## Short hand for above
    length(iris[,1])
    iris[,1]
    
    ## You can also look at particular observations
    iris$Sepal.Length[10]
    ## or
    iris[10,1]
    
    ## The 5th column is our grouping variable, we can see how many groups
    nlevels(iris$Species)
    ## And what those levels are
    levels(iris$Species)
    
    ## If you just want the "setosa" data, you can subset the data
    iris_setsoa <- subset(iris, iris$Species == "setosa") # Nottice that I used a "<-" to assign a name to my new data
    
    ## If you are just interested in Petal.Length of setosa, you can just subset that column
    iris$Petal.Length[iris$Species == "setosa"]

Notice that there are **150 rows** of data and **five columns**. 
Each row represents an individual iris flower. The first four columns 
indicate what was measured from that flower. The last column
identifies the species of the flower. 

The first four columns are what we would call **numerical data**, 
we can perform mathematical operations on them. The last column is 
what we would call a **factor** or a **identifier** or a **grouping
variable** for your data. In this case, the column "Species" 
indicates from what species of iris the data was collected. 
There are a total of three species (three factors) in this data set.


<a id="orgd986897"></a>

# Part 5: Exporting data

You can also export your new data to your project directory:

    ## If you want to export your subsetted data, you can do that easily too
    write.csv(iris_setosa, "~/NewDirectory/iris_2.csv", rownames = FALSE)

If you add or edit files in your project directory, it 
 will mess up your next `PULL` because your 
local directory now does not match the repository. 
The best way to deal with is to 
tell save anything that is not from the repository in another directory
on your machine. If you are using a lab computer, this could be in your network drive
or on a USB stick. That will ensure that your work is saved on your 
local directory and it will not conflict with
what is in the repository. 


<a id="orgf8a6168"></a>

# Part 6: Basic calculations

Now that we have some data, we can do some basic calculations on that data. Here 
is an example script that you can paste into `my_first_script.R`:

R is basically a calculator with a lot of functions built into it. 
For everything you can calculate,there is probably a function:

    x <- 1
    y <- 2
    
    x + y # or
    sum(x, y)

You can also do basic statistics, including calculating averages by combining functions
or using the built-in function `mean()`:

    ## What is the average Sepal.Length in Iris?
    sum(iris$Sepal.Length) / length(iris$Sepal.Length) # or
    mean(iris$Sepal.Length) 
    
    ## You can use subsetting to caclulat the average Sepal.Length in Iris setosa?
    mean(iris$Sepal.Length[iris$species == "setosa"]) # or
    mean(iris_setsa$Sepal.Length) # if you already subsetted the data

There is also a built-in function called `summary()` that will give you a whole suite of
summary statistics for your data:

    summary(iris)

Try it out!

