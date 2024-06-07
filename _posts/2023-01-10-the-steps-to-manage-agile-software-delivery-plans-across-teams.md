---
layout: post
title: "The steps to manage Agile software delivery plans across teams"
date:   2023-01-10 12:33:15 +0100
---

The delivery plan shows the scheduled work items by sprint of selected
teams against a calendar view, we use it to ensure that our teams are
aligned with our organizational goals.
We are going to use an Azure DevOps Demo Generator Template project
which is: Manage Agile Software delivery plans across teams.


<figure class="wp-block-image size-large">
<img
src="/assets/images/2023/03/3-select-template-1024x550.png"
class="wp-image-10709" />
</figure>

## 1. **Create the Delivery Plan**

1. Select the Template and create the project.
2. From the Boards of the created project, select Delivery Plans.
3. It will show that there are no plans, so let\'s create a new one.
4. Click on the New Plan button.

<figure class="wp-block-image size-large">
<img
src="/assets/images/2023/03/7-new-plan-1024x551.png"
class="wp-image-10710" />
</figure>

5\. Type your delivery plan\'s desired name.
6. Add teams, I have added two teams (one for the web team and the other
for the Engine team).
7. Select Backlog for each team (maybe on Epic, Feature, or Backlog Item
levels), I have selected Backlog items.
8. Click Create.

<figure class="wp-block-image size-large">
<img
src="/assets/images/2023/03/8-delivery-plan-configs-1024x553.png"
class="wp-image-10711" />
</figure>

## **2. Add milestone markers.**

1\. From the settings of the delivery plan, select add markers\
2. To set a marker, open **Markers**, specify a date and specify a
hexadecimal colour, or choose the colour palette icon to change to a new
colour selected by the system.\
3. To add more markers, choose **+ Add marker**. You can add up to 30
markers. The **+ Add marker** button becomes disabled after 30 markers
have been added.
4. Choose **Save** when you are done.

<figure class="wp-block-image size-large">
<img
src="/assets/images/2023/03/12-markers-added-1024x549.png"
class="wp-image-10712" />
</figure>

Markers appear on the plan as shown.

<figure class="wp-block-image size-large">
<img
src="/assets/images/2023/03/13-marker-added-1024x550.png"
class="wp-image-10713" />
</figure>

## 3. Track dependencies by using Delivery Plans

With Delivery Plans, you can track dependencies that have been added to
work items.\
Those cards with a green icon indicate there are no dependency issues.\
Those cards with a-red icon indicate there are issues with one or more
dependencies.
Dependency issues arise when a predecessor work item is scheduled to
finish after a successor work item.

<figure class="wp-block-image size-large">
<img
src="/assets/images/2023/03/16-four-depend-1024x551.png"
class="wp-image-10716" />
</figure>

To view dependency lines for a work item, select the top or bottom of
its card.
To dismiss the lines select the top or bottom of the card again, or
anywhere else within the plan.
Dependency lines that have no issues show up as black lines.

<figure class="wp-block-image size-large">
<img
src="/assets/images/2023/03/19-green-arrow-direction-1024x550.png"
class="wp-image-10717" />
</figure>

Dependency lines that have issues, show up with red lines.
The issues indicate that the successor work item is scheduled to end
before the predecessor work item is completed.

<figure class="wp-block-image size-large">
<img
src="/assets/images/2023/03/18-red-arrow-direction-1024x553.png"
class="wp-image-10718" />
</figure>

After defining all the wrong dependencies, you can fix them by
reordering the items to the sprints.
After moving items the dependency has been fixed (the colour will be
changed from red to green).

<figure class="wp-block-image size-large">
<img
src="/assets/images/2023/03/22-all-are-green-1024x551.png"
class="wp-image-10719" />
</figure>

