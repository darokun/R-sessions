---
layout: post
category : updates
tagline: "Supporting tagline"
tags : [recoding, types of variables]
---
{% include JB/setup %}

# Recode continous variables into several categories:
So, I've noticed that some of you have had a hard time trying to recode the continuous variable age into a categorical one. However, I have seen some nice approaches, and would like to provide a summary of at least four possible ways in which you could tackle this problem. I have named the resulting variable from each method `age.cat` + the number corresponding to each method (either 1, 2, 3 or 4).  

These examples assume that you have already set your working directory using `setwd()`, that you have read in your data using `read.table()`, and that you have attached your data using `attach()`. I will be using `nhanesdataset_a.tsv` for the examples, but you may use whichever you like the most.

### 1. Using logical operators.
This is the way that Riccardo and Vindi showed on class, and the one that they recommend. The nice thing about this approach is that is very straightforward: if you understand the logic of "greater-than" and "smaller-than", is very easy to come up with this solution. Plus, you'd get to practice using R's subsetting and logical operators. From my point of view, the main disadvantage about this method is having to type too much.

{% highlight r %}
age.cat1 <- NULL                          # I create a new empty vector called age.cat1
age.cat1[age >= 20 & age <= 34] <- 1      # I set the first age level to be between 20 and 34
age.cat1[age >= 35 & age <= 49] <- 2      # Second level: 35-49
age.cat1[age >= 50 & age <= 64] <- 3      # Third level: 50-64
age.cat1[age >= 65 & age <= 79] <- 4      # Fourth level: 65-79
age.cat1[age >= 80] <-5                   # Fifth level: more than 80
age.cat1 <- as.factor(age.cat1)           # I convert age.cat1 into a factor
tab$age.cat1 <- age.cat1                  # I add age.cat1 to my dataset as tab$age.cat1
summary(age.cat1)                         # check variable
{% endhighlight %}

{% highlight text %}
##   1   2   3   4   5 
## 761 800 786 556 206
{% endhighlight %}

As you can see, most of the subjects are included in levels 2, 3 and 1, respectively and in decreasing order. The group with less subjects is number 5.

---

### 2. Using the function cut():
The function `cut()` literally 'cuts' the continuous variable at specific cut-off points (determined by you!), and adds the amount of subjects in each resulting level to a new variable that we then convert to a factor. In this example I have also set an `age.labels` character vector, to tell `cut()` what's the name of my new levels, in a way that makes sense to a human. The advantages of this method are that it doesn't require too much typing and that the code is easy to read. The main disadvantage is that if you don't know how the function `cut()` works, the reader may not understand what's going on. If you want to learn more about this function, you may use the help by typing `?cut`. This is the example:

```r
# I create labels for each age group
age.labels <- c("20-34", "35-49", "50-64", "65-79", ">80")      
# I cut the variable age according to my desired points and label each resulting group with age.labels. Plus, I put everything directly into a variable called age.cat2, and add it to my dataset as tab$age.cat2
tab$age.cat2 <- cut(age, c(19, 34, 49, 64, 79, Inf ),
                    labels = age.labels)
# check variable:
summary(tab$age.cat2)
```
```
## 20-34 35-49 50-64 65-79   >80 
##   761   800   786   556   206
```

As you may notice, the amount of subjects per level is exactly the same as the one we obtained using the first method.

---

### 3. Using the function recode():
Since the exercise actually says the word "recode", I found a function that does exactly that: takes values in a continuous variable and recodes them into levels of a categorical variable. The `recode()` function is included in the car package, so you need to install and load this package before trying to use the `recode()` function. The advantages and disadvantages are similar to using `cut()`, but the fact that you actually need to install and load a package makes it less friendly. Plus, I think that the way you specify the levels is not as straightforward as with other methods. As usual, for more info about this function, you may type `?recode` or `??recode` into R.

```r
install.packages("car")
library(car) #Load car package for using function recode

# use recode() to recode the age variable into 5 categories with desired cut-off points, make it a factor, and add it to my data set as tab$age.cat3:
tab$age.cat3 <- recode(age, "20:34='1'; 35:49='2'; 50:64='3'; 65:79='4'; 80:Inf='5' ", as.factor=T)

# check variable:
summary(tab$age.cat3)
```
```
##   1   2   3   4   5 
## 761 800 786 556 206 
```

Once again, results should be the same as with methods 1 and 2.

---

### 4. Using for loops and if statements:
Some of you may already have experience with other statistical packages and programming languages, and might understand better by using `if else` statements. The thing about R is that you need to use its proper syntax, and you may need to use a `for` loop when trying to use an `if` (and optionally `else`) statement. There are many ways to do this, but one of the ways I've come up with is:

```r
age.cat4 <- NULL # create variable

for(i in 1:nrow(tab)) {                               # initiate for loop
  if(age[i] >= 20 & age[i] <= 34) age.cat4[i] <- 1    # first level
  if(age[i] >= 35 & age[i] <= 49) age.cat4[i] <- 2    # second level
  if(age[i] >= 50 & age[i] <= 64) age.cat4[i] <- 3    # third level
  if(age[i] >= 65 & age[i] <= 79) age.cat4[i] <- 4    # fourth level
  if(age[i] >= 80) age.cat4[i] <- 5                   # fifth level
}
age.cat4 <- as.factor(age.cat4)                       # convert to factor 
tab$age.cat4 <- age.cat4                              # add to data set as tab$age.cat4
summary(age.cat4)                                     # check variable
```
```
##   1   2   3   4   5 
## 761 800 786 556 206 
```

I tried to make the code as readable as possible. During the R-sessions some of you tried to do this, and initially I made it too complicated by using several curly brackets, so now I've tried to get rid of all unnecessary typing. Notice that the results are exactly the same as for methods 1, 2 and 3.

---

### Final blow: Check all results at once to see if they're the same.
Now, what I'd like to do is make sure that ALL results from the new 4 variables are exactly the same. To do this, I'm using a function called `rbind()`, which literally binds into rows whatever information you want to present, so there's like a 'table-like' display of the data. It is also interesting that `rbind()` has a sister function called `cbind()`, which does the same thing, but aligning the variables by columns. I'm going to stick to `rbind()` for this example, but you may check the help files at `?rbind` and `?cbind` and explore both as you like.

```r
# First, detach and re-attach your data to avoid any errors:
detach(tab)
attach(tab)       # you'll get a warning that you can ignore

# Check that all four new variables are equivalent:
rbind(table(age.cat1), table(age.cat2), table(age.cat3), table(age.cat4))
```
```
##        1   2   3   4   5
## [1,] 761 800 786 556 206
## [2,] 761 800 786 556 206
## [3,] 761 800 786 556 206
## [4,] 761 800 786 556 206
```

## Conclusions:
* R provides several ways of doing the same things.
* Choose the methods you're most comfortable with.
* If you have a problem, it is most likely that somebody else has already had the same problem. Look for help within R, but also on the Internet (Google, Stack Overflow, R Pubs, etc.).

## Bonus:
* As usual, you may find the complete R script for this entry by [clicking here](https://github.com/darokun/Others/blob/master/RecodeContinuousVariablesIntoCategories.R).