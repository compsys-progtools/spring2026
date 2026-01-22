---
jupytext:
  text_representation:
    extension: .md
    format_name: myst
    format_version: 0.13
    jupytext_version: 1.16.4
kernelspec:
  display_name: Python 3 (ipykernel)
  language: python
  name: python3
---

# Badge Deadlines and Procedures

This page includes more visual versions of the information on the [grading](grading.md) page.  You should read both, but this one is often more helpful, because some of the processes take a lot of words to explain and make more sense with a diagram for a lot of people.

```{code-cell} ipython3
:tags: [hide-input]

%matplotlib inline
import os
from datetime import date,timedelta
import calendar
import pandas as pd
import numpy as np
import seaborn as sns
# style note: when I wrote this code, it was not all one cell. I merged the cells
# for display on the course website, since Python is not the main outcome of this course
# import constants from cspt
from cspt import CourseDates
import warnings
warnings.simplefilter(action='ignore', category=FutureWarning)

course_dates = CourseDates()

meetings = course_dates.class_meeting_strings

# build a table for the dates
badge_types = ['experience', 'review', 'practice']
target_cols = ['review_target','practice_target']
df_cols = badge_types + target_cols
badge_target_df = pd.DataFrame(index=meetings, data=[['future']*len(df_cols)]*len(meetings),
                                columns=df_cols).reset_index().rename(
                                   columns={'index': 'date'})
# set relative dates
today = date.today()
start_deadline = date.today() - timedelta(7)
complete_deadline = date.today() - timedelta(14)

#  created indexing bools with casting types first, then reuse them throughout below
before_today = pd.to_datetime(badge_target_df['date']) <=pd.to_datetime(today)
before_start = pd.to_datetime(badge_target_df['date']) <=pd.to_datetime(start_deadline)
before_complete = pd.to_datetime(badge_target_df['date']) <=pd.to_datetime(complete_deadline)
before_penalty = pd.to_datetime(badge_target_df['date']) <=pd.to_datetime(course_dates.penalty_free_end)
# mark eligible experience badges
# mark targets, cascading from most recent to oldest to not have to check < and >
badge_target_df['experience'][before_today] = 'eligible'
badge_target_df['review_target'][before_today] = 'active'
badge_target_df['practice_target'][before_today] = 'active'
badge_target_df['review_target'][before_start] = 'started'
badge_target_df['practice_target'][before_start] = 'started'
badge_target_df['review_target'][before_complete] = 'completed'
badge_target_df['practice_target'][before_complete] = 'completed'
# mark enforced deadlines
badge_target_df['review'][before_today] = 'active'
badge_target_df['practice'][before_today] = 'active'
badge_target_df['review'][before_start] = 'started'
badge_target_df['practice'][before_start] = 'started'
badge_target_df['review'][before_complete] = 'completed'
badge_target_df['practice'][before_complete] = 'completed'
badge_target_df['review'][before_penalty] = 'penalty free'
badge_target_df['practice'][before_penalty] = 'penalty free'

# convert to numbers and set dates as index for heatmap compatibility
status_numbers_hm = {status:i+1 for i,status in enumerate(['future','eligible','active','penalty free','started','completed'])}
badge_target_df_hm = badge_target_df.replace(status_numbers_hm).set_index('date')

# set column names to shorter ones to fit better
badge_target_df_hm = badge_target_df_hm.rename(columns={'review':'review(e)','practice':'practice(e)',
                                                       'review_target':'review(t)','practice_target':'practice(t)',})
# build a custom color bar 
n_statuses = len(status_numbers_hm.keys())
manual_palette = [sns.color_palette("pastel", 10)[7],
                 sns.color_palette("colorblind", 10)[2],
                 sns.color_palette("muted", 10)[2],
                 sns.color_palette("colorblind", 10)[9],
                 sns.color_palette("colorblind", 10)[8],
                 sns.color_palette("colorblind", 10)[3]]
# generate the figure, with the colorbar and spacing
ax = sns.heatmap(badge_target_df_hm,cmap=manual_palette,linewidths=1)
# mote titles from bottom tot op
ax.xaxis.tick_top()
# pull the colorbar object for handling
colorbar = ax.collections[0].colorbar 
# fix the location fo the labels on the colorbar
r = colorbar.vmax - colorbar.vmin 
colorbar.set_ticks([colorbar.vmin + r / n_statuses * (0.5 + i) for i in range(n_statuses)])
colorbar.set_ticklabels(list(status_numbers_hm.keys()))
# add a title
today_string = today.isoformat()
ax.set_title('Badge Status as of '+ today_string); 
```

<!-- **November 5 above will actually be on November 6**  -->

