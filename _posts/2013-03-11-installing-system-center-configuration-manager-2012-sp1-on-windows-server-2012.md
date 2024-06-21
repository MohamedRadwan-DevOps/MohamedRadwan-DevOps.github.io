---
layout: post
title: "Installing System Center Configuration Manager 2012 SP1 on Windows Server 2012"
date: 2013-03-11 09:59:29 +0100
---

Microsoft System Center 2012 is one of the perfect tools that integrate and work with ALM to provide a very powerful ALM environment in different areas. For example, SCOM (System Center Operation Manager) integrates with TFS in the DevOps scenario to support integration between Development and Operation, among many other scenarios. I will start to show some of these wonderful integrations, beginning with how to install System Center 2012 Configuration Manager SP1 (SCCM 2012 SP1) with MS SQL Server 2012 SP1 on Windows Server 2012.

### Sections

- **Examine the environment**
- **Add required Windows Roles and Features for Windows Server 2012**
- **Create a System Management Container on the DC machine**
- **Extend the Active Directory Schema on the SCCM machine**
- **Install SQL Server 2012 SP1 on Windows Server 2012**
- **Download and install Assessment and Deployment Kit**
- **Install System Center Configuration Manager 2012 SP1**

The following is a step-by-step video for this post.

{% include embed/youtube.html id='mhQPhda-aRk' %}

### Examine the environment

In this scenario, I have 3 machines: Domain Controller (DC08.com), SCCM (SCCM-2012), and one client with Windows 8 (SCCM-Client-Win8). Of course, the SCCM-2012 and SCCM-Client-Win8 are joined to the domain.

![1-Architecture](/assets/img/2013/03/1-architecture-1.jpg)

### Add required Windows Roles and Features for Windows Server 2012

Open the Server Manager and click on **Add roles and features**.

![2-Add roles and features](/assets/img/2013/03/2-add-roles-and-features.jpg)

Click next until you reach **Server Roles**.

![3-Add role and feature next](/assets/img/2013/03/3-add-role-and-feature-next.jpg)

In the Server Roles, choose **Web Server (IIS)**, add the required features, and then click **Next**.

![4-Server Roles- Web Server (IIS)](/assets/img/2013/03/4-server-roles-web-server-iis.jpg)

![5-Add features that are required for Web Server (IIS)](/assets/img/2013/03/5-add-features-that-are-required-for-web-server-iis.jpg)

Select **.NET Framework 3.5** and ensure **4.5** is also selected. After that, select **BITS** and add the required features, then scroll down.

![6-Features-.NET Framework 3.5 Features-Background Intelligent Transfer Service (BITS)](/assets/img/2013/03/6-features-net-framework-3-5-features-background-intelligent-transfer-service-bits-1.jpg)

![7-Add features that required for Background Intelligent Transfer Service (BITS)](/assets/img/2013/03/7-add-features-that-required-for-background-intelligent-transfer-service-bits.jpg)

Add **Remote Differential Compression**.

![8-Features - Remote Differential Compression](/assets/img/2013/03/8-features-remote-differential-comperssion.jpg)

In Security, choose **Basic Authentication**, **IP and Domain Restrictions**, **URL Authorization**, and **Windows Authentication**.

![9-Web Server Role (IIS) Security](/assets/img/2013/03/9-web-server-role-iis-security.jpg)

Add **ASP, ASP.NET 3.5, ASP.NET 4.5**, and any other required features, then scroll down.

![10-Web Server Role (IIS) Application Development](/assets/img/2013/03/10-web-server-role-iis-application-developement-1.jpg)

Add **IIS 6 WMI Compatibility, IIS Management Scripts and Tools, Management Service** and click **Next**.

![11-Web Server Role (IIS) Management Tools](/assets/img/2013/03/11-web-server-role-iis-management-tools-1.jpg)

Select **Restart the destination** and then click on **Specify an alternate source path**.

![12-Confirm installation selections](/assets/img/2013/03/12-confirm-installation-selections-1.jpg)

Insert the Windows Server 2012 DVD into the machine, put its drive letter followed by `:\Sources\sxs`, and click **OK**.

![13-Specify Alternate Source Path](/assets/img/2013/03/13-secify-alternate-source-path-1.jpg)

After the installation is complete, click on **Close**.

