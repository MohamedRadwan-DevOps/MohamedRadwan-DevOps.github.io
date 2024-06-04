---
layout: post
title:  "umbraco Database Structure"
date:   2010-05-30 07:40:05 +0100
---

To understand the DB we will assume a scenario that we create CMS project for Training Center that provide training in ASP.NET, C#, etc.We will see what happen in DB when we start create most action in Admin site how this effect on the DB, we will see the following Actions

*   Add Document Type (ex."Course Categories")
*   Add Template (ex."Master")
*   Add Content (ex."Programming (of type course Categories)")
*   Publish content
*   Add Data Type
*   Add Macro that use XSLT
*   Add user
*   Add User Type like administrator, writer, and translator
*   Add Member Type
*   Add Member
*   Add Group

First let's see the main object node ID that exist

|Object Node ID “GUID” | Type and Description |       |
|----------------------|----------------------|-------|
|1                     |30A2A501-1978-4DDB-A57B-F7EFED43BA3C |**Data Type ex.** Label, DatePicker, RichText, (Sys & user define)|
|2                     |01BB7FF2-24DC-4C0C-95A2-C24EF72BBAC8 |Recycle Bin **<? >**|
|3                     |EA7D8624-4CFE-4578-A871-24AA946BF34D |Umbraco master root**<?>**|
|4                     |4EA4382B-2F5A-4C2B-9587-AE9B3CF3602E |**Media ex.**Image, file, folder|
|5                     |A2CB7800-F571-4787-9638-BC48539A0EFB |**Document Type ex. Trainer**, Course Management|
|6                     |6FBDE604-4178-42CE-A10B-8A2600A2F07D |**Template ex.** Course Management, Category, New Course|
|7                     |B796F64C-1F99-4FFB-B886-4BF4BC011A9C |**Media ex.** image1, image2|
|8                     |C66BA18E-EAF3-4CFF-8A22-41B16D66A972 |**Content ex.** Business, C #, ASP.NET|
|9                     |9B5416FB-E72F-45A9-A07B-5A9A2709CE43 |**Member Type ex.** Member |
|10                    |366E63B9-880F-4E13-A61C-98069B029728|**Group ex.**Group|
|11|39EB0F98-B348-42A1-8662-E7EB18487560|**Member ex.**Mohamed Radwan, Maged Farag,|
|12|9F68DA4F-A3A8-44C2-8226-DCBD125E4840|**Style sheet** ex.rating, styleCourseHome (Custom CSS)|

**Add Document Type (ex."Course Categories")**

[![Document Type](/assets/images/2010/05/Document-Type.jpg)](/assets/images/2010/05/Document-Type.jpg)

1-add 1 record "node" to **\[umbracoNode\]** Table "with objectNodeID ending with **0EFB**”

2-add 1 record to **\[cmsContentType\]** Table

3-add n records to **\[cmsTab\]** Table "if you add tabs"

4-add n records to **\[cmsContentTypeAllowedContentType\]** Table "if you add structure""with all nodes under this node id"

5-add n records to **\[cmsPropertyType\]** Table"for each property""if you add properties"

**ERD**

[![Document Type DB Diagram](/assets/images/2010/05/Document-Type-DB-Diagram.jpg)](/assets/images/2010/05/Document-Type-DB-Diagram.jpg)

**umbracoNode Table**

[![Document Type DB Diagram t1](/assets/images/2010/05/Document-Type-DB-Diagram-t1.jpg)](/assets/images/2010/05/Document-Type-DB-Diagram-t1.jpg)

**cmsContentType Table**

[![Document Type DB Diagram t2](/assets/images/2010/05/Document-Type-DB-Diagram-t2.jpg)](/assets/images/2010/05/Document-Type-DB-Diagram-t2.jpg)

**cmsTab Table**

[![Document Type DB Diagram t3](/assets/images/2010/05/Document-Type-DB-Diagram-t3.jpg)](/assets/images/2010/05/Document-Type-DB-Diagram-t3.jpg)

**cmsContentTypeAllowedContentType Table**

[![Document Type DB Diagram t4](/assets/images/2010/05/Document-Type-DB-Diagram-t4.jpg)](/assets/images/2010/05/Document-Type-DB-Diagram-t4.jpg)

