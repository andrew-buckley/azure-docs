---
title: 'Tutorial: Configuring LinkedIn Lookup for automatic user provisioning with Azure Active Directory | Microsoft Docs'
description: Learn how to configure Azure Active Directory to automatically provision and de-provision user accounts to LinkedIn Lookup.
services: active-directory
documentationcenter: ''
author: asmalser-msft
writer: asmalser-msft
manager: stevenpo

ms.assetid: d4ca2365-6729-48f7-bb7f-c0f5ffe740a3
ms.service: active-directory
ms.workload: identity
ms.tgt_pltfrm: na
ms.devlang: na
ms.topic: article
ms.date: 04/15/2017
ms.author: asmalser-msft
---

# Tutorial: Configuring LinkedIn Lookup for Automatic User Provisioning


The objective of this tutorial is to show you the steps you need to perform in LinkedIn Lookup and Azure AD to automatically provision and de-provision user accounts from Azure AD to LinkedIn Lookup. 

## Prerequisites

The scenario outlined in this tutorial assumes that you already have the following items:

*   An Azure Active Directory tenant
*   A LinkedIn Lookup tenant 
*   An administrator account in LinkedIn Lookup with access to the LinkedIn Account Center

> [!NOTE]
> Azure Active Directory integrates with LinkedIn Lookup using the [SCIM](http://www.simplecloud.info/) protocol.

## Assigning users to LinkedIn Lookup

Azure Active Directory uses a concept called "assignments" to determine which users should receive access to selected apps. In the context of automatic user account provisioning, only the users and groups that have been "assigned" to an application in Azure AD will be synchronized. 

Before configuring and enabling the provisioning service, you will need to decide what users and/or groups in Azure AD represent the users who need access to LinkedIn Lookup. Once decided, you can assign these users to LinkedIn Lookup by following the instructions here:

[Assign a user or group to an enterprise app](active-directory-coreapps-assign-user-azure-portal.md)

### Important tips for assigning users to LinkedIn Lookup

*	It is recommended that a single Azure AD user be assigned to LinkedIn Lookup to test the provisioning configuration. Additional users and/or groups may be assigned later.

*	When assigning a user to LinkedIn Lookup, you must select the **User** role in the assignment dialog. The "Default Access" role does not work for provisioning.


## Configuring user provisioning to LinkedIn Lookup

This section guides you through connecting your Azure AD to LinkedIn Lookup's SCIM user account provisioning API, and configuring the provisioning service to create, update and disable assigned user accounts in LinkedIn Lookup based on user and group assignment in Azure AD.

> [!TIP]
> You may also choose to enabled SAML-based Single Sign-On for LinkedIn Lookup, following the instructions provided in [Azure portal](https://portal.azure.com). Single sign-on can be configured independently of automatic provisioning, though these two features complement each other.


### To configure automatic user account provisioning to LinkedIn Lookup in Azure AD:


The first step is to retrieve your LinkedIn access token. If you are an Enterprise administrator, you can self-provision an
    access token. In your account center, go to **Settings &gt; Global Settings** and open the **SCIM Setup** panel.

> [!NOTE]
> If you are accessing the account center directly rather than through a link, you can reach it using the following steps.

1)  Sign in to Account Center.

2)  Select **Admin &gt; Admin Settings** .

3)  Click **Advanced Integrations** on the left sidebar. You are
    directed to the account center.

4)  Click **+ Add new SCIM configuration** and follow the procedure by
    filling in each field.

> When auto­assign licenses is not enabled, it means that only user
> data is synced.

![LinkedIn Lookup Provisioning](./media/active-directory-saas-linkedinlookup-provisioning-tutorial/linkedin_1.PNG)

> When auto­license assignment is enabled, you need to note the
> application instance and license type. Licenses are assigned on a
> first come, first serve basis until all the licenses are taken.

![LinkedIn Lookup Provisioning](./media/active-directory-saas-linkedinlookup-provisioning-tutorial/linkedin_2.PNG)

5)  Click **Generate token**. You should see your access token display
    under the **Access token** field.

6)  Save your access token to your clipboard or computer before leaving
    the page.

7) Next, sign in to the [Azure portal](https://portal.azure.com), and browse to the **Azure Active Directory > Enterprise Apps > All applications**  section.

8) If you have already configured LinkedIn Lookup for single sign-on, search for your instance of LinkedIn Lookup using the search field. Otherwise, select **Add** and search for **LinkedIn Lookup** in the application gallery. Select LinkedIn Lookup from the search results, and add it to your list of applications.

9)	Select your instance of LinkedIn Lookup, then select the **Provisioning** tab.

10)	Set the **Provisioning Mode** to **Automatic**.

![LinkedIn Lookup Provisioning](./media/active-directory-saas-linkedinlookup-provisioning-tutorial/linkedin_3.PNG)

11)  Fill in the following fields under **Admin Credentials** :

* In the **Tenant URL** field, enter https://api.linkedin.com.

* In the **Secret Token** field, enter the access token you generated in step 1 and click **Test Connection** .

* You should see a success notification on the upper­right side of
    your portal.

12) Enter the email address of a person or group who should receive provisioning error notifications in the **Notification Email** field, and check the checkbox below.

13) Click **Save**. 

14) In the **Attribute Mappings** section, review the user and group attributes that will be synchronized from Azure AD to LinkedIn Lookup. Note that the attributes selected as **Matching** properties will be used to match the user accounts and groups in LinkedIn Lookup for update operations. Select the Save button to commit any changes.

![LinkedIn Lookup Provisioning](./media/active-directory-saas-linkedinlookup-provisioning-tutorial/linkedin_4.PNG)

15) To enable the Azure AD provisioning service for LinkedIn Lookup, change the **Provisioning Status** to **On** in the **Settings** section

16) Click **Save**. 

This will start the initial synchronization of any users and/or groups assigned to LinkedIn Lookup in the Users and Groups section. Note that the initial sync will take longer to perform than subsequent syncs, which occur approximately every 20 minutes as long as the service is running. You can use the **Synchronization Details** section to monitor progress and follow links to provisioning activity reports, which describe all actions performed by the provisioning service on your LinkedIn Lookup app.


## Additional Resources

* [Managing user account provisioning for Enterprise Apps](active-directory-enterprise-apps-manage-provisioning.md)
* [What is application access and single sign-on with Azure Active Directory?](active-directory-appssoaccess-whatis.md)
