---
layout: post
title: "Configure TFS 2010 Alert using Local SMTP that use Gmail account"
date:   2011-06-26 16:34:10 +0100
---

When I start the task of configuring TFS Alert I found very good article
on how to configure this alert using the Gmail, see the following link
[http://elbruno.com/2011/04/25/tfs2010-howto-configure-an-smtp-service-to-send-mails-using-a-gmail-account/](http://elbruno.com/2011/04/25/tfs2010-howto-configure-an-smtp-service-to-send-mails-using-a-gmail-account/ "TFS Alert ")

Thanks Albruno for this post Any way when I start test the example all I
need to do just stop and start the SMTP server from IIS 6.0 Manager and
the e-mails will be sent, I also decide to decrease all the time for the
retry time which is the first one is 15 minutes to be 5 minutes and so
on You can also test the email using Telnet for more information google
how to send email using telnet Don\'t forget to change the service to be
automated start for **Simple Mail Transfer Protocol service** We will
also configure the alert in the MOSS 2010 as the following:

### Configure outgoing e-mail for a farm by using Central Administration in MOSS 2010

1.  In Central Administration, click **System Settings**.
2.  On the System Settings page, in the **E-Mail and Text Messages
    (SMS)** section, click **Configure outgoing e-mail settings**.
3.  On the Outgoing E-Mail Settings page, in the **Mail Settings**
    section, type the SMTP server name for outgoing e-mail (for example,
    mail.example.com) in the **Outbound SMTP server** box.
4.  In the **From address** box, type the e-mail address as you want it
    to be displayed to e-mail recipients.
5.  In the **Reply-to address** box, type the e-mail address to which
    you want e-mail recipients to reply.
6.  In the **Character set** list, select the character set that is
    appropriate for your language.
7.  Click **OK**.