## Getting Feedback 

Who should you request/assign?


```{list-table}
:label: PRreviewers

* - course item type
  - issue asignee
  - PR reviewer
* - prepare work
  - assignment not required; can be student
  - none requierd; merge to experience branch
* - experience badge
  - N/A
  - TA asigned to your group (will be automatic after a few classes)
* - practice badge
  - assignment not required; can be student
  - `@instuctors` (will then convert to 1 person)
* - review badge
  - assignment not required; can be student
  - `@instuctors` (will then convert to 1 person)
* - explore badge
  - proposal, assigned to `@brownsarahm` (also student optionally)
  - `@brownsarahm`
* - build badge
  - proposal, assigned to `@brownsarahm` (also student optionally)
  - `@brownsarahm`
* - anything merged pre-emptively in penalty free
  -  N/A
  - `@brownsarahm` & clear other assignees
```

(badges:deadlines)=
## Deadlines 

<!-- Deadlines are flexible in this course so that you can balance your workload across other courses, and instead the **feedback** schedule is fixed.  Weekly feedback hours will be announced and posted. 

However, leaving all of the work to the end of the semester is not good for you to achieve your goals or for me to manage my time giving feedback.   -->

<!-- There will be fixed feedback hours each week, if your work is submitted by the start of that time it will get feedback.  If not, it will go to the next feedback hours.  -->


We do not have a final exam, but URI assigns an exam time for every class.  The date of that assigned exam will be the final due date for all work including all revisions. 

