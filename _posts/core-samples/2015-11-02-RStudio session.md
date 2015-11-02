---
layout: post
category : updates
tagline: "Supporting tagline"
tags : [RStudio session, workflow]
---
{% include JB/setup %}

## RStudio session
In RStudio, a session begins when you open RStudio, and ends when you close the software. If you close the software, you'll get a prompt asking you if you want to save your progress or not. However, you're only able to save your R Scripts and R Data, but not all of your settings. 

In this post, we'll learn about all the necessary steps to follow each time you want to use R (or RStudio). But first, let's recall how does RStudio look like when you open it.

## Anatomy of RStudio
When you open RStudio, you may see a screen similar to this one:
![RStudio Main Screen](https://36.media.tumblr.com/2ed3a2cb94069b9107b6ea5c0c99a51d/tumblr_nx6xisTPg61qahqiuo1_540.png)

There are at least 3 subscreens:

* Left: the Environment/History subscreen
* Upper Right hand side: The Console subscreen.
* Bottom Right hand side: The Files/Plots/Packages/Help/Viewer subscreen.

Perhaps these subscreens have a different arrangement in your computer. We'll learn how to configure the position of these subscreens in a future post.

A very important subscreen that we need yet to see is the Scripts subscreen.
In order to open it, you may do one of these:

* Go to the File Menu > New File > R Script: ![Open R Script from File Menu](https://40.media.tumblr.com/b932bac57512f8595862f808130c0138/tumblr_nx6y2bMVKN1qahqiuo3_1280.png)

* Click on the white sheet icon with a green plus sign located at the upper left corner of RStudio, and choose R Script: ![Open R Script from button](https://36.media.tumblr.com/c145730ea80f7ddcae0de7b98b38777e/tumblr_nx6y2bMVKN1qahqiuo2_400.png)

* Press shift+Cmd+n on Mac, or ctrl+shift+n on Mac and Windows.

Once you have opened your R Script subscreen, your RStudio session might look similar to this:
![RStudio with R Script subscreen](https://40.media.tumblr.com/1a899c362fcafa8260d0dc064f35942a/tumblr_nx6y2bMVKN1qahqiuo1_1280.png)


## Getting started
The first step I recommend when using RStudio is to use R Scripts to write, edit and store all of your code. 
You may write anything you want in this script file, and RStudio will ignore it until you run that line of code.

The second step I always recommend to do, is to tell R and RStudio where to look for files in your own computer. This process is called "Setting the Working Directory", and we can use the function `setwd()`. In order to do this, you may want to use a similar line of code to this one when working from the computers in Kursraum 5:

```
setwd("/usr281/ben/msc15xx/rest_of_your_path")
```

Where:

* `setwd()` is the 'set working directory' function, 

* `msc15xx` is your personal msc number (write `phd15xx` if you're a PhD-CIH student, and replace the last two x's by your own number), 

* and `rest_of_your_path` refers to all the folders and subfolders that you have before getting to the one where your data are located at.

**Note: The path should be enclosed in quotation marks to work!**


If you're working on a mac computer, your path might look something like this:

```
setwd("~/Documents/rest_of_your_folders")
```

Where `~` represents your User name (you don't need to write your name, the `~` sign is enough), and `Documents` could be some other folder (like your `Desktop`, `Dropbox` folder, etc.).

If you're working on Windows, the path might look like this:

```
setwd("c:/docs/mydir")
```

And, as usual, **be sure to change all of your folders according to your own computer's architecture and configuration!!!**.

In order to run a command such as `setwd()`, you can either go to the Run button located in the upper right corner of the R Script subscreen, or press cmd+Enter on a mac (or ctrl+Enter on Windows):
![Run Commands](https://41.media.tumblr.com/e67f2292e3d9316eb1e906b9eae2bc6d/tumblr_nx712qMrvb1qahqiuo1_1280.png)
Every command you run from the R Script subscreen will appear in the Console subscreen, along with any output from R. If R doesn't do anything (no errors, no warnings, no nothing), it means it worked but the command you used has no output.

## Loading data
Once, you've set up your working directory, you can ask R to see which files are there in your working directory, just to make sure that your data files are there. If you run the `dir()` function, you're asking R to tell you which files are in your *dir*ectory:

```
dir()
```

and it should return something like:

```
> dir()
[1] "nhanesdataset_a.tsv" "nhanesdataset_b.tsv" "nhanesdataset_c.tsv"
[4] "nhanesdataset_d.tsv" "nhanesdataset_e.tsv"
```

You could have more files, but at least your data set files should be in there. If they are not, or if you get any errors, repeat setting the working directory and **make sure you're using the right path to the folder where your data set files are!**

Then, you're ready to read-in your data, using the `read.table()` function. Use a code similar to the one we learned in the [R course - Lecture 2](http://www.en.msc-epidemiologie.med.uni-muenchen.de/download/winter-term-15__6/quantitave-methods/r-course/r-course_l2_datasets_plots.pdf):

```
tab <- read.table("nhanesdataset_a.tsv", sep="\t", header=TRUE)
```

To find out more about the `read.table()` function, you could go to its help page by typing:

```
?read.table
```

## Work on your data
Now you're finally set to start analyzing your data!

## Comments
I highly recommend using comments to specify what you've done, and either make it understandable for someone else, or for your future-self! In R, you can write the pound or hastag sign (`#`), and everything you write after this sign will be a comment. Comments are ignored by R. The comment ends when you start writing in a new line:
![Working with comments](https://41.media.tumblr.com/0c92dbdf787fc9acfc8bbbfe45fe2fd8/tumblr_nx70u8oovB1qahqiuo2_1280.png)


In the image, lines 1, 4 and 7 are comments, and will be ignored by R. These comments help me remember that what I've written in lines 2, 5 and 8 is for setting the working directory, seeing the files withing my working directory, and reading the data, respectively.

## Save your R Script:
Once you're done working on RStudio, you should save your R Script to store all of the code that you used during this session.
To save, just go to File > Save, and choose a name for your file:
![Save R Script](https://41.media.tumblr.com/be545993cf8a426ec4e8600b31bf0b37/tumblr_nx70u8oovB1qahqiuo1_1280.png)

Alternatively, you can also press cmd+s on mac or ctrl+s on windows. 
Next time you open RStudio, you only need to run these lines of code again, without having to type your working directory path and everything.

## Concluding remarks
A typical RStudio session workflow goes as follows:

1. Open RStudio
2. Open a new script file (or a previously saved script) and write everything in there
3. Set your working directory
4. Read-in your data
5. Work on your data
6. Use comments as often as you like
7. Save your R Script



