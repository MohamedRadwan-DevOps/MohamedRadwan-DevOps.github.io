---
layout: post
title: "New enhancement in MTM 11 Preview"
date:   2012-02-29 12:04:07 +0100
---

There are very good enhancements in [MTM (Microsoft Test Manager) 11 Preview](https://mohamedradwan.com/category/tfs-11-beta/ "TFS 11 Beta"), I will describe 3 of them:

- Change the screenshot annotation tool
- Audio Recording
- Exploratory testing without test cases

### Change the screenshot annotation tool

Now when you take a screen capture while using the test runner (TR), this capture will be opened by default in Microsoft Paint for editing. Any modifications made will be saved to the attachment itself (WOW). Not only this, but we can also change the default editing tool to our favorite tool. I use SnagIt, so I changed the screenshot editing tool to SnagIt. Open MTM 11 Preview:

![MTM 11 Preview](https://public.bay.livefilestore.com/y1pKuz3Y9ilu09velXHG---aWLD3PEQGehOxIGgsToWDZQsTQGztXUv_EkAdRfojk-mDaPMvb8fbghtf4XAOEaRXw/9-15-2011%2012-25-23%20PM.png?psid=1 "MTM 11 Preview")

Add a new plan:

![Add new Plan](https://public.bay.livefilestore.com/y1pbYUUNX4b9RUyZ_jUofsd7CoRRLzNvHKe7G6S7YT9A9jv2wzK_I0zkfXrVi5ltWQK4AcF_VmCF_h81bRi2wv8ww/9-15-2011%2012-25-51%20PM.png?psid=1 "Add new Plan")

Open settings and browse to the SnagIt folder:

![Settings](https://public.bay.livefilestore.com/y1pA6rzKWfXPmELpYGkgz4pQsm7wArn-wWzmWGH5zzv8fB0I6Rk_BslQsmbEg18xkmNNMOybhCo13g1PFO9uBsPwA/9-15-2011%2012-32-42%20PM.png?psid=1 "Settings")

Select SnagIt.exe and mark the checkbox for "After taking the snapshot...":

![Select SnagIt.exe](https://public.bay.livefilestore.com/y1pQQ6Yo2fGggSUomd1O7D9d7wfwLIIgt_EdZIvwIOqaOfWK87jf9jMdsxEyqDQ3jERLa-Q3LvwTuV64_Igz3MXEg/9-15-2011%2012-40-08%20PM.png?psid=1 "Select SnagIt.exe")

Start the TR (Test Run) and take a screenshot capture:

![Capture screen](https://public.bay.livefilestore.com/y1ppwC3MMxOiOdtAD0Afm84Tzuv7FBC2WhX7bIQ5DixGRQNlLJHohyftiugSX28AGK1ICaVx0lCpIrshCG4eFarZA/9-15-2011%2012-36-03%20PM.png?psid=1 "Capture screen")

The SnagIt will open, edit the image and save it. You will notice that the edition is saved with the attachment:

![Edit the capture](https://public.bay.livefilestore.com/y1pKhPjriGautzH39duECGv5lbysJcLegpuMMxcSa2PedOxnVDeT3zR0XkQIbaNTw0P6edC2iV1YJ4Ke8ND-axzbA/Capture.PNG?psid=1 "Edit the capture")

---

### Audio Recording

Now you can audio record so the tester can add any comments with voice to the bug or the TR (Test Run). You can also mute or unmute the audio record at any point in time while TR is working:

![Audio Record](https://public.bay.livefilestore.com/y1pVbl4SExTUBPzsknBQR_BsE9TNwAW0fFesazW63ttZBAthBRvy2FWjGkWMlAqkmFlLsg6H6zy0H5YfcM6kQj9LA/2-29-2012%201-12-00%20PM.png?psid=1 "Audio Record")

---

### Exploratory testing without test cases

Now you don’t need to create a fake test case to run Exploratory testing. You just open the run tab and you will find two new items: Do Exploratory Testing and View Exploratory Test Sessions. Now you just need to choose which user stories you want to run the Exploratory test against or even not to choose any and click explore. The TR (Test Runner) will start without needing a test case like in the old MTM (2010). We also notice that we have a create test case button in the TR (Test Runner) that allows us to make a test case directly:

![Exploratory Test in MTM 11](https://public.bay.livefilestore.com/y1poH39lG369t1ZCjXdVhYT90M3Ut-Pf_YhDzKa0elPDERLEth1M6dYT1vjQjPQ4wOAa8Z1fC6b6XXcvx2BohTTHQ/9-15-2011%2012-27-03%20PM.png?psid=1 "Exploratory Test in MTM 11")

After you run some Exploratory sessions, you can open the View Exploratory Sessions at any point of time to analyze the Exploratory session runs:

![View Exploratory sessions](https://public.bay.livefilestore.com/y1pB10ODJBTXU9aGlGa4fmQyjDsIFT3f_2pr2n1pXKHWjue70VIvEgDtLYZiLK2lS45U-hnCHK20vXg_s8snVK3Lg/9-15-2011%2012-47-11%20PM.png?psid=1 "View Exploratory sessions")
