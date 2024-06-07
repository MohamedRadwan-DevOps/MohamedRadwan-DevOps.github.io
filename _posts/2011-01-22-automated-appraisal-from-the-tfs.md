---
layout: post
title: "Automated appraisal from the TFS"
date:   2011-01-22 23:53:27 +0100
---

From a few days ago my manager request me to create appraisal for my
team, this appraisal has many factors like code quality, quantity of the
tasks, and many other factors. So as you may already know in my world of
automation we can automate anything and since all our work recorded on
the TFS so I can extract this report from the TFS with button click. I
just enter the following, date from, date to and then boom the report
is created, so this report can be more accurate, created in no time and
has no subjective or biased . so I create the following appraisal report
as a baseline, I know it will not be mature enough at the time being
but with running the experimental and your feedback it will be enhanced.
This report values should change from one to another , from my opinion
all people have most of the skill set needed but with different
distribution from one to another, so this report will show what the
main advantage and skills of a person and what are the other skills that
need to improve? it will also show where you can put this person, in
other word it will show the best place for this person and what is the
hidden output of each one.

[![Apprisal](assets/img/2011/01/Apprisal-1024x552.png)](assets/img/2011/01/Apprisal.png)

So let\'s talk about each factor and what does it mean? and how does it
calculated?

-   Completed Task

The number of completed tasks, this factor show the planning skills
because the more task you will have the more planning effort you will
spend, for example if there is one feature that has 10 story point size,
divided by someone to 2 tasks and another person divide it to 10 tasks
so the second person is spending more effort in planning activity.

-   Completed features

The number of resolved or closed feature, this is the main productivity
factor, it show how the productivity of the person, remember the feature
has size for example there is a feature with 10 story point and there is
a feature with 30 story point, so we can calculate this factor based on
the number of feature times the story points, remember if the QC team
reopen the feature it will not considered until resolved latter

-   Effort

The number of actual hours spend in the tasks , for my opinion this
factor has a contrast relation with the communication time and holding
meetings, for example if the communication increased (there are many
meetings every day) the effort will be reduced and vise versa

-   Reported issues

The number of reported issues, any issue of the system, the process or
anything that could delay the smoothing or the streamlining of the
work, this factor show the positive attitude of the person for pointing
to problems.

-   Resolved issues

The number of resolved issues, this factor will show the positive
attitude of the person to solve problems, remember some people are
problem finders and others are problem resolvers

-   Reported enhancement

The number of requested enhancement, this factor will show the positive
attitude of the person to enhance the defects of architecture, design,
code or anything that not created very well, he can smell the code or
the debts because this is not an issue the system work but with debts,
it\'s like Technical debt or Code smell, for more information about
Technical debt, see

[link1](http://c2.com/cgi/wiki?TechnicalDebt "Tech debt"),

[link2](http://en.wikipedia.org/wiki/Technical_debt "Tech debt"), for more information about code smell 

[see this link](http://en.wikipedia.org/wiki/Code_smell "Code smell") This factor
also will show the degree of the initiative of the person for introducing initiatives to the project, the team and the company

-   Resolved enhancement

The number of resolved enhancement, this factor show the positive
attitude of the person for paying our debts

-   Code churn

This factor indicate the quality and maturity of the following, the
code, the project, the module and so on because it\'s the number of the
change of the code from change-set or revision to another, for example
suppose there are 3 bugs on the system and to fix these bugs you create
500 code churn, in another application or person you only create 5
code churn, so the second case indicate that the application is well
design and coded and the person that fix these bugs write a quality
code. for information about what is code churn, [see this link](http://blogs.msdn.com/b/askburton/archive/2004/09/09/227515.aspx?ocid=soc-n-eg-elite--MRadwan "Code churn")
, or see the IEEE paper for this

[link](http://ieeexplore.ieee.org/xpl/freeabs_all.jsp?arnumber=738486 "Code churn IEEE")

-   Produced bugs

This is the number of bugs that the person produced, and since we
develop by feature and we assign the developer the features so the
easiest way to know who caused the bug is to assign the bug to the one
that resolve the feature, this number can be calculated based on the
number of bugs times the severity of the bug.

-   Resolved bugs

The number of resolved bugs and consider that the developer may resolve
bugs for other developer.

-   Estimation accuracy

This is very important factor, it will be calculated based on the number
of tasks, the estimation effort and the actual effort, the problem
always not the long or the short time estimation, the problem is the
accurate of the estimation because the plan consist of many task WBS
(Work breakdown structure) so if the project has 1000 tasks and each
task only delayed 1 hour this mean you may delay the project by 1000
hours (if them on the critical path?) which mean about 5 months, so we
have to focus on accurate estimation rather than fast with no accuracy

-   Attendance degree

Of curse this information not exist on the TFS but we have a system that
has this information we can extract this info to produced calculation
based on the following , the number of business days, the number of
vacation or late for example if we said from 1/1/2011 to 1/2/2011 there
are 22 business days so every late or vacation consider as minus 1 so
for 2 late and 1 day vacation it will has minus 3 so the percentage
could be as the following 19/22 % = 86% What we need to make this report
effective and realistic?

-   All requirement and features must be exist on the TFS with the
    description, prototype and the [support
    ]{style="text-decoration: underline;"}needed for the developer so he
    can start the development.
-   All requirements should size estimated (Story points) from the
    developers team only.
-   Any iteration should be well planned and well break down by the
    developers with well estimation for the time of the tasks (Effort
    needed)
-   No task assign to anyone out of the TFS
-   No task or activity created out of the TFS (Every activity should
    made through the TFS to capture time, effort, cost, etc)

At the end, this report will not be the only depenendent, we have to not
forget the other factors like the project factors itself, for example we
need to see all fators of the project and what is the effect of removing
or assigning a resource to the project, for example the project maybe
deliver faster by adding some resource to the project but with low
qulity and stability. What we will get from doing this? we will have
historical data that can be used for estimation and analysis purpose, I
can well identify the skills of my team, when and where I will use them,
I will know how to fast a project? how to enhance the quality? or how
to balance between them. I hope to see your feedback to enhance this
report. 

Thanks

