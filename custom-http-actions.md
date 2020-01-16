<img src="https://tva1.sinaimg.cn/large/006tNbRwgy1gay7syx5kjj30a304mwej.jpg" width="200px"/>

## Creating Custom http actions in MS Flow/Power-Automate to run against Adobe Sign API 

#### Ok .... Why do this at all?

Right now there are Product people prioritizing the new features and configurable options to make the [existing Flow/PA connector](https://docs.microsoft.com/en-us/connectors/adobesign/) for Adobe Sign more powerful and flexible, but in the short term you may have a need to do something it can't accomplish **out of the box**. I've been working with various integrations for Adobe Sign since 2012 and with MS Flow for the last 2 years and there are many things that can be done in Flow that the connector does not yet do. (or possibl)

##### Some concepts to get started:

* To use the generic "http" action to do things with Adobe Sign in Flow (I'll be calling it Flow for brevity) you need to have some example API calls to work from.  I have a link to a pretty large [POSTMAN](https://www.getpostman.com/) collection with many example calls that should work for you against the [Adobe Sign V6 Rest API](https://secure.echosign.com/public/docs/restapi/v6).  You can find a link to it in my "[developer resources](https://github.com/skaboy71/AdobeSign-resources/blob/master/Developer%20Resources.md)" page.
* Becaues many things are "abstracted" in the Adobe Sign "connector" for Flow, in these custom actions you'll need to re-use things like an "[Integration Key](https://helpx.adobe.com/sign/kb/how-to-create-an-integration-key.html)" and the "shard"(The geolocation URL segment that corresponds to where your Adobe Sign account lives)
* It's also expected that you have a basic understanding of Rest APIs and how to use POSTMAN. If not, you may be able to learn a bit as you go and figure it out as it not too complicated.

#### Example #1 You want to create a Flow that will "send-as" the user logged into SharePoint (or some other O365 app you want to use to send for signature)

In the existing Flow integration, you use the "connector" which asks you to use your Adobe Sign credentials to get access to the Adobe Sign Rest api via an oAuth "token".  (I can explain this in more detail somewhere else)  What this means for us right now is that **ALL agreements sent through this new Flow you're creating *will be sent with YOU(or whoever made the Flow and the connection) as the "Sender"***.  If Bob in your IT department has access to this SharePoint site and can start the Flow, he will NOT be the "Sender" of the agreement because the credentials of the person who created it are "baked into" the Flow.

This is not always a desirable way to handle things.  One example of this would be a Flow in a "manager" SharePoint site where many manager's can send HR related docs to their respective reports where they don't want these docs to all show up together under one person's "queue" or manage page in Adobe Sign. 





 

 









