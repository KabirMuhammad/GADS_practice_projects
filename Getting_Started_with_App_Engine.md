## Lab: Google Cloud Fundamentals: Getting Started with App Engine 

## Objectives 

In this lab, you learn how to perform the following tasks:

    - Initialize App Engine.

    - Preview an App Engine application running locally in Cloud Shell.

    - Deploy an App Engine application, so that others can reach it.

    - Disable an App Engine application, when you no longer want it to be visible.

Task 1: Sign in to the Google Cloud Platform (GCP) Console with the credentials generated for you by Google

Task 2: Initialize App Engine 

    1. Initialize your App engine App with your project and choose its region 

        gcloud app create --project=$DEVSHELL_PROJECT_ID

    2. Clone the source code repository for a sample application in the hello_world directory

        git clone https://github.com/GoogleCloudPlatform/python-docs-samples

    3. Navigate to the source directory 

        cd python-docs-samples/appengine/standard_python3/hello_world

Task 3: Run Hello World application locally

    1. Execute the following command to download and update the packages list

        sudo apt-get update

    2. Set up a virtual environment in which you will run your application

        sudo apt-get install virtualenv

        virtualenv -p python3 venv

    3. Activate the virtual environment

        source venv/bin/activate

    4. Navigate to your project directory and install dependencies

        pip install  -r requirements.txt

    5. Run the application 

        python main.py

    6. Click Web preview (Web Preview) > Preview on port 8080 to preview the application

    7. To end the test, press Ctrl+C to abort the deployed service

Task 4: Deploy and run Hello World on App Engine

    1. Navigate to the source directory

        cd ~/python-docs-samples/appengine/standard_python3/hello_world

    2. Deploy your Hello World application 

        gcloud app deploy 

    3. Launch your browser to view the app at http://YOUR_PROJECT_ID.appspot.com where YOUR_PROJECT_ID is the Project ID assigned by Google

        gcloud app browse

    4. Copy and paste URL into a new browser tab. 

Task 5: Disable the application 

    1. App Engine offers no option to Undeploy an application. After an application is deployed, it remains deployed,
    
      although you could instead replace the application with a simple page that says something like "not in service 
     
      However, you can disable the application, which causes it to no longer be accessible to users.

    2. In the Cloud Console, on the Navigation menu, click App Engine > Settings > Click Disable application 

       Enter the App ID and click DISABLE.

    3. You created your first application using App Engine!