**Add Template (ex."Master")**

[![Template](/assets/images/2010/05/Template.jpg)](/assets/images/2010/05/Template.jpg)

1-add 1 record "node" to **\[umbracoNode\]** Table "with objectNodeID ending with **F07D**"

2-add 1 record to **\[cmsTemplate\]** Table

3-add 1 record to **\[cmsDocumentType\]** Table "to associate content type with template"

**ERD**

[![Template DB Diagram](/assets/images/2010/05/Template-DB-Diagram.jpg)](/assets/images/2010/05/Template-DB-Diagram.jpg)

**umbracoNode Table**

[![TemplateDBDiagramt1](/assets/images/2010/05/Template20DB20Diagram20t1.jpg)](/assets/images/2010/05/Template20DB20Diagram20t1.jpg)

**cmsTemplate Table**

[![Template DB Diagram t2](/assets/images/2010/05/Template-DB-Diagram-t2.jpg)](/assets/images/2010/05/Template-DB-Diagram-t2.jpg)

**cmsDocumentType Table**

[![Template DB Diagram t3](/assets/images/2010/05/Template-DB-Diagram-t3.jpg)](/assets/images/2010/05/Template-DB-Diagram-t3.jpg)

 

**Add Content (ex."Programming (of type course Categories)")**

[![Content](/assets/images/2010/05/Content.jpg)](/assets/images/2010/05/Content.jpg)

1-add 1 record "node" to **\[umbracoNode\]** Table "with objectNodeID ending with **A972**"

2-add 1 record to **\[cmsContent\]** Table "to associate new content with document type"

3-add 1 record **\[cmsDocument\]** Table "That generate **GUID** of this version"

4-add 1 record **\[cmsContentVersion\]** Table" with the generated **GUID** and the date

5-add 1 record to **\[cmsContentXml\]** Table "with all node information as "**XML**" if you publish it"

6-add n records to **\[cmsPropertyData\]** Table "one record for each data which point to property type id from **\[cmsPropertyType\]** Table""If you add data to its properties”

**ERD**

[![Content DB Diagram](/assets/images/2010/05/Content-DB-Diagram.jpg)](/assets/images/2010/05/Content-DB-Diagram.jpg)

**umbracoNode Table**

[![Content DB Diagram t1](/assets/images/2010/05/Content-DB-Diagram-t1.jpg)](/assets/images/2010/05/Content-DB-Diagram-t1.jpg)

**cmsContent Table**

[![Content DB Diagram t2](/assets/images/2010/05/Content-DB-Diagram-t2.jpg)](/assets/images/2010/05/Content-DB-Diagram-t2.jpg)

**cmsDocument Table**

[![ContentDBDiagramt3](/assets/images/2010/05/Content20DB20Diagram20t3.jpg)](/assets/images/2010/05/Content20DB20Diagram20t3.jpg)

**cmsContentVersionTable**

[![ContentDBDiagramt4](/assets/images/2010/05/Content20DB20Diagram20t4.jpg)](/assets/images/2010/05/Content20DB20Diagram20t4.jpg)

**cmsContentXml Table**

[![ContentDBDiagramt5](/assets/images/2010/05/Content20DB20Diagram20t5.jpg)](/assets/images/2010/05/Content20DB20Diagram20t5.jpg)

**cmsPropertyData Table**

[![Content DB Diagram t6](/assets/images/2010/05/Content-DB-Diagram-t6.jpg)](/assets/images/2010/05/Content-DB-Diagram-t6.jpg)

**cmsPropertyType Table**

[![Document Type DB Diagram t5](/assets/images/2010/05/Document-Type-DB-Diagram-t5.jpg)](/assets/images/2010/05/Document-Type-DB-Diagram-t5.jpg)

**Publish content**

[![Publish Content](/assets/images/2010/05/Publish-Content.jpg)](/assets/images/2010/05/Publish-Content.jpg)

1-add 1 record to **\[cmsDocument\]** Table "That generate **GUID** of this version" and make newest column = True

2-update 1 record of the previous version and make published =True "1" and update date very near of the last one, update newest=false

