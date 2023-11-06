# HHA 504 Week 5: Video Hosting, Flask App and Cloud Deployment

## Design Rationale and Principles Followed
- App is a python script utilizing html/tailwind css via Flask
- Content comprised of:
    - A humorous video explaining how to choose an insurance plan, focusing on explaining premiums
    - A table previewing some New York State insurance plans, comparing premiums

## CDN

### CDN setup 

<b> Step 1. Create a storage account on Azure
![Picture](images/az_storagesetup_2.png "Text to show on mouseover")

Step 2. Configure security settings to enable blob anonymous access
![Picture](images/az_storage_setup_3.png "Text to show on mouseover")

Step 3. Create a container within the storage setup
![Picture](images/container_setup_az.png "Text to show on mouseover")

Step 4. Set up Front Doot and CDN within storage account
![Picture](images/az_storage_setup1.png "Text to show on mouseover")

Step 5. Combine the endpoint URL with the CDN url

    Endpoint URL: https://rb-ins-video-cdn.azureedge.net
    Part of the CDN URL: /flaskapp504wk5vid/tiktok_insvideo.mp4

    Unique URL: https://rb-ins-video-cdn.azureedge.net/flaskapp504wk5vid/tiktok_insvideo.mp4

</b>
<b> Azure CDV setup, showcasing URL</b>
![Picture](images/CDN_URL_setup.png "Text to show on mouseover")

<b> Video content hosted on Azure CDN</b>
![Picture](images/CDN_video.png "Text to show on mouseover")

### CDN integration into Flask

Code is integrated into the index.html file


                  <source src="https://rb-ins-video-cdn.azureedge.net/flaskapp504wk5vid/tiktok_insvideo.mp4" type="video/mp4">
                  Your browser does not support the video tag
                  

## Flask app deployed using Azure app services
![Picture](images/azure_deployed_flaskapp.png "Text to show on mouseover")
![Picture](images/az_deployed_flaskapp_2.png "Text to show on mouseover")
![Picture](images/az_deployed_flaskapp_3.png "Text to show on mouseover")

### Steps for deploying Flask app to cloud platform

1. Link azure web app services to google shell enivronment: https://learn.microsoft.com/en-us/cli/azure/install-azure-cli-linux?pivots=apt
            
            
            
            
        #copy into CLI	
        curl -sL https://aka.ms/InstallAzureCLIDeb | sudo bash
	    
        #command prompts for a url and device code for authentication
        az login --use-device-code
	    az webapp up --resource-group <groupname> --name <app-name> --runtime <PYTHON:3.9> --sku <B1> 

2. Click on web link with deployed application

### Responsive design 
<b>
- Video was embed with the following code to allow video to be seen on different sized devices

        <div class="md:flex">
          <div class="md:shrink-0">

Web application on mobile device:

![Picture](images/flask_mobile.PNG "Text to show on mouseover")
</b>

## Validate Asset Delivery - Using GTmetrix

<b> Website hosted in Vancouver Canada, with 2.7 seconds fully loaded time </b>

![Picture](images/Performance_1.png "Text to show on mouseover")
![Picture](images/Performance_2.png "Text to show on mouseover")
![Picture](images/Performance_3.png "Text to show on mouseover")

<b> CDN link confirmed via GTmetrix </b>
![Picture](images/performance_4_cdn.png "Text to show on mouseover")

## Observations and Benefits of using a CDN and cloud deployment

1. CDNs allow websites to load faster based on the user's location
2. Cloud deployment provides enhanced content accesibility and security for websites

## Troubleshooting
1. Had to convert the video from a document to an mp4, then upload video to the azure container as an mp4 file to be able to play in the flask app