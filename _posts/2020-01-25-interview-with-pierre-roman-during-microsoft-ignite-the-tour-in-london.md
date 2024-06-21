---
layout: post
title: "Interview with Pierre Roman during Microsoft Ignite The Tour in London"
date:   2020-01-25 09:45:39 +0100
pin: true
---

Interview with [Pierre Roman](https://developer.microsoft.com/en-us/advocates/pierre-roman), a Senior Cloud Advocate at [Microsoft](https://www.microsoft.com/) during [Microsoft Ignite The Tour in London](https://www.microsoft.com/en-gb/ignite-the-tour/london)

The following video has the complete interview:  

{% include embed/youtube.html id='jSdFG4FgK6w' %}


### Intro

Welcome to community interview episode (3).  
Our community interview is all about Standing on the shoulders of giants! This is a metaphor which means "Using the understanding gained by major thinkers who have gone before in order to make intellectual progress".

So, our giant in this episode is Pierre Roman, who is working as a Senior Cloud Advocate at Microsoft. Pierre Roman has more than 30 years of experience, 15 of them at Microsoft. He is a very specialized IT Pro in Azure and he delivered many amazing sessions and talks all over the globe. A few insights from Pierre's sessions/talks:

![Pierre-Roman](/assets/img/2020/01/Pierre-Roman-2.jpg)

![Pierre-Roman](/assets/img/2020/01/Pierre-Roman-1-1.jpg)

![Pierre-Roman](/assets/img/2020/01/Pierre-Roman-3.jpg)

![Pierre-Roman](/assets/img/2020/01/Pierre-Roman-4-2.jpg)

It was a huge experience for me, it's like I opened 1000s of books and I started extracting the deep experience out of them. This interview is saying a lot but in a little. Here is the interview:

**Mohamed:** Hello everyone, welcome to the community interviews. We are here at Microsoft Ignite The Tour in London and I have here Pierre Roman with me. Hello Pierre! How are you doing?

**Pierre:** How you doing? Hi everyone!

**Mohamed:** It’s great to have you here!

**Pierre:** Thanks! It’s great to be here. Actually as long as there’s no snow I’m happy.

**Mohamed:** So, first, if you can give us an introduction about yourself, what you are doing, and where you are based actually?

**Pierre:** Okay, my name is Pierre Roman. I am Canadian. I’ve been in the IT industry for about 30 years, I’m aging myself a little here, and I’ve done pretty much everything, from the first-level helpdesk to the director of multinational for all IT operations. Now, I work for Microsoft, I’ve been at Microsoft for 15 years and I’m in the DevRel, Developer Relations Group. However, I cover infrastructure operations for cloud and hybrid. So, it’s all of the operations side of cloud computing and hybrid computing that I cover right now as a cloud advocate.

**Mohamed:** That’s fantastic! Can you give us an introduction about your sessions that you are going to present in this event?

**Pierre:** I’ve got three sessions this week. The first this morning was a theatre session, 15 minutes rapid-fire on things you need to keep top of mind when you’re securing your IaaS environment. So, virtual machines, virtual networks, what are the things that you need to think about in terms of securing that environment, it’s not about securing the OS. It’s about securing not only the control plane so, the Azure environments as to who has access to modify the security settings and security controls that you may have put into your environment, securing the VMs themselves, the network, how would you access it because when you’re putting something in the cloud, it’s literally on the Internet, it’s in the cloud. So, there are extra things that you need to think about, but all of the best practices that we’ve all learned on-prem are still absolutely valid. IaaS is an extension of your data center, you have to deal with those machines and those resources the same as you would on-prem.

The second session is going to be the last one today, again another theatre session, which is very quick again rapid-fire, my top Windows 2019 features. So, what I love about them, why I find they’re very important, and where I think they’re going to give the best bang for the buck.

The first session tomorrow is how to integrate and manage your IaaS operations, how to manage it, how to support it, how to patch it, how to secure it, and back it up, and all the stuff that you need to do, but when you’re dealing strictly with an IaaS environment.

**Mohamed:** How do you see the future for this part?

**Pierre:** The future depends on who you’re listening to, it can go multiple different ways. The way I look at it, is for the next decade, we are going to be in a hybrid model. So, companies have a lot of investments on-prem. They’re going to the cloud, the speed at which they’re going to go to the cloud, it depends on the companies themselves, it depends on the regulatory environment, that these companies work in, it depends on the amount of resources that they can throw at migrating to the cloud, or do a little developing new application. Because we’re all stuck with the stuff that nobody wants to deal with, legacy applications that may not work the way you want them in the cloud, that may not be built to support things like elastic scaling. So, if you’ve got applications that don’t support elastic scaling, putting them in the cloud, is just hosting them in another environment. So, now we have to start thinking it’s not just about putting it in the cloud, it’s how do I actually modernize it to be able to start taking advantage of cloud technologies, automatic scaling, and so on. How do I move a SQL box to Azure, do I just run it as a VM, like SQL on a VM, or can I do PaaS services. There are some advantages to going the PaaS services route, in terms of cost, in terms of scaling, in terms of management, because you don’t have to worry about patching the VM itself, you just have to worry about your database, but there are restrictions. For example, you can’t run reporting services in a PaaS environment. So, how do you deal with all that?

You really have to understand where your applications are, how they work together, all of the little integrated details that you’re looking at, to be able to figure out how you’re moving those to the cloud. So, in terms of how I see this going, it’s a hard one, it’s a hard question because there’s no silver bullet, there’s no one answer for everyone, it all depends as to which company you are working with. However, that being said, there are things that people in on-prem administrators and architects that are working with on-prem environments, they can start leveraging some cloud services to help them with stuff that is still on-prem. Azure Monitor, Azure Backup, Azure Site Recovery, all services that can help them manage better the environment, they have on-prem without committing to moving all these workloads to the cloud. So, in the next 10 years, I think we’re going to see a good mix of on-prem and cloud but using cloud services to alleviate some of the business problems that you may have on-prem.

New companies, startups, or companies that are starting from scratch, they don’t have that legacy, they don’t have those workloads that they need to keep the lights on, they’re starting from scratch. So, what’s the point of developing, architecting, and deploying something on-prem when you can from the get-go take advantage of some of those cloud services, and some of those modern applications and modern ways of doing things that make lives a lot easier. That way, you don’t spend all your time fighting fires and keeping lights on, you’re becoming more of a resource for the business as to how to plan going forward.

So, that’s a little bit of what I see in terms of the jobs, because you mentioned before we started recording, what I think as to is it going to steal my job. So, all of you remember, if your only job is rack servers and run cables, if that’s all you do eight hours a day, five days a week, if that’s all you do then, yes maybe the cloud will affect your job. If you’re a system administrator, if you’re maintaining and developing and deploying systems on-prem, your job is not going to go away. If your job involves a collective knowledge of security, compliance, deployment, monitoring, management, all of that is still very very much relevant, even more in a cloud environment because if you get developers or startups that are putting stuff into the cloud without thinking about all those things, all those areas that are super crucial. Especially, like in Europe with GDPR. So, how do you manage the data, how do you manage the backup, how do you manage the disaster recovery, that is still very much relevant and the developer side of the house may not be aware of all that, that is available to them to support their application. So, IT operations is very much alive and well, that’s what will remain.

**Mohamed:** That’s great and people would really like to hear that. So, we can see now that changes are too fast, you know, we don’t have time to learn everything. So, how about adopting that either from individuals or also from the business?

**Pierre:** I understand and I feel ...

**For the rest of the answer and other questions/answers, please watch the