3-add 1 record to **\[cmsContentVersion\]** Table" with the generated **GUID** and the date

4-add 1 record to **\[cmsContentXml\]** Table "with all node information as "**XML**" if you publish it"

5-add n records to **\[cmsPropertyData\]** Table "one record for each data "if you change any value otherwise it will not add any "ex. content has 4 properties you change 1 property so it will add 4 records considering none changed value as a new values

  
**ERD**

[![Publish Content DB Diagram](/assets/images/2010/05/Publish-Content-DB-Diagram.jpg)](/assets/images/2010/05/Publish-Content-DB-Diagram.jpg)

**cmsDocument Table**

See the previous

**cmsContentVersion Table**

See the previous

**cmsContentXml Table**

See the previous

**cmsPropertyData Table**

See the previous

**Add Data Type**

**[![Data Type](/assets/images/2010/05/Data-Type.jpg)](/assets/images/2010/05/Data-Type.jpg)**

1-add 1 record "node" to **\[umbracoNode\]** Table "with objectNodeID ending with **BA3C**"

2-add 1 record to **\[cmsDataType\]** Table "with the type of the data "**int**, **date**, **txt**" and the type of the control "**dropdown**, **list**"

3-add n records to **\[cmsDataTypePreValues\]** Table "which has all entered values like "**Egypt**, **UAE**, **KSA**"

**ERD**

**[![Data Type DB Diagram](/assets/images/2010/05/Data-Type-DB-Diagram.jpg)](/assets/images/2010/05/Data-Type-DB-Diagram.jpg)**

**umbracoNode Table**

[![Data Type DB Diagram t1](/assets/images/2010/05/Data-Type-DB-Diagram-t1.jpg)](/assets/images/2010/05/Data-Type-DB-Diagram-t1.jpg)

**cmsDataType Table**

[![Data Type DB Diagram t2](/assets/images/2010/05/Data-Type-DB-Diagram-t2.jpg)](/assets/images/2010/05/Data-Type-DB-Diagram-t2.jpg)

**cmsDataTypePreValues Table**

[![Data Type DB Diagram t3](/assets/images/2010/05/Data-Type-DB-Diagram-t3.jpg)](/assets/images/2010/05/Data-Type-DB-Diagram-t3.jpg)

**Add Macro that use XSLT**

**[![Macro](/assets/images/2010/05/Macro.jpg)](/assets/images/2010/05/Macro.jpg)**

1-add 1 record to **\[cmsMacro\]** Table "that associate this macro with the **XSLT** file name if it use **XSLT**"

**ERD**

[![Macro DB Diagram](/assets/images/2010/05/Macro-DB-Diagram.jpg)](/assets/images/2010/05/Macro-DB-Diagram.jpg)

**cmsMacro Table**

[![Macro DB Diagram t](/assets/images/2010/05/Macro-DB-Diagram-t.jpg)](/assets/images/2010/05/Macro-DB-Diagram-t.jpg)

**Add user**

[![User](/assets/images/2010/05/User.jpg)](/assets/images/2010/05/User.jpg)

1-add record to **\[umbracoUser\]** Table

2-add 7 records to **\[umbracoUser2app\]** Table "if you select all modules “**Content**\-**Developer**\-**Media**\-**Members**\-**Settings**\-**Translation**\-**Users**”

**ERD**

[![User DB Diagram](/assets/images/2010/05/User-DB-Diagram.jpg)](/assets/images/2010/05/User-DB-Diagram.jpg)

**umbracoUser Table**

[![User DB Diagram t1](/assets/images/2010/05/User-DB-Diagram-t1.jpg)](/assets/images/2010/05/User-DB-Diagram-t1.jpg)

**umbracoUser2app Table**

[![User DB Diagram t2](/assets/images/2010/05/User-DB-Diagram-t2.jpg)](/assets/images/2010/05/User-DB-Diagram-t2.jpg)

**Add User Type like administrator, writer, and translator**

[![User Type](/assets/images/2010/05/User-Type.jpg)](/assets/images/2010/05/User-Type.jpg)

1-add 1 record to **\[umbracoUserType\]** Table "With all permission needed” "one character for each permission" "**F:C54ZDMOSRPKAUHI**"

