# LAB:Google Cloud Fundamentals: Getting Started with App Engine

## Objectives
1. Initialize App Engine.

2. Preview an App Engine application running locally in Cloud Shell.

3.  Deploy an App Engine application, so that others can reach it.

4. Disable an App Engine application, when you no longer want it to be visible.


### 1. Initialize App Engine

    * Initialize your app engine with your project name and set the region where $DEVSHELL_PROJECT_ID is your project ID

        gcloud app create --project=$DEVSHELL_PROJECT_ID

    * A prompt will show asking you to choose a region among all the listed region. 14 is for us-central1

        14
    
    * The appengine will be created in the region you set
    * Clone the source code repository for a sample application in the hello_world directory:

        git clone https://github.com/GoogleCloudPlatform/python-docs-samples

    * Navigate to the source directory

        cd python-docs-samples/appengine/standard_python3/hello_world

### 2. Preview an App Engine application running locally in Cloud Shell (Hello world App)
* We will run the Hello World App in a local, virtual environment in Cloud shell.

    * Download and update the packages list

        sudo apt-get update
    
    * Set up a virtual environment where you will run your application

        sudo apt-get install virtualenv

    * A prompt will show, and you will select Y and press Enter

    * Python virtual environments are used to isolate package installations from the system.

        virtualenv -p python3 venv

    * Activate the virtual environment

        source venv/bin/activate

    * Navigate to your project directory and install dependencies.

        pip install  -r requirements.txt

    * Run the application

        python main.py

### 3. Deploy an App Engine application, so that others can reach it

    * Navigate to the source directory:

        cd ~/python-docs-samples/appengine/standard_python3/hello_world

    * Deploy your Hello World Application

        gcloud app deploy
    
    * If prompted, press Y

    * Launch your browser to view the app at http://YOUR_PROJECT_ID.appspot.com

        gcloud app browse

    * And that is it, you have deployed your app engine.

### 4. Disable the application

    * To disable the application go to cloud console,  click app engine  then settings then click disable application.



    
