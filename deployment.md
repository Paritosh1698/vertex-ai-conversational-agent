## Deployment

The application was authenticated and deployed using the **Google Cloud CLI (`gcloud`)**.

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

### Contents of the main.go
Populate the main.go file with the following
```bash
// Package main is the main package
package main

import (
        "log"
        "net/http"
        "os"
        "text/template"
)

var templates *template.Template

func init() {
        templates = template.Must(template.New("").ParseGlob("templates/*"))
}

// indexHandler handles the homepage.
func indexHandler(w http.ResponseWriter, r *http.Request) {
        if r.URL.Path != "/" {
                http.NotFound(w, r)
                return
        }
        if err := templates.ExecuteTemplate(w, "index.html", nil); err != nil {
                log.Fatal(err)
        }
}

func main() {
        // Register the handlers
        http.HandleFunc("/", indexHandler)

        port := os.Getenv("PORT")
        if port == "" {
                port = "8080"
                log.Printf("Defaulting to port %s", port)
        }

        log.Printf("Listening on port %s", port)
        if err := http.ListenAndServe(":"+port, nil); err != nil {
                log.Fatal(err)
        }
```
### UI
After going into the templates, populate the following in the index.html
```bash
<!DOCTYPE html>
<html lang="en-US">
  <head>
    <meta charset="utf-8">
    <meta name="viewport" content="width=device-width">
    <title>Trip Advisor</title>
  </head>
  <body>
    <p>Open the chat window in the bottom right corner.</p>
        <link rel="stylesheet" href="https://www.gstatic.com/dialogflow-console/fast/df-messenger/prod/v1/themes/df-messenger-default.css">
        <script src="https://www.gstatic.com/dialogflow-console/fast/df-messenger/prod/v1/df-messenger.js"></script>
        <df-messenger
            location="LOCATION_ID"
            project-id="PROJECT_ID"
            agent-id="AGENT_ID"
            language-code="en"
            max-query-length="-1">
            <df-messenger-chat-bubble
                chat-title="Trip Advisor">
          </df-messenger-chat-bubble>
        </df-messenger>
        <style>
            df-messenger {
            z-index: 999;
            position: fixed;
            --df-messenger-font-color: #000;
            --df-messenger-font-family: Google Sans;
            --df-messenger-chat-background: #f3f6fc;
            --df-messenger-message-user-background: #d3e3fd;
            --df-messenger-message-bot-background: #fff;
            bottom: 16px;
            right: 16px;
            }
        </style>
  </body>
</html>
```


