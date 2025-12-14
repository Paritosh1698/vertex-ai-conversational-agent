## Deployment

The application is authenticated and deployed using the **Google Cloud CLI (`gcloud`)**.

Key steps included:
- Authenticating the local environment using `gcloud auth`
- Setting the active project and region
- Deploying the application to Google Cloud using App Engine

### Example Commands
```bash
gcloud init # If you haven't initialized Google Cloud CLI
gcloud auth login # Takes you to the browser page to authenticate
gcloud config set project <PROJECT_ID> # Select from a drop-down list of active projects
```
### Project Setup (Local)

Create a project structure as below:

```bash
go-app/
├── main.go # This file contains the application code
├── app.yaml # This is used to specify the runtime environment
└── templates/
    └── index.html # Template that contains HTML for the homepage
```

Step 1: Select the working directory
```bash
cd ~/MyDirectory
```

Step 2: Create the directory structure
```bash
mkdir -p go-app/templates
```

Step 3: Create the required files
```bash
touch go-app/main.go
touch go-app/app.yaml
touch go-app/templates/index.html
```
Step 4: Deploy the agent
```bash
gcloud app deploy
```
Step 5: Launch the browser page
```bash
gcloud app browse
```