![14-Add Roles and Features Wizard Installation Complete](/assets/img/2013/03/14-add-roles-and-features-wizard-instllation-complete-1.jpg)

### Create a System Management Container on the DC machine

Connect to the Domain Controller machine using **Remote Desktop**.

![15-Remote Connect to Domain Controller](/assets/img/2013/03/15-remote-connect-to-domain-controller-1.jpg)

From the run type `ADSIedit.msc` to open the **ADSI**, click connect to, and accept the default.

![16-Connect to Default naming context](/assets/img/2013/03/16-connect-to-default-naming-context.jpg)

Navigate to System and create a new container with the exact spelling and case: "**System Management**".

![17-Add System Management Container](/assets/img/2013/03/17-add-system-management-container.jpg)

Open the **Active Directory Users and Computers** and from the **View** menu click on **Advanced Features**.

![18-Open Active Directory Users and Computers and Open Advanced Features](/assets/img/2013/03/18-open-active-directory-users-and-computers-and-open-advanced-features.jpg)

Navigate to "System Management" and add the SCCM machine to it.

![19-Choose SCCM-2012 Machine](/assets/img/2013/03/19-choose-sccm-2012-machine.jpg)

Give the SCCM machine full control permission and click **Advanced**.

![20-Give SCCM Full Control](/assets/img/2013/03/20-give-sccm-full-control.jpg)

Select the SCCM machine and click **Edit**.

![21-Edit Permission for SCCM-2012 Machine](/assets/img/2013/03/21-edit-permission-for-sccm-2012-machine.jpg)

Change the apply to "This object and all descendant objects" and choose **Apply this permission**.

![22-Apply to This object and all descendant objects](/assets/img/2013/03/22-apply-to-this-object-and-all-descentdant-objects.jpg)

Close the Active Directory remote desktop, we will not use it again for now.

![23-Close Domain Controller Machine](/assets/img/2013/03/23-close-domain-controller-machine.jpg)

### Extend the Active Directory Schema on the SCCM machine

Insert the SCCM DVD into your DVD and navigate to `SMSSETUP\BIN\X64`. Double-click on `extadsch`.

![24-Run Extend Active Directory Schema (extadsch)](/assets/img/2013/03/24-run-extend-active-directory-schema-extadsch-1.jpg)

Navigate to the C drive and open the created file `ExtADSch.txt`.

![25-Open extend active directory schema file (ExtADSch)](/assets/img/2013/03/25-open-extend-active-directory-schema-file-extadsch.jpg)

Make sure that it successfully extends the schema.

![26-Review Successfully extended the Active Directory schema](/assets/img/2013/03/26-review-successfully-extended-the-active-directory-schema.jpg)

### Install SQL Server 2012 SP1 on Windows Server 2012

Insert or mount the SQL Server 2012 DVD into your DVD drive and click on **New SQL Server stand-alone installation**.

![27-New SQL Server stand-alone installation or add features to existing installation](/assets/img/2013/03/27-new-sql-server-stand-alon-instllation-or-add-features-to-existing-installation.jpg)

It's better to include the update and then click **Next**.

![28-Include SQL Server product updates](/assets/img/2013/03/28-include-sql-server-product-updates.jpg)

Select **SQL Server Feature Installation**.

![29-SQL Server Feature Installation](/assets/img/2013/03/29-sql-server-feature-installation.jpg)

Select **Database Engine Services** and scroll down.

![30-Database Engine Services](/assets/img/2013/03/30-database-engine-services.jpg)

Select **Client Tools Connectivity, Management Tools Basic, Management Tools Complete**, and click **Next**.

![31-Client Tools Connectivity and Management Tools Basic](/assets/img/2013/03/31-client-tools-connectivity-and-management-tools-basic.jpg)

Make all services automatic and assign **Network Services** for **SQL Server Database Engine**.

![32-Specify the service accounts for SQL](/assets/img/2013/03/32-specify-the-service-accounts-for-sql.jpg)

Review the Collation and make sure it's "latin1_general_ci_as", then click **Next**.

![33-Specify the SQL collation](/assets/img/2013/03/33-specify-the-sql-collation-1.jpg)

Add the current user that will be used to install SCCM 2012, click next until the installation completes.

![34-Specify Database Engine authentication security mode-Add current user](/assets/img/2013/03/34-specify-database-engine-authentication-security-mode-add-current-user-1.jpg)

