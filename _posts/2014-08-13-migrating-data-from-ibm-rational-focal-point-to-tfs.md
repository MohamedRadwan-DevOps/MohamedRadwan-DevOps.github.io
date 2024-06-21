---
layout: post
title: "Migrating data from IBM Rational Focal Point to TFS"
date: 2014-08-13 15:13:00 +0100
---

![FocalPoint](/assets/img/2014/08/focalpoint.jpg)

I had an assignment that needed to migrate defects (bugs) from [**IBM Rational Focal Point**](http://pic.dhe.ibm.com/infocenter/rfphelp/v6r5/index.jsp?topic=%2Fcom.ibm.rational.fp.help.doc%2Ftopics%2Fc_focal_point_overview.html "Rational Focal Point overview") to [**TFS (Team Foundation Server)**](http://msdn.microsoft.com/en-us/vstudio/ff637362.aspx "Team Foundation Server"). The data for the defects was as follows:

- 13000 defects
- 9000 attachments (4 GB size)

I used the API for both, Focal Point and TFS, to develop a migration tool... for more information about these APIs, see the following links:

- [Integrating with Rational Focal Point by using web services](http://pic.dhe.ibm.com/infocenter/rfphelp/v6r5/index.jsp?topic=%2Fcom.ibm.rational.fp.help.doc%2Ftopics%2Fc_web_services.html "Integrating with Rational Focal Point by using web services")
- [Extending Work Item Tracking by Using the Client Object Model for Team Foundation](http://msdn.microsoft.com/en-us/library/bb130347.aspx "Extending Work Item Tracking by Using the Client Object Model for Team Foundation")

Here are some considerations for anyone who may have a similar situation:

- Reading and getting the defects from Focal Point takes time, especially with the attachments. Also, saving a work item with attachments takes time, so running the migration after finishing the tool took up to 5 hours.
- Using the API method of getElements crashed by throwing an out-of-memory exception for the client running the migration tool, so we needed to get 100 in each round.
- Everything is structured by Alias inside Focal Point, and you need to get the Alias of Work-space -> Modules -> Elements -> Fields.
- Log all the transactions so if any exception is thrown during the migration, you could know where you stopped and where you will need to continue.
- Handle the exceptions very well as you don’t want to restart the process if any exception is thrown.
- As the process takes time, try to get a status on what happens by printing out on the console what you read and what you save.
