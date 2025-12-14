# Conversational Interactions (JSON-Based)

This document describes how conversational interactions are handled using **JSON-based request and response payloads** when communicating with **Google Conversational Agents (Dialogflow CX)**.

Each conversational turn represents a single **interaction** between an end-user and the conversational agent.

---

## Interaction Overview

During an interaction:
1. An end-user sends an input message to the conversational agent.
2. The agent processes the input using intent detection, agent orchestration, tools, and grounding.
3. The agent returns a structured response to the end-user.

Although interactions can be performed through both API calls and integration, we will try to choose the API method since it enables us to view the payload and underlying details such as **Session ID** and **Intent Detetction Confidence**.

## Interaction Lifecycle

Each conversational turn follows this flow:

```text
User Input → Dialogflow CX → Agent Reasoning & Tools → Agent Response
```

## Before beginning the interactions, save the request.json file locally.

## To send your request, run the following in the terminal:
```bash
curl -X POST \
     -H "Authorization: Bearer $(gcloud auth print-access-token)" \
     -H "x-goog-user-project: PROJECT_ID" \
     -H "Content-Type: application/json; charset=utf-8" \
     -d @request.json \
     "https://REGION_ID-dialogflow.googleapis.com/v3/projects/PROJECT_ID/locations/REGION_ID/agents/AGENT_ID/sessions/SESSION_ID:detectIntent"
```