[experience](#badges:deadlines:experience), [review, and practice](badges:deadlines:rp) badges have general deadlines. [Explore](#badges:deadlines:explore) and [build](#badges:deadlines:build) deadlines are based on when you propose and you can propose your own. 

(badges:deadlines:experience)=
### Experience badges

Prepare work tasks must be done before class so that you are prepared.  Missing a prepare task could require you to do an experience report to make up what you were not able to do in class.

If you miss class, the experience report should be at least attempted/drafted (though you may not get feedback/confirmation) before the next class that you attend. This is strict, not as punishment, but to ensure that you are able to participate in the next class that you attend. Skipping the experience report for a missed class, may result in needing to do an experience report for the next class you attend to make up what you were not able to complete due to the missing class activities.  

If you miss multiple classes, create a catch-up plan to get back on track by contacting instructor either with an issue or email. 

(badges:deadlines:rp)=
### Review and Practice Badges 

These badges have 5 stages: 
- posted: tasks are on the course website([review](activities/review) and [practice](activities/practice)) and an {term}`issue` is created
- started: one task is attempted and a draft PR is open 
- completed: all tasks are attempted {term}`PR <pull request>` is ready for review, and a review is requested
- earned: PR is approved (by instructor or a TA) and work is merged


These badges badges must be *started* within one week of when they are posted  and *completed* within two weeks. A task is attempted when you have answered the questions or submitted evidence of doing an activity or asked a sincere clarifying question.

```{tip}
these badges should *ideally* be started before the next class. This will set you up to make the most out of each class session. However, only prepare for class tasks *must* be done immediately. 
```


If a badge is planned, but not started within one week it will become expired and ineligble to be earned. You may request extensions to complete a badge by updating the PR message, these will typically be granted. Extensions for starting badges will only be granted in exceptional circumstances.  

Expired badges will receive a comment and be closed

Once you have a good-faith attempt at a complete badge, you have until the end of the semester to finish the revisions in order to *earn* the badge. 

```{tip}
Try to complete revisions quickly, it will be easier for you
```

(badges:deadlines:explore)=
### Explore Badges 

Explore badges are feedback-limited. You will not get feedback on subsequent explore badge proposals until you earn the first one. 

Explore badges have 5 stages:
- proposed: issue created 
- in progress: issue is labeled "proceed" by the instructor
- complete: work is complete, PR created, review requested
- revision: "request changes" review was given
- earned: PR approved

 Once you have one earned, then you can have up to two in progress and two in revision at any given time. At most, you will receive feedback for one explore badge per week, so in order to earn six, your first one must start your first one early enough. 

(badges:deadlines:build)=
### Build Badges 

At most one build badge will be evaluated every 4 weeks.  This means that if you want to earn 3 build badges, the first one must be in 8 weeks before the end of the semester.
 <!-- The second would be due April 1st, and the third submitted by the end of classes, April 29th.  -->

<!-- ### Notes


- Keep your deeper explorations and more practice task content in your KWL chart repository.
- Link approved PRs to your grading contract for record keeping.

### Grading Contract Instructions

```{important}
this includes minor corrections relative to the readme in the template provided
``` 
-->

## Procedures

(badges:procedure:experience)=
### Prepare work and Experience Badges Process


This is for a single example with specific dates, but it is similar for all future dates

The columns (and purple boxes) correspond to branches in your KWL repo and the yellow boxes are the things that you have to do. The "critical" box is what you have to wait for us on. The arrows represent PRs (or a local merge for the first one)

::::{margin}
:::{warning}
the diagrams do not look great in dark mode, use light mode for them
:::
::::::


```{mermaid}
sequenceDiagram
    participant P as prepare Jan 28
    participant E as experience Jan 28
    participant M as main 
    note over P: complete prepare work<br/> between feb Jan 23 and Jan 28
    note over E: run experience badge workflow <br/> at the end of class Jan 28
    P ->> E: local merge or PR you that <br/> does not need approval
    note over E: fill in experience reflection 
    critical Badge review by instructor or TA
        E ->> M: Experience badge PR
    option if edits requested
        note over E: make requested edits
    option when approved 
        note over M: merge badge PR
    end
```



In the end the commit sequence for this will look like the following:


```{mermaid}
gitGraph
   commit
   commit
   checkout main
   branch prepare-2025-01-28
   checkout prepare-2025-01-28
   commit id: "gitunderstanding.md"
   checkout main
   branch experience-2025-01-28
   checkout experience-2025-01-28
   commit id: "initexp"
   merge prepare-2025-01-28
   commit id: "fillinexp"
   commit id: "revisions" tag:"approved"
   checkout main
   merge experience-2025-01-28
```

You can merge the prepare into the experience with a PR or on the command line, your choice. 

Where the "approved" tag represents and approving reivew on the PR. 


You can, once you know how, do this offline and do the merge with in the CLI instead of with a PR.

+++


(badges:procedure:rp)=
### Review and Practice Badge 


Legend:
```{mermaid}
flowchart TD
    badgestatus[[Badge Status]]
    passive[/ something that has to occur<br/> not done by student /]      
    student[Something for you to do]

    style badgestatus fill:#2cf

    decisionnode{Decision/if}
      sta[action a]
      stb[action b]
      decisionnode --> |condition a|sta
      decisionnode --> |condition b|stb
    subgraph phase[Phase]
      st[step in phase]
    end
```

::::{margin}
:::{warning}
the diagrams do not look great in dark mode, use light mode for them
:::
::::::


This is the general process for review and practice badges 

```{mermaid}
flowchart TD
%%    subgraph work[Steps to complete]
    subgraph posting[instructor will post the Badge]
      direction TB
      write[/instructor finalizes tasks after class/]
      post[/instructor pushes to github/]
      link[/notes are posted  with badge steps /]
      posted[[Posted: on badge date]]
      write -->post
      post -->link
      post --o posted
    end
    subgraph planning[Plan the badge]
      direction TB
      create[/instructor runs your workflow/]
      decide{Do you need this badge?}
      close[close the issue]
      branch[create branch]
      create -->decide
      decide -->|no| close
      decide -->|yes| branch
    end
    subgraph work[Work on the badge]
      direction TB
      start[do one task]
      commit[commit work to the branch]
      moretasks[complete the other tasks]
      ccommit[commit them to the branch]
      reqreview[request a review]
      started[[Started <br/> due within one week <br/> of posted date]]
      completed[[Completed <br/>due  within two weeks <br/> of posted date]]
      wait[/wait for feedback/]
      start --> commit
      commit -->moretasks
      commit --o started
      moretasks -->ccommit
      ccommit -->reqreview
      reqreview --> wait
      reqreview --o completed
    end
    subgraph review[Revise your completed badges]
      direction TB
      prreview[Read review feedback]
      approvedq{what type of review}
      merge[Merge the PR]
      edit[complete requested edits]
      earned[[Earned <br/> due by final grading]]
      discuss[reply to comments]
      prreview -->approvedq
      approvedq -->|changes requested|edit
      edit -->|last date to edit: May 1| prreview
      approvedq -->|comment|discuss
      discuss -->prreview
      approvedq -->|approved|merge
      merge --o earned
    end

    posting ==> planning
    planning ==> work
    work ==> review

%% styling 
style earned fill:#2cf
style completed fill:#2cf
style started fill:#2cf
style posted fill:#2cf
style planned fill:#2cf
```

(badges:procedure:explore)=
### Explore Badges


```{mermaid}
flowchart TD
    subgraph proposal[Propose the Topic and Product]
      issue[create an issue]
      proposed[[Proposed]]
      reqproposalreview[Assign it to instructor]
      waitp[/wait for feedback/]
      proceedcheck{Did instructor apply a proceed label?}
      branch[start a branch]
      progress[[In Progress ]]
      iterate[reply to comments and revise]
      issue --> reqproposalreview
      reqproposalreview --> waitp
      reqproposalreview --> proposed
      waitp --> proceedcheck
      proceedcheck -->|no| iterate
      proceedcheck -->|yes| branch
      branch --> progress
      iterate -->waitp
    end
    subgraph work[Work on the badge]
      direction TB
      moretasks[complete the work]
      ccommit[commit work to the branch]
      reqreview[request a review]
      wait[/wait for feedback/]
      complete[[Complete]]
      moretasks -->ccommit
      ccommit -->reqreview
      reqreview --o complete
      reqreview --> wait
    end
    subgraph review[Revise your work]
      direction TB
      prreview[Read review feedback]
      approvedq{what type of review}
      revision[[In revision]]
      merge[Merge the PR]
      edit[complete requested edits]
      earned[[Earned <br/> due by final grading]]
      prreview -->approvedq
      approvedq -->|changes requested|edit
      edit --> prreview
      edit --o revision
      approvedq -->|approved| merge
      merge --o earned
    end

    proposal ==> work
    work ==> review

%% styling 
style proposed fill:#2cf
style progress fill:#2cf
style complete fill:#2cf
style revision fill:#2cf
style earned fill:#2cf

```

(badges:procedure:builld)=
### Build Badges 


```{mermaid}
flowchart TD
    subgraph proposal[Propose the Topic and Product]
      issue[create an issue]
      proposed[[Proposed]]
      reqproposalreview[Assign it ]
      waitp[/wait for feedback/]
      proceedcheck{Did instructor apply a proceed label?}
      branch[start a branch]
      progress[[In Progress ]]
      iterate[reply to comments and revise]
      issue --> reqproposalreview
      reqproposalreview --> waitp
      reqproposalreview --> proposed
      waitp --> proceedcheck
      proceedcheck -->|no| iterate
      proceedcheck -->|yes| branch
      branch --> progress
      iterate -->waitp
    end
    subgraph work[Work on the badge]
      direction TB
      commit[commit work to the branch]
      moretasks[complete the work]
      draftpr[Open a draft PR and <br/> request a review]
      ccommit[incorporate feedback]
      reqreview[request a review]
      wait[/wait for feedback/]
      complete[[Complete]]
      commit -->moretasks
      commit -->draftpr
      draftpr -->ccommit
      moretasks -->reqreview
      ccommit -->reqreview
      reqreview --> complete
      reqreview --> wait
    end
    subgraph review[Revise your work]
      direction TB
      prreview[Read review feedback]
      approvedq{what type of review}
      revision[[In revision]]
      merge[Merge the PR]
      edit[complete requested edits]
      earned[[Earned <br/> due by final grading]]
      prreview -->approvedq
      approvedq -->|changes requested|edit
      edit --> prreview
      edit -->revision
      approvedq -->|approved| merge
      merge --o earned
    end

    proposal ==> work
    work ==> review

%% styling 
style proposed fill:#2cf
style progress fill:#2cf
style complete fill:#2cf
style revision fill:#2cf
style earned fill:#2cf

```

(badges:process:community)=
### Community Badges

You can log them either [manually](badges:process:community:manual)  or with help of an [action](#badges:process:community:logger)  that a past student contributed!  It always ends up with a PR that must be reviewed by `@brownsarahm`

(badges:process:community:logger)=
#### Logger Action

Your KWL repo has an action called "Community & Explore Badge Logger" that will help you. 

Find that on the left hand list on the Actions tab of your repository. 

````{margin}
````{note}
You, too could contribute code that helps automate things in class or organize things
```
````
(badges:process:community:manual)=
#### Manual logging
These are the instructions from your `community_contributions.md` file in your KWL repo: 
For each one: 
- In the `community_contributions.md`` file on your kwl repo, add an item in a bulleted list (start the line with - )
- Include a link to your contribution like `[text to display](url/of/contribution)`
- create an individual {term}`pull request` titled "Community-shortname" where `shortname` is a short name for what you did. approval on this PR by instructor will constitute credit for your grade
- request a review on that PR from `@brownsarahm`

```{important}
You want one contribution per {term}`PR`` for tracking
```

```{mermaid}
flowchart TD
    contribute[Make a contribution <br> *typically not in your KWL*]
    link[Add a link to your <br> contribution to your<br> communiyt_contribution.md<br> in your KWL repo]
    pr[create a PR for that link]
    rev[request a review <br> from `@brownsarahm`]
    contribute --> link
    link --> pr --> rev
    rev --> approved[Instructor] --> merge[Merge the PR]
    merge --o earned

```

