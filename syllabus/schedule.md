---
jupytext:
  formats: ipynb,md:myst
  text_representation:
    extension: .md
    format_name: myst
    format_version: 0.13
    jupytext_version: 1.15.1
kernelspec:
  display_name: Python 3 (ipykernel)
  language: python
  name: python3
---

# Schedule

![](#location)

## Overview

The following is a tentative outline of topics in an order, these things will be filled into the concrete schedule above  as we go.  These are, in most cases bigger questions than we can tackle in one class, but will give the general idea of how the class will go.  

<!-- This plan accounts for 1 less week than we actually have.  We will either go over somewhere or we'll use the last week for sharing projects, reflection, or an additional topics that comes up during the semester. -->

### How does this class work?

*~ one week*

We will start by introducing some basics of GitHub and setting expectations for how the course will work. This will include how you are expected to learn in this class which requires a bit about how knowledge production in computer science works and getting started with the programming tools.  

<!-- ### How do all of these topics relate?

*approximately two weeks*

````{margin}
```{tip}
We will integrate history throughout the whole course.  Connecting ideas to
one another, and especially in a sort of narrative form can help improve retention of ideas. My goal is for you to learn.  

We'll also come back to different topics multiple times with a slightly different framing each time.  This will both connect ideas, give you chance to practice recalling (more recall practice improves long term retention of things you learn), and give you a chance to learn things in different ways.
```
````

We'll spend a few classes doing an overview where we go through each topic in a little more depth than an introduction, but not as deep as the rest of the semester. In this section, we will focus on how the different things we will see later all relate to one another more than a deep understanding of each one.  At the end of this unit, we'll work on your grading contracts.

We'll also learn more key points in history of computing to help tie concepts together in a narrative.


Topics:
- bash
- man pages (built in help)
- terminal text editor
- git
- survey of hardware
- compilation
- information vs data -->

(sectools)=
### What tools do Computer Scientists use?



Next we'll focus in on tools we use as computer scientists to do our work.  We will use this as a way to motivate how different aspects of a computer work in greater detail. While studying the tools and how they work, we will get to see how some common abstractions are re-used throughout the fields and it gives a window and good motivation to begin considering how the computer actually works.     

Topics:
- bash
- linux
- git
- i/o
- ssh and ssh keys
- number systems
- file systems


### What Happens When I run code?


Finally, we'll go in really deep on the compilation and running of code. In this part, we will work from the compilation through to assembly down to hardware and then into machine representation of data.   

Topics:
- software system and Abstraction
- programming languages
- cache and memory
- compiliation
- linking
- basic hardware components

(timemangement)=
## Recommended workload distribution

To plan your time, I recommend expecting the following:
- 30 minutes, twice per week for prepare work (typically not this much). 
- 1.5(review)-3(practice) hours, twice per week for the dated badges (including revisions). 



For each explore : 
- 30 min for proposal
- 7 hours for the project

For each build: 
- 1.5 hour for the proposal (including revisions)
- 22 hours for the project
- 30 min for the final reflection


````{margin}
```{note}
the first explore or build will probably take longer than this because there will be more revisions, but the later ones will likely take less than this.

You do **not** have to do both build and explore see [grading page](#badgecounts) for details. 
```
````


This is a four credit course, meaning we have approximately 4 hours of class + lab time per week($75 \times 2+105 = 255$ minutes or 4.25 hours). By the [accredidation standards](https://www.neche.org/wp-content/uploads/2018/12/Pp111_Policy_On_Credits-And-Degrees.pdf), students should spend a minimum of 2 hours per credit of work outside of class over 14 weeks.  For a 4 credit class, then, the expected minimum number of hours of work outside of class you should be spending is 112 hours(2 * 4 * 14). With these calculations, given that there are 26 class sessions and only 18 review or practice are required, it is possible to earn an A with approximately 112 hours of work outside of class and lab time.  

## Tentative Timeline

```{warning}
This section is not yet updated for Fall 2025. 

This is a rough example. 
```

This is the planned schedule, but is subject to change in order to adapt to how things go in class or additional questions that come up. 

::::::::{csv-table} Schedule
:label: classschedule
:header: date,keyword,conceptual,practical,social,activity
2025-09-04,intro,"what is a system,why study tools",GitHub basics,class intros,"create kwl repo in github, navigate github.com basics"
2025-09-09,logistics,github flow with issues,syllabus,working together and building common vocab,"set up to work offline together, create a folder"
2025-09-11,terminal start,"git structure,paths and file system","bash path navigation,git terminal authentication",why developers work differently than casual users,navigate files and clone a repo locally
2025-09-16,gitoffline,git branches,"github flow offline,resolving merge conflicts","communication is important,git can help fix misunderstandings and save effort","make a branch locally,create and fix merge conflicts"
2025-09-18,why terminal,"computing mental model,paths and file structure","bash navigation,tab completion","collaboration requires shared language,shared convention and standards help get people up to speed faster",work with bash and recover from a mistake with git
2025-09-23,commit,"what a commit is,what the parts of a commit are",git plumbing commands,"commits are signed,commit messages are for people",inspect a commit in detail
2025-09-25,documentation,"build,automation,modularity,pattern matching,","generate documentation with jupyterbook,gitignore,git init,git remote","main vs master,documentation community",make a jupyterbook
2025-09-30,unix philosophy,"unix philosophy,debugging strategies","decision making for branches,review cspt","social advantages of shared mental model,different target users impact on design",discussion with minor code examples
2025-10-02,git structure,"what is a file system,how does git keep track of versions","find in bash,seeing git config,plumbing/porcelain commands","git workflows are conventions,git can be used different ways for different types of teams,two sets of ""rules""",examine git from multiple definitions and inspect objects
2025-10-07,git internals,"pointers,design and abstraction,intermediate stages in git,what is the staging area","inspecting git objects,when hashes are unique or the same",conventions vs requirements,create a commit using plumbing commands
2025-10-09,git references,"pointers,git branches and tags","git branches, advanced fixing,semver and conventional commits,git tags,code releases","advantages of data that is both human and machine readable,social disadvantages of computational efficiency",make a tag and release
2025-10-14,numbers,"hashes,number systems","git commit numbers,manual hashing with git",number  systems are derived in culture,discussion and use hashing algorithm
2025-10-16,bash scripting,"bash is a programming language,official docs,scripting/interactive","script files,man pages,bash variables,bash loops,bash conditionals,gh CLI",using automation to make collaboration easier,build a bash script that calculates a grade
2025-10-21,IDE,IDE parts,compare and contrast IDEs,"collaboraiton features,developer communities",discussions and sharing IDE tips
2025-10-23,server use,"ssh keys,hpc system strucutre","ssh keys,interactive,slurm",social aspects of passwords and security,configure and use ssh keys on a hpc
2025-10-28,building,building C code,"ssh keys,gcc compiler","file extensions are for people,when vocabulary is imprecise",build code in C and examine intermediate outputs
2025-10-30,hardwar,von neuman architecture,reading a basic assembly language,historical context of computer architecures,use a hardware simulator to see step by step of a simple program
2025-11-04,floats,float representation,floats do not equal themselves,"social processes around standard developents,standards are for people",work with float representation through fractions in Python
2025-11-06,bitwise operation,"what is a bit,what is a register,how to break larger calculations down",how an ALU works,tech interviews look for obscure details sometimes,derive addition from basic logic operations
2025-11-13,architecture,"physical gates,history",interpretting specs,social context influences technology,discussion
2025-11-18,timing,"timing,control unit,threading",threaded program with a race condition,different times matter in different cases,write a threaded program and fix a race condition
2025-11-20,memory,"different type of memory,different abstractions",working with large data,privacy/respect for data,large data that has to be read in batches
2025-11-25,abstraction,"general abstraction,design patterns",general techniques for understanding new systems in CS,shared abstractions help us collaborate,"find examples of abstraction,stress test abstractions"
2025-11-27,programming languages,"types of PLs,what is PL studying",choosing a language for a project,usability depends on prior experience,discussion or independent research
2025-12-02,review,all,end of semester logistics,group work final,"review quiz,integration/reflection questions"
2025-12-04,,,,,

::::::::






## Tentative Lab schedule



::::::::{csv-table} Lab Schedule
:label: labschedule
:header: date,title
2025-09-08,Setup and Syllabus Quiz
2025-09-15,progress and reflection
2025-09-22,wrapping up
2025-09-29,Misconception-Busting
2025-10-06,vocab and processes
2025-10-20,Branches
2025-10-27,Plan for Success & Working with files
2025-11-03,"Install, reflection, and co-working"
2025-11-10,Planning for Explore and Builds
2025-11-17,git plumbing
2025-11-24,reflection
2025-12-01,scripts
2025-12-08,floats
::::::::