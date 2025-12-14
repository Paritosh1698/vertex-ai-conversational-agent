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
gcloud config set project <PROJECT_ID> # Select from a drop-down of list of active projects
```
### Project Setup (Local)

Create a project structure as below:

```bash
go-app/
├── main.go
├── app.yaml
└── templates/
    └── index.html
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
Populate the app.yaml file with the following
```bash
runtime: go125 # This is the latest version
```
Run the following gcloud command
```bash
gcloud app deploy
```