**ERD**

[![User Type DB Diagram](/assets/images/2010/05/User-Type-DB-Diagram.jpg)](/assets/images/2010/05/User-Type-DB-Diagram.jpg)

**umbracoUserType**

[![User Type DB Diagram t](/assets/images/2010/05/User-Type-DB-Diagram-t.jpg)](/assets/images/2010/05/User-Type-DB-Diagram-t.jpg)

**Add Specific permission for specific node**

[![Spec premission to spec node](/assets/images/2010/05/Spec-premission-to-spec-node.jpg)](/assets/images/2010/05/Spec-premission-to-spec-node.jpg)

1-add n records to **\[umbracoUser2NodePermission\]** Table for each node for each permission "ex. Node: 1055 premission: 5 for each node, it will add one record for each character of the following "**F:C54ZDMOSRPKAUHI**" if needed

**ERD**

[![Spec premission to spec node DB Diagram](/assets/images/2010/05/Spec-premission-to-spec-node-DB-Diagram.jpg)](/assets/images/2010/05/Spec-premission-to-spec-node-DB-Diagram.jpg)

**umbracoUser2NodePermission**

[![Spec premission to spec node DB Diagram t](/assets/images/2010/05/Spec-premission-to-spec-node-DB-Diagram-t.jpg)](/assets/images/2010/05/Spec-premission-to-spec-node-DB-Diagram-t.jpg)

**Add Member Type**

[![Member Type](/assets/images/2010/05/Member-Type.jpg)](/assets/images/2010/05/Member-Type.jpg)

1-add 1 record "node" to **\[umbracoNode\]** Table "with objectNodeID ending with **CE43**"

2-add 1 record to **\[cmsContentType\]** Table "like adding document type" to be associated with members like content to be associated with document

**ERD**

[![Member Type DB Diagram](/assets/images/2010/05/Member-Type-DB-Diagram.jpg)](/assets/images/2010/05/Member-Type-DB-Diagram.jpg)

**umbracoNode Table**

[![Member Type DB Diagram t](/assets/images/2010/05/Member-Type-DB-Diagram-t.jpg)](/assets/images/2010/05/Member-Type-DB-Diagram-t.jpg)

**cmsContentType Table**

[![Member Type DB Diagram t2](/assets/images/2010/05/Member-Type-DB-Diagram-t2.jpg)](/assets/images/2010/05/Member-Type-DB-Diagram-t2.jpg)

**Add Member**

[![Member](/assets/images/2010/05/Member.jpg)](/assets/images/2010/05/Member.jpg)

1-add 1 record "node" to **\[umbracoNode\]** Table "with objectNodeID ending with **7560**"

2-add 1 record to **\[cmsContent\]** Table "to associate new content (member) with member type (like document type)"

3-add 1 record to **\[cmsContentVersion\]** Table" with the generated GUID and the date

4-add 1 record to **\[cmsContentXml\]** Table "with all node information as xml"

5-add n record **\[cmsMember2MemberGroup\]** Table “if we add it to group" "1 record for each group to this member with member nodeid and group nodeid"

**ERD**

[![Member DB Diagram](/assets/images/2010/05/Member-DB-Diagram.jpg)](/assets/images/2010/05/Member-DB-Diagram.jpg)

**umbracoNode**

[![Member DB Diagram t1](/assets/images/2010/05/Member-DB-Diagram-t1.jpg)](/assets/images/2010/05/Member-DB-Diagram-t1.jpg)

**cmsContent**

See the previous

**cmsContentVersion**

See the previous

**cmsContentXml**

See the previous

**cmsMember2MemberGroup**

[![Member DB Diagram t2](/assets/images/2010/05/Member-DB-Diagram-t2.jpg)](/assets/images/2010/05/Member-DB-Diagram-t2.jpg)

**Add Group**

[![Group](/assets/images/2010/05/Group.jpg)](/assets/images/2010/05/Group.jpg)

1-add 1 record "node” to **\[umbracoNode\]** Table "with objectNodeID ending with **9728**"

**umbracoNode Table**

[![Group t1](/assets/images/2010/05/Group-t1.jpg)](/assets/images/2010/05/Group-t1.jpg)