After installation completes, open **SQL Server Management Studio** and click on the instance name and choose **Properties**. Choose **Memory**, enter **4000** as **Minimum** and **Maximum** server memory. It's recommended to be **8000**.

![34-2-Set Minimum and Maximum server memory for SQL Server](/assets/img/2013/03/34-2-set-minimum-and-maximum-server-memory-for-sql-server-1.jpg)

### Download and install Assessment and Deployment Kit

Download the [Assessment and Deployment Kit](http://msdn.microsoft.com/en-us/library/windows/hardware/hh825420.aspx "Assessment and Deployment Kit"). For download, click [here](http://www.microsoft.com/en-eg/download/details.aspx?id=34866 "Download") and then click on `adksetup`.

![35-Download and run Assessment and Deployment Kit](/assets/img/2013/03/35-download-and-run-assessment-and-deployment-kit-1.jpg)

Only select Deployment Tools, Windows Preinstallation Environment (Windows PE), User State Migration Tools, and then click Install.

![36-Select Deployment Tools-Windows PE and USMT](/assets/img/2013/03/36-select-deployment-tools-windows-pe-and-usmt-1.jpg)

![37-Assessment and Deployment Kit Installing features](/assets/img/2013/03/37-assessment-and-deployment-kit-installing-features-1.jpg)

### Install System Center Configuration Manager 2012 SP1

Insert the media of System Center Configuration Manager SP1 (SCCM 2012) into your machine and click **Install**.

![38-Install System Center 2012 SP1](/assets/img/2013/03/38-install-system-center-2012-sp1.jpg)

Select **Install a Configuration Manager primary site** and then click **Next**. For more understanding about why we choose this option and the other options, see the video for this post.

![39-Install a Configuration Manager primary site](/assets/img/2013/03/39-install-a-configuration-manager-primary-site.jpg)

Select and accept all license terms and conditions.

![40-Accept all](/assets/img/2013/03/40-accept-all-1.jpg)

Browse and choose the path to download the needed files for installation.

![41-Download required files](/assets/img/2013/03/41-download-required-files.jpg)

After the download completes, click **Next**.

![42-Server Language Selection](/assets/img/2013/03/42-server-language-selection.jpg)

Type a code for the site and the site name. Deselect the installation of Management Console; we will install it later.

![43-Site and Installation Settings](/assets/img/2013/03/43-site-and-installation-settings.jpg)

Select **Install the primary site as stand-alone site**.

![44-Primary Site Installation](/assets/img/2013/03/44-primary-site-installation.jpg)

Enter the SQL Server name here. We will leave the default since SCCM will be installed on the same machine with SQL Server.

![45-Database Information](/assets/img/2013/03/45-database-information.jpg)

We choose where to install the SMS provider; we will leave the default on the same machine.

![46-SMS Provider Settings](/assets/img/2013/03/46-sms-provider-settings.jpg)

Select **Configure the communication method on each site system role**.

![47-Client Computer Communication Settings](/assets/img/2013/03/47-client-computer-communication-settings.jpg)

Leave the default to install **management point** and the **distribution point** and click **Next**.

![48-Site System Roles](/assets/img/2013/03/48-site-system-roles.jpg)

The prerequisite check runs and shows some warnings. We can install WSUS later and it's OK for the other warnings. Click **Begin Install**.

![49-Prerequisite Check](/assets/img/2013/03/49-prerequisite-check.jpg)

The installation starts and we review it until complete.

![50-Installation Complete](/assets/img/2013/03/50-installation-complete.jpg)

Click on **Install Configuration Manager console**.

![51-Install Configuration Manager console](/assets/img/2013/03/51-install-configuration-manager-console.jpg)

![52-Install Configuration Manager console](/assets/img/2013/03/52-install-configuration-manager-console.jpg)

Type the name of the server that has SCCM; in our case, it's the same machine, but of course, we can install this console on any machine, even on a desktop machine.

![53-Identify Site server name](/assets/img/2013/03/53-identify-site-server-name.jpg)

![55-SCCM Console Installation Complete](/assets/img/2013/03/55-sccm-console-installation-complete-1.jpg)

Now the System Center Configuration Manager Console will open and it's ready to use :-)

![56-System Center Configuration Manager 2012 SP1](/assets/img/2013/03/56-system-center-configuration-manager-2012-sp1.jpg)
