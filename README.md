# Vertex AI Conversational Agent using AI Applications

## Overview
This project demonstrates the design and implementation of a conversational AI agent using **Google Cloud Vertex AI Applications**. The agent is built using a Natural Language approach and supports multi-agent orchestration to handle complex user queries through a chat-based interface.

Instead of custom Python tools, the agent is extended using **REST APIs** defined via an **OpenAPI schema**, enabling real-time data access and external system integration.

## Agent Network Design

The conversational system is implemented as a **network of task-based AI agents** orchestrated through **Vertex AI Agent Builder**, enabling modular reasoning and tool invocation.

<img width="790" height="327" alt="Screenshot 2025-12-13 at 6 24 49 PM" src="https://github.com/user-attachments/assets/0f31978b-02ae-4775-b2cf-e4b191062f29" />

## Architecture Overview
- **Vertex AI Agent Builder** for multi-agent orchestration
- Primary conversational agent: *Vancouver City Guide*
- Task-based agents for geolocation and neighbourhood knowledge
- **Automatic RAG** for document grounding
- **OpenAPI-based REST integration** with Google Maps Geocoding API
- Web-based chat interface for user interaction

### Primary Agent
**Vancouver City Guide**  
Acts as the main conversational interface, responsible for:
- Understanding user intent
- Delegating tasks to specialized agents
- Synthesizing responses from multiple agent outputs

### Task-Based Agents

**1. Location Lookup Agent**
- Invoked for geolocation-related queries
- Uses a custom **OpenAPI schema** to call the **Google Maps Geocoding API**
- Converts user-provided addresses into precise latitude and longitude coordinates
- Enables location-aware responses within the conversation

**2. Neighbourhood Information Agent**
- Acts as a structured knowledge base for **Vancouver neighbourhoods**
- Provides historical context, key facts, and curated **Wikipedia references**
- Supports users interested in learning about the history and background of the neighbourhood they are currently in

This multi-agent architecture allows the system to combine **real-time geospatial data** with **static, document-based knowledge**, delivering richer and more context-aware conversational experiences.

## Technologies Used
- Google Cloud Vertex AI (AI Applications)
- Google Cloud Conversational Agents (Previously Dialogflow CX)
- Retrieval-Augmented Generation (RAG)
- Google Maps Geocoding API
- REST APIs & OpenAPI Specification
- Google Cloud CLI (gcloud) for authentication and deployment
- Google Cloud App Engine
- HTML / Web UI

## Use Cases
- City guide and tourism assistants
- Location-aware conversational applications
- Educational tools for urban history and neighbourhood exploration
- Smart assistants for residents and visitors
- AI-powered interfaces combining spatial and historical context


