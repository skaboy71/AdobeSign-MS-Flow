## Create a Flow that will "send-as" the user logged into SharePoint (or some other O365 app you want to use to send for signature)

In this example, I'll create a custom list in SharePoint that contains some employee info.  This will be used to "merge" that data via MS Flow/Power-Automate into an Adobe Sign Doc template to gather some info about an upcoming Vacation time.  This will have been requested by employees through some other mechanism.(like MS Forms maybe?)  

The SharePoint list will merge the data from the request into the form, send it for signature to the employee for review and/or possible "correction" and then back to the manager who started the flow for final signature.  This will demonstrate how to create flows using the "http" action in Flow/PA that allow for the "sender" of the Adobe Sign "agreement" to be the user logged into SharePoint or other Office 365 based platform, or any other platform where the email address of the "current user" can be obtained in Flow.  It will also show how to send through Adobe Sign using those "http" actions to "merge" data from other sources into the fields of a for or document.

#### Let's get started!

**Prerequisits for following this tutorial:** 

- Access to an Adobe Sign account as the Admin (this can be a production account or will also work fine if you're using a [free developer's account](https://acrobat.adobe.com/us/en/sign/developer-form.html) )
- Access to Office 365, SharePoint, MS Flow
- You will probably want to have [postman](https://www.getpostman.com/) installed and have imported the example collection from this [URL](https://www.getpostman.com/collections/dc2c35db1924b7b9e782).

### **Pre work:**

1. Get an "integration key" for your Adobe Sign account as the account Admin.
2. [Create an an Adobe Sign Library Template](https://helpx.adobe.com/sign/using/create-document-template.html#Create) Doc with the fields named as listed as the columns in #3 below for use as the "document" being sent in Flow. Make sure to include a "signature" field.
   You can see how I created the fields for the template [on YouTube](https://youtu.be/BONYszknH-w) and get a copy of the final edited pdf [here](https://github.com/skaboy71/AdobeSign-MS-Flow/raw/master/Git-Hub-Flow-Example.pdf).
3. Create a new ["custom" list in SharePoint](https://support.office.com/en-us/article/create-a-list-in-sharepoint-0d397414-d95f-41eb-addd-5e6eff41b083) to house the data and also as a place to attach the "signed" agreement.  for this example, my list contains the following columns which are all text(not formatted as specific data type) and column names contain no spaces just to make the example easier.  It's easy enough to "convert" data types but don't need to spend that time here: 

   - "Employee-Email" (re-name the Title column)
   - "First-Name"
   - "Last-Name"
   - "Start-Date"
   - "End-Date"
   - "Manager-Name"
   - "Manager-Email"
   - "Time-off-description"(this will be a multi-line "plain-text" field not, single text[255]- see [example](https://tva1.sinaimg.cn/large/006tNbRwgy1gb6x7m5ixpj31430u0wmd.jpg))

***Notice the column names above contain no spaces.  This is to avoid needing "encoding" to reference these columns in your Flow and is important.*** 

Once you are finished your list columns should look like this:

![](https://tva1.sinaimg.cn/large/006tNbRwgy1gb6xb17q3pj311o0m2ae6.jpg)






