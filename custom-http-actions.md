### ![image](https://user-images.githubusercontent.com/5784265/72485281-168dea00-37bc-11ea-8ddb-725b3bb324e4.png)

### Creating Custom http actions in MS Flow/"Power-Automate" to run against Adobe Sign API 

###### Some concepts to get started:

* To use the generic "http" action to do things with Adobe Sign in Flow(I'll keep calling it Flow) you need to have some example API calls to work from.  I have a link to a pretty large POSTMAN collection with many calls that should work for you against the Adobe Sign V6 Rest API.  You can find a link to it in my "[developer resources](https://github.com/skaboy71/AdobeSign-resources/blob/master/Developer%20Resources.md)" page.
* Becaues many things are "abstracted" in the Adobe Sign "connector" for Flow, in these custom actions you'll need to re-use things like an "Integration Key" and the "shard"(The geolocation URL segment that corresponds to where your Adobe Sign account lives)

