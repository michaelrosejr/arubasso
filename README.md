# Aruba Central - SAML SSO

## Azure AD Integration Guide

### Before you Begin

Go through the [SAML SSO feature description](https://help.central.arubanetworks.com/2.5.3/documentation/online_help/content/nms/user-mgmt/saml-profile-conf.htm?Highlight=SSO) to understand how [SAML](https://help.central.arubanetworks.com/2.5.3/documentation/online_help/content/nms/user-mgmt/saml-profile-conf.htm?Highlight=SSO) framework works in the context of Aruba Central.

In Azure AD, create a Group (Ex: Aruba Central Admins) and add the users that should have access to Aruba Central to this new group. This group will be used to grant access to Aruba Central using the users Azure AD credentials.

### Steps to Configure SSO/SAML Application in Azure AD
To configure SSO in Aruba Central, first download the metadata file from Azure AD.


<ol>
<li>Create an Enteprise Application in the [Azure Portal](https://portal.azure.com)</li>
<li>Upload the azure-metadata file from Azure to Aruba Central</li>
<li>Download the aruba-central-metadata file from Aruba Central</li>
<li>Upload the aruba-central-metadata file to Azure </li>
</ol>


### Step 1: Create an Azure AD Enterprise Application

* Log into to Azure portal.

* Click **Enterprise Applications** (you may need to search for it, if it's not on your menu)

* Click **New Application**
![Image](images/new_app.png)

* Click **Create your own Application**
  
  Enter the name of your app. (Ex: Aruba Central USWEST 4)
![Image](images/create_app.png)
* Select **Integrate any other application you don't find in the gallery (Non-gallery)**
* Under Step 1: Assign users and groups, select the AD Group you created at the beginning of this document.
![Image](images/AssignUsersGroups.png)
* Under Step 2: Set Up Signle sign on
* The default setting is Disabled. Select **SAML** 
![Image](images/select-saml.png)
* Click **Download** under Step 3 : Federation Metadata XML
![Image](images/azure-download-metadata.png)

### Step 2: Create Aruba Central SSO for Azure AD

* Log into Aruba Central
* From the **Account Home**, select **Single-Sign-On**
* Enter your domain name. The domain name must be the email address for the user logging. (Ex: @arubanetworks.com) This is how Aruba Central knows to redriect the authentication request to Azure AD.
* Click **Add SAML PROFILE**
 ![Image](images/central-create-sso.png)
* You'll upload the federated metadata file you downloaded from Azure in the previous step. Click METADATA FILE and Browse. Locate the file you downloaded and upload it to Aruba Central. 

![Image](images/azure-browse-metadata.png)

###FIX


* Then download the Aruba Central metadata file


* Then upload the metadata file (domain_metadata.xml) to Azure AD Enterprise App that you created.

![Image](images/upload-central-metadata-to-azure.png)


