---
layout: post
category : updates
tagline: "Supporting tagline"
tags : [booleans, George Boole's 200th birthday, google, doodle, computer science, programming, logical vectors]
---
{% include JB/setup %}

## Booleans and George Boole's 200th Birthday!
Booleans are vectors in R and other programming languages, which can take the logical form `TRUE` or `FALSE`. For example, let's compare the numbers `24` and `100`, as we did in slide 22 of [R course - Lecture 1](http://www.en.msc-epidemiologie.med.uni-muenchen.de/download/winter-term-15__6/quantitave-methods/r-course/r-course_lecture_1_intro.pdf):

We create a numerical vector of length one (because there is only one element in it), called `x`, which has the value `24`:


```
x <- 24
```

We compare `x` (whose value is `24`) against another value... let's say, `100`:

* Hey R, is `x` greater than `100`?

```
x > 100
[1] FALSE 
```

R says it's `FALSE` because `24` is **not** greater than `100`.

* Is `x` smaller than `100`?

```
x < 100
[1] TRUE
```

* Is `x` **not equal to** `100`? (In R, '**not equal to**' is written with an exclamation mark followed by an equal sign):

```
x != 100
[1] TRUE
```

* Is `x` **exactly equal to** `100`? (In R, '**exactly equal to**' is written with two equal signs):

```
x == 100
[1] FALSE
```

---

The guy who pioneered this system in the mid 1800s was George Boole, and that's why we call these logical expressions `booleans`. Google made a very nice doodle today to commemorate this date:
![George Boole's 200th B-day doodle](https://41.media.tumblr.com/25077d0db67f56c9d0879970e41cc0c2/tumblr_nx751ulZFA1qahqiuo1_1280.png)


You may find the permanent link for this doodle [here](http://www.google.com/doodles/george-booles-200th-birthday)



