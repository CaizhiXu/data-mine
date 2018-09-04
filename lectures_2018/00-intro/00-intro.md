<style>
  .reveal pre {font-size: 12px;}
</style>

Introduction to R programming
================================================
author: Rebecca C. Steorts
date: 29 August 2017


Agenda
===
- Why Machine Learning?
- Motivational Ideas
- Expectations for this Class
- Topics Covered
- Questions?

What is Machine Learning?
===
``Statistics is the science of learning from data. Machine Learning (ML) is the science of learning from data. These fields are identical in intent although they
differ in their history, conventions, emphasis and culture."

- Larry Wasserman, Rise of the Machines

Machine Learning versus Statistics
===

- Machine learning and statistics has much to learn from each other.

- In this course, we will focus on machine learning, as in other courses, you will learn the fundamentals of statistics.

- To be successful, you need both insights and perspectives. (As a follow up class, take Cynthia Rudin's machine learning course).

Motivations
===
Let's talk about a very small number of motivatinal problems in machine learning.

Think on your own about how you might try and tackle them if you had the data right now.

Apple music database
===
Suppose you have an Apple database with 2 million songs on it. How would you unique identify the number of unique songs?

\begin{figure}[htbp]
\begin{center}
\includegraphics[width=0.8\textwidth]{figures/apple}
\end{center}
\end{figure}

- What is the main issue here?

Apple music database
===
Suppose you have an Apple database with 2 million songs on it. How would you identify the number of unique songs?

\begin{figure}[htbp]
\begin{center}
\includegraphics[width=0.8\textwidth]{figures/apple}
\end{center}
\end{figure}

- How might you solve it without knowing any machine learning.

- ML buzzwords: record linkage, entity resolution, de-deduplication (types of clustering)

Electronic health records
===
Goal: identify patient risk for certain illness (kidney failure).

- Suppose there are 2 million patients.
- Suppose for now we ignore any time component.

1. Suppose you have access to Duke health records (patients) that on vitals and labs.
2. Suppose you also have access to patient notes.

How would you identify at risk patients in real time?

Hacked Webpages
===
Out of all the webpages that exist, how could you try and identify in near-real time that a webpage has been hacked?

\begin{figure}[htbp]
\begin{center}
\includegraphics[width=0.8\textwidth]{figures/hacked}
\end{center}
\end{figure}

Classifying Objects
===
Given different kinds of animals, how might we classify each animal into it's right class (cat, dog, mouse, etc)?

![plot of chunk unnamed-chunk-1](00-intro-figure/unnamed-chunk-1-1.png)



The Machine Learning (ML) culture
===
- It's fast.
- Papers are well written (and I expect your thoughts to be well written)!
- Code is reproducible (or it should be). And thus, I expect yours to be!
- In this course, we will look at standard techniques that are important to data mining and machine learning and are a good start for building your knowledge basis.

The Book
===
- The book we will use is the required text \textcolor{blue}{(\href{http://www-bcf.usc.edu/~gareth/ISL/}{Intro to Statistical Learning with R})}
- Please read all of it and follow it as we go.
- Please do the lab exercises in ISL on your own.
- For extra information that you might find interesting that is beyond this class, read the Rise of the Machine by Larry Wasserman.

The Lectures
===
- Lectures will be via slides, code, examples.
- They will be based on the book.
- Expect about 8--10 homeworks throughout the semester.
- All information will be posted on Sakai regarding deadlines.

The Homeworks
===
1. All code must be written to be reproducible in Markdown.
2. All derivations can be done in any format of your choosing (word, latex, markdown) but must be converted to a pdf document. It must be legible.
3. All files must be zipped together and submitted to Sakai as one file. Otherwise, you cannot submit. (Try this early to avoid not submitting anyting).
4. Ask questions early if you have a problem to a TA.
5. Your lowest homework will be dropped.

The Exams
===
1. All exams will be in class, closed book.
2. They will be cumulative as they go, but they will focus on the most recent material we have covered.
3. Make up exams will not be given.
4. You must take the final exam to pass the class!

Course Material
===
1. Introduction (Today)
2. Statistical Learning
3. Linear Regression
4. Classification
5. Re-sampling Methods
6. Linear Model Selection and Regularization
7. Moving Beyond Linearity
8. Tree Based Methods
9. Support Vector Machines
10. Unsupervised Learning

Typos
===
- If you find a typo on a slide, please
write it down neatly with the slide number
and give it to me after class.

- I do my best to fix typos within 48 hours after lecture with highlights in red so you can spot them.

- Thanks for helping me spot typos in advance!

Coding using R, RStudio, and Markdown
===

- In this class, I will assume that you are
very familiar with R.

- If you need to refresh certain R skills, please do this on your own.

Reproducible Code
===

In this course, all code you turn in will be expected to be reproducible.

What does this mean?

Reproducible Code
===

-  Suppose I write a lecture on linear regression with many plots explaining my analysis.

- You might wonder how exactly I created my analysis.

- If I simply write my code in a way such that you can reproduce my entire lecture, then you can verify all the results that I show you.

- Similarly, if you write your code in this way for your homeworks, then I and the TAs can also verify the results very quickly.

R versus RStudio
===

- RStudio mediates your interaction with R.

- RStudio is a driver of the emergergence of R Markdown, knitr, R + Github.



What is Markdown?
===

- Markdown is a lightweight markup language for creating PDF (or other documents).

- Markup languages produce documents from human readable text (and annotations).

- Some of you might be familiar with LaTeX (less friendly). This is another mark up language for creating PDF documents.

Why I like Markdown
===

1. It's very easy to learn.
2. The focus is on content rather than coding and debugging of errors.
3. One you have the basics, you can get fancy!

(In fact, my slides right now are in markdown, so you can even make slides)!

R Markdown
===
This just means that you include R code in your **markdown** document.


```r
2 + 2
```

```
[1] 4
```

Installing RStudio and Markdown
===
- How do I install \textcolor{blue}{\href{https://courses.edx.org/courses/UTAustinX/UT.7.01x/3T2014/56c5437b88fa43cf828bff5371c6a924/}{Rstudio}}?

- How do I include markdown?

Use the command
```
install.packages("rmarkdown")
```

More behind R Markdown
===

R Markdown files are the source code for rich, reproducible documents. You can transform an R Markdown file in two ways.

1. knit: You can knit the file.

- The rmarkdown package will call the knitr package.
- knitr will run each chunk of R code in the document and append the results of the code to the document next to the code chunk.
- This workflow saves time and facilitates reproducible reports.

In the R Markdown paradigm, each report contains the code it needs to make its own graphs, tables, numbers, etc. The author can automatically update the report by re-knitting.

More behind R Markdown
===

2. convert: You can convert the file.

- The rmarkdown package will use the pandoc program to transform the file into a new format. - For example, you can convert your .Rmd file into an HTML, PDF, or Microsoft Word file.
- You can even turn the file into an HTML5 or PDF slideshow.
- rmarkdown will preserve the text, code results, and formatting contained in your original .Rmd file.

Conversion lets you do your original work in markdown, which is very easy to use. You can include R code to knit, and you can share your document in a variety of formats.

More behind R Markdown
===
In practice, authors almost always knit and convert their documents at the same time. In this article, I will use the term render to refer to the two step process of knitting and converting an R Markdown file.

You can manually render an R Markdown file with

```
rmarkdown::render().
```

Takeaways
===
1. Make sure that you understand the class policies.
2. Make sure you can access the Google group.
3. Make sure that you can access Sakai, the first homework assignment, and start your assigned readings for the course.
4. If you feel unprepared for the class, please speak with me now, rather than later.
5. Install RStudio and markdown. Use the lab with this lecture to make sure that you can do basic exercises
in R and that they are reproducible. (If you have trouble with the lab or first few homework assignments and exam, then please see me quickly to resolve issues.)









