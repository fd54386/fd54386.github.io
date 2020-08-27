---
layout: post
title: "R in Data Science"
---

  I've worked with several programming languages over my career.  Usually the choice of languages is driven by the answer to "Which language has the most relevant library already?"  Strong secondary considerations are "Is there a good IDE for it?", "Is it strongly typed?" (Strong typing is easier to troubleshoot), and "Does everyone else in the team already work with it and have the appropriate licensing?" are strong secondary factors.  Speed is thus far a distant third, but there are usually options to offload work to servers in SQL / Spark or to call functions written in C as necessary.

  In the context of R vs Python for datascience, I tend towards R. Both have very good datascience libraries -- Python tends to be ahead with machine learning libraries, but R has decades of statistical package development and is still the go-to for Statistics academics.  Each language has ongoing work to balance out the differences, but R's statistics make it easier to explore and run diagnostics on data.  RStudio is another strong point in R's favor. It's a mature and robust IDE, and the cheatsheets they put out for popular R packages save a lot of time digging through documentation.  Python on the other hand has a lot of environment competitors -- at some point I'll take a day and try the most popular ones to have an informed opinion, but I've yet to find one that feels easy to navigate. The other points are a wash -- neither is strongly typed.  Both R and Python have minimal licensing issues compared to SAS. If a team doesn't yet have a preference, you can download and try them both without needing to cut a check.  

  R does have one nuance that I'm undecided about -- vectorized operators and functions.  I haven't run into them in other languages.  Take for example trying to perform some multiplication on a vector x:  
```r 
x<- c(1,5,7,4)
print(x * 2)
```  
  Under the hood, someone has already defined an operator that takes a numeric vector on the left and some sort of numeric on the right, and iterates along all indices to perform the same operation on every element.  Well, what if I want to get several multiples of x, I should just be able to define a vector of factors to multiply against, right?

```r 
x<- c(1,5,7,4)
y<- c(1,2,3,0)
print(x * y )
```  
Nope, element-wise multiplication.  What about non-matching lengths?

```r
x<- c(1,5,7,4)
y<- c(0,1,0)
print(x * y )
```  
Well, that's an error, but you can at least infer it's going to do the element-wise operations in chunks when the dimensions do match up.

``r
x<- c(1,5,7,4)
y<- c(1,2)
print(x * y )
``  
  At the end of the day, with all of the data analysis and operations that go into R, it is useful have these operators pre-defined.  In another language, you'd have to write that loop yourself to iterate across every element.  Sure you could define your own operator or function so that you'd only have to write it once, but you would have to write it.  
  
  The downside is, particularly since objects aren't strongly typed -- it takes a lot of practice to know what dimensions are going to be returned.  If I call the `mean` function on a dataframe, is it going to go column-wise and give me a mean for every field? Or maybe it's going to average every column?
```r
mean(iris)
```
  Nope, doesn't work at all.  Per `help(mean)`, the function supposedly takes 'An R object.' But it apparently doesn't work with a list of vectors.  Turns out you needed `colMeans()` to input a dataframe and get column-wise results. So, alright, R adds a bit of guesswork into your code design if you don't have experience with the functions.  Strongly typed languages don't really have this problem -- they have to be explicit about input and output types. There are always going to be quirks and bugs to work out whatever language you use, but with enough work you've got a robust & polished product.  R's particular set of quirks are just a little different, and it's nice to have to rethink your approaches from time to time.
