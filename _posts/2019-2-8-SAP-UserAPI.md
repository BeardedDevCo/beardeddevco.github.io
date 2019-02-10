---
layout: post
title: Making the SAP User API Available to MDK
author: Sean Campbell
---

So as a little lead in to next weeks series of posts around building your first MDK app I thought I would write something quickly about the user API service. 

Currently in MDK there is no way of getting the logged in user data from SCP. Fortunately there is a really easy work around to this by creating and deploying a very simple UI5 app. 

open webIDE and create a blank UI5 App from the project template. Navigate to the neo-app.json file and add the following code. 


<code>
{
    "path":"/services/userapi",
    "target":{
        "type":"service",
        "name":"userapi"
    }
}
</code>

Save that and Deploy your app to HCP... Thats it, its really that easy to expose the service. If you go to the active URL of the app you created and append the URL with "/services/userapi/currentuser" you will get back the logged in user details. 

Next up we create a destination that points at that URL in mobile services, remember to set the security to AppToAppSSO and the userapi is now available in all your MDK applications. 