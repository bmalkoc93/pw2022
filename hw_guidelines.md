---
title: "R Markdown Guidelines"
subtitle: <h4 style="font-style:normal">CRD 298 - Spatial Methods in Community Research</h4>
output: 
  html_document:
    toc: true
    toc_depth: 3
    toc_float: true
    theme: cosmo
---

<h4 style="font-style:normal">Winter 2019</h4>

<style>
h1.title {
  font-weight: bold;
}
</style>

\


Assignments are due approximately every two weeks. They have two components:

1. Executing data analysis tasks - for example, create a map or run a statistical model.
2. Answering conceptual questions - for example, interpret results that were produced from a data analysis task.  

Any response requiring a data analysis task  must be supported by code you generate to produce your result. Just examining your various objects in the “Environment” section of R Studio is insufficient—you must use scripted commands.  You can ask for help from the me and work with other students.  However, you *must* submit your own assignments.


<div style="margin-bottom:25px;">
</div>
## **R Markdown**
\

You will use [R Markdown](https://rmarkdown.rstudio.com/) to write up all R related assignments.  R Markdown is a simple formatting syntax for authoring html, pdf, and Microsoft Word documents in RStudio.  In an R Markdown document, you will write the assignment questions, write the R code that answers each question, and write text that help explain the results.  You then will "run" this document, which executes the R code, shows its output, and formats the document into an html, pdf or Microsoft word document.  For each R related assignment, you will upload onto Canvas an R Markdown document, which has an `.Rmd` extension, and its resulting `.html`, `.pdf`, or `.docx` file. 

To be clear, R is a *programming language*. RStudio is an *application*. R Markdown is a *markup syntax* to convert R script and text into a word, pdf or html document.

In RStudio, install the package **rmarkdown** using the `install.packages()` command.  


```r
install.packages("rmarkdown")
```

<div style="margin-bottom:25px;">
</div>
## **Opening an R Markdown file**
\

A generic R Markdown assignment template can be found [here](https://raw.githubusercontent.com/crd230/data/master/assignment_template.Rmd).  You can use this for every assignment or create your own R Markdown document.  To open a new `.Rmd` file in RStudio, select File -> Open File -> R Markdown. A window like below should pop up.

<center>
![Figure 1: A new R Markdown file](/Users/noli/Documents/UCD/teaching/CRD 230/Lab/crd230.github.io/hwguide0.png)

</center>

For Title, you'll put the Assignment number. For Author, put your first and last name.  Leave the rest alone (we'll get to those options later) and click OK. You should see the R Markdown file pop up on the top left portion of your RStudio interface.

<div style="margin-bottom:25px;">
</div>
##**Authoring an R Markdown document**
\

R Markdown documents contain 3 major components:

1. A YAML header surrounded by ---
2. Chunks of R code surrounded by ```
3. Text mixed with simple text formatting using the [Markdown syntax](https://www.markdownguide.org/cheat-sheet/)


<div style="margin-bottom:25px;">
</div>
###**YAML header**
\

The YAML header controls how R Markdown renders your `.Rmd` file. A YAML header is a section of key: value pairs surrounded by --- marks.  For the assignments, it will generally look like the following.

````
---
title: "Assignment [insert number here]"
subtitle: CRD 298
author: Your full name here
date: Assignment due date
output: 
  html_document:
    theme: cosmo
---
````

When you create a document, the title, subtitle, author and date will be published. We'll get to the output section a little later.

<div style="margin-bottom:25px;">
</div>
###**Text**
\

After you've set the YAML, you start answering the Assignment questions. When answering an assignment question, you'll have the following sequence of components in your R Markdown document: Question text, R code answering the question, and your text to explain the results. Let's say you see this in one of your assignments

````
1+1

1. What does the above code do?
2. What is the result of 2+2?
````
\

You would type in your R Markdown document the following

````
1. What does the above code do?

The code adds 1 + 1

2. What is the result of 2+2?

```{r, warning=FALSE, message = FALSE}
2+2
```

The result of 2+2 is 4.
````

There is nothing special about the text in terms of its format or placement.  However, the R code must be inside an R code chunk. The text "1. What does the above code do?", "The code adds 1 + 1", "2. What is the result of 2+2?" and "The result of 2+2 is 4" are written as normal whereas the R code answering these questions are inside R code chunks.  

<div style="margin-bottom:25px;">
</div>
###**R Code chunks**
\

You present your R code through R code chunks.  R code is inserted in between `` ```{r} `` and `` ``` ``.  For example, to designate `1+1` as R code, it will look like the following in your R Markdown document

````
```{r}
1+1
```
````

Your R code must reside inside an R code chunk in order for it to be processed as R code (otherwise R Markdown will think it is text).  

R will often spit out messages that are not necessary for answering the assignment question.  You should add the options `warning=FALSE` and `message=FALSE` to the R code chunk to hide these unnecessary messages.

````
```{r, warning=FALSE, message = FALSE}
1+1
```
````

You'll need to test code to make sure it is running properly.  Rather than writing all the code and then running it at the end, run them in chunks.  To run code in just one chunk, click on the R code chunk you want to run and either click on ![](/Users/noli/Documents/UCD/teaching/CRD 230/Lab/crd230.github.io/hwguide3.png) and select *Run Current Chunk* or click on ![](/Users/noli/Documents/UCD/teaching/CRD 230/Lab/crd230.github.io/hwguide4.png) located on the right corner of the chunk.  You can also use the keyboard shortcuts described in [Lab 0](https://crd230.github.io/lab0.html#r_scripts).

To elaborate, let's say the first question in an assignment is (1) Add one plus one.  In your R Markdown document, type in the following to answer this question.

````
```{r, warning=FALSE, message = FALSE}
1+1
```
````

Run that code chunk to make sure it works (you should get 2!).  *Then* proceed to the next question.  

Note that you when you run an R code chunk, its output will be embedded within your R Markdown document as shown in Figure 2

<center>
![Figure 2: Output within R Markdown document.](/Users/noli/Documents/UCD/teaching/CRD 230/Lab/crd230.github.io/hwguide1.JPG)

</center>

When you are testing your code, it is better that the code results are shown in your RStudio Console (the bottom left window). To get RStudio to do this, select the "Tools" menu and select "Global Options".  Select "R Markdown" from the left-hand side and deselect the check box "Show output inline for all R Markdown documents". The output from your code should now be shown in the console. 

<center>
![Figure 3: R Markdown options.](/Users/noli/Documents/UCD/teaching/CRD 230/Lab/crd230.github.io/hwguide2.JPG)

</center>



<div style="margin-bottom:25px;">
</div>
## **Knitting an R Markdown document**
\

In addition to the R Markdown file, you will need to submit its knitted result. Knitting puts an assignment's main components - code, output, and text - in a nicely formatted document.  You can create three types of knitted documents: html, Microsoft Word, and a pdf. You specify the type in the New R Markdown window when you first create an R Markdown file. 

<center>
![Figure 4: Selecting the knitted document format.](/Users/noli/Documents/UCD/teaching/CRD 230/Lab/crd230.github.io/hwguide0.png)

</center>

Go back to the YAML example I showed above. *output:* *html_document* tells R to produce an html document.  If you want a word document, *output:* will be *word_document*. A pdf is *pdf_document*.  

My recommendation is to find the document type that suits you and stick with it the rest of the quarter. Some R Markdown features are specific to a certain document, so you should pick one document type to avoid the headache of trying to find out which R Markdown feature goes with which document type.  My experience is that html documents are the easiest to work with.

Note that in order to knit to a pdf, you'll need to install [LaTeX](https://www.latex-project.org/get/).  One way to do this is to install the package **tinytex** in R.  TinyTeX is a lightweight, portable, cross-platform, and easy-to-maintain LaTeX distribution. The R companion package [**tinytex**](https://github.com/yihui/tinytex) can help you automatically install missing LaTeX packages when compiling LaTeX or R Markdown documents to PDF.

To Knit your document click ![](/Users/noli/Documents/UCD/teaching/CRD 230/Lab/crd230.github.io/hwguide6.png).  Note that you can select your document type when knitting by clicking the pull down menu next to ![](/Users/noli/Documents/UCD/teaching/CRD 230/Lab/crd230.github.io/hwguide6.png) and selecting your document choice.  A preview will pop up in a new window and the `.html`, `.pdf`, or `.docx` file will be saved in the folder where your Rmd file resides.  If your R Markdown file has some issues, an error will pop up in the bottom left window of RStudio.  Carefully read the description of the error, which also contains the line number of the offending code.  Go to the line of that offending code and fix the problem.

I recommend not waiting till the very end of an assignment to knit.  When you finish one question, knit your document to see if everything is working properly. If it is working for that question, move on to the next question. There are two things you'll have to deal with: (1) Making sure the R code is working correctly to get the results you need in order to answer the question (2) Making sure the code is working correctly to knit a final document.  These two issues may be related (if your R code is producing an error, R Markdown will not knit), but sometimes they are not.  So, check both your R code and your knitting results often. 

When you're satisfied with the end product, submit your `.Rmd` document and a knitted `.html`, `.docx`, or `.pdf` document on [Canvas](https://login.canvas.ucdavis.edu/). 


<div style="margin-bottom:25px;">
</div>
## **File Management**
\

File management is key to preventing R programming frustration.  Here are a few guidelines to follow in file management when doing the lab guide and homework.

* Set up a clear and understandable hierarchical file system for this class on your hard drive.  For example, create a class folder (CRD 298).  Within that class folder, create two folders, one for Labs and another for Assignments.  Within the Lab folder, create separate folders for each Lab (Lab 1, Lab 2, ...).  Ditto for the Assignments folder.  You might end having a system that looks like the following

<center>
![This is what file organization looks like](/Users/noli/Documents/UCD/teaching/CRD 230/Lab/crd230.github.io/lab1fig1.png)

</center>

* Try to keep all your files that are related to a lab or assignment in one folder.  That is, don't have an Assignment 3 folder that contains data files specific to Assignment 1.  Keep everything in one folder, including the R Markdown for that assignment or lab. 

<div style="margin-bottom:25px;">
</div>
## **Having problems knitting?**


* A major source of error for most new R Markdown users is that they call up a data object in their R Markdown that has not been created within the R Markdown file.  Treat the R Markdown as its own separate system - even if you've created an object through the R Console, and you can see it sitting in your Environment window, R Markdown won't recognize it because it was not created within the R Markdown document.  
* Are you trying to bring in a data file that is not located in the directory your R Markdown is pointed to?  Remember, don't scatter your data files for a lab or assignment across different folders.  Keep them in one folder - the folder where your R Markdown document resides.
* Do you have an `install.packages()` in your R Markdown script? Take it out!  You only need to do it once - and never inside an R Markdown (or a regular R) script.
* Are you using functions for a package that you need to load into R and haven't loaded it in your R Markdown using `library()`. If so, load it in R Markdown!
* If you change a piece of code somewhere in the middle because you caught an error, make sure that change is reflected throughout the code.  For example, let's say you decide to turn an object from an *sp* object to an *sf* object.  There are functions that are specific only to *sp* objects and thus do not work on *sf* objects - so, you'll need to change those functions in the rest of the file.
* As I mentioned above, don't wait till the last minute to knit.  Knit after every question.
* The first place to check when you get a knitting error is the specific line that the error is pointing to.
* Having problem with a line of R code?
    + Did you install the appropriate package?
    + Did you load in the  appropriate library?
    + Are you using the right function?
    + Did you specify all the function's arguments correctly?
* Still having problems?  Break up your code line by line or even argument by argument to find the error? For example, let's say you have 4 lines of code that are connected together - i.e. line 4 depends on line 3, line 3 depends on line 2, and so on


```r
line 1 code
line 2 code
line 3 code
line 4 code
```

If you get an error, run line 1 first.  No error? Run line 1 and 2. No error? Keep going until you find the error.

* If you have a Mac and you are getting an error when knitting, you may need to download the most recent version of XQuartz, which can be downloaded [here](http://xquartz.macosforge.org)
* If you're still stuck, more than likely someone else in this vast world of ours also had a similar problem in the past.  So, ask Google and it might help you out.

<div style="margin-bottom:25px;">
</div>
## **Why R Markdown?**
\

Why R Markdown and not a regular R Script? 

1. This will allow me to link your output (e.g. regression results, maps, tables) to the code producing that output.  In other words, your code **has to work** in order for you to get a result.
2. This promotes transparency and reproducibility.
3. You can intersperse text, images, links, comments, gifs, video and other multimedia files into your code and results, providing a holistic and interwoven framework for data acquisition, cleaning, analysis, presentation, and interpretation.


<div style="margin-bottom:25px;">
</div>
## **Summary**
\

The proper workflow for each assignment will be as follows

1. Create a folder on your hard drive that is specific to the assignment.
2. Download any data needed for the assignment into the assignment folder.
3. Open a new R Markdown file.  Set the proper settings in your YAML.
4. Save the R Markdown file in the assignment folder.
5. In the R Markdown document, answer the first assignment question.
* Most of the questions will ask you to run code.  Show that code in an R Markdown chunk. Bottom line: Any code you used to get a result should be in your assignment.  
  + Make sure your code works.  If it doesn't, then partial to no credit. Run code one chunk at a time to make sure it is working. Note that there are multiple ways to get to an answer in R - **I will not grade on how efficient your code is unless stated so in the question**. 
* Most of the questions will ask you to explain your code/results. Please - *please* - take these interpretation questions seriously.  This is a not a programming or Data Science course - you may have taken 40 hours to produce super elegant code to answer a question, but your results won't be worth much to anyone if you can't properly interpret them. 
5. After you've completed the first question, knit.  You can choose an html, word, or pdf.
6. If you're satisfied with your code and its results for the first question, and the document properly knitted, move on to the next question.
7. Once you've completed all questions and successfully knitted, submit the `.Rmd` and `.html`/`.docx`/`.pdf` files on Canvas **before** the designated due time.
8. Smile, pat yourself on the back, and have some ice cream (I like these [folks](https://threetwinsicecream.com/)).

<div style="margin-bottom:25px;">
</div>
## **Others things to know**


* Please spell-check your assignment before handing it in (Edit -> Check Spelling from the top menu bar).
* In each R chunk, pressing the button ![](/Users/noli/Documents/UCD/teaching/CRD 230/Lab/crd230.github.io/rchunkbutton.png) will run all previous R chunks.
* The default editor settings are to insert matching parentheses and quotes; if you find that this intrudes on your workflow, you can disable it via Tools -> Global Options -> Code then uncheck Insert matching parens/quotes.


<div style="margin-bottom:25px;">
</div>
##**Getting R Markdown Help**
\

Whenever you are editing R Markdown documents in RStudio, you can display an R Markdown cheat sheet by going to Help -> Cheatsheets -> R Markdown Cheat Sheet. A basic introduction to R Markdown can also be found in Chapter 21 in [R for Data Science](http://r4ds.had.co.nz/index.html). 


***


Website created and maintained by [Noli Brazil](https://nbrazil.faculty.ucdavis.edu/)