## Table of Contents
- [SmartQuestion Bank Application](#smartquestion-bank-application)
  - [Features](#features)
  - [Prerequisites](#prerequisites)
  - [Installation](#installation)
    - [MkDocks Setup](#mkdocks-setup)
    - [Docker Setup](#docker-setup)
    - [Manual Setup (Without Docker)](#manual-setup-without-docker)
      - [1. Backend (Node.js Server)](#1-backend-nodejs-server)
      - [2. Frontend (React Client)](#2-frontend-react-client)
      - [3. MongoDB](#3-mongodb)
      - [4. Ollama](#4-ollama)
  - [Environment Variables](#environment-variables)
  - [Usage](#usage)
    - [Running Commands](#running-commands)
  - [Coding Standard](#coding-standard)
  - [Troubleshooting](#troubleshooting)
- [Project Setup So Far](#project-setup-so-far)
  - [Server](#server)
  - [Client](#client)
  
---

# SmartQuestion Bank Application
This application, SmartQuestion Bank, is a Node.js and React.js project designed to provide an automated, web-based repository and interface for managing exam questions. It leverages MongoDB as the core database and integrates AI-driven smart question generation and analysis powered by Ollama. This README covers how to set up the application using Docker (recommended) and manual setup instructions if you prefer not to use Docker.

To know details about SmartQuestion Bank application click [here](https://github.com/RakibCSE30/Project/wiki/Software-Requirement-Specification)

---

## Features
- Full-stack application with Node.js backend and React.js frontend.
- Secure MongoDB storage for structured question banks, categories, and user roles.
- Smart, automated question generation powered by local Ollama AI models.
- Configurable environment variables for database connection, secret keys, and token duration.

---

## Prerequisites
- Docker and Docker Compose (for Docker setup)
- Node.js (version 18 or higher) and npm/Yarn (for manual setup)
- MongoDB instance (local or MongoDB Atlas)

---

## Installation

### MkDocks setup
---

## 📚 Project Documentation (MkDocs & GitHub Pages)

Our project documentation is built using **MkDocs (Material Theme)** and is automatically hosted via **GitHub Pages**.

### 🌐 Live Docs Link
👉 [Click here to view the Live Documentation Website](https://RakibCSE30.github.io/Project/) 
 

### 🚀 Quick Contribution Guide for the Team:
1. Add or edit your `.md` documentation files inside the `resources/documents/` folder.
2. If you create a new file, update the sidebar navigation in the `mkdocs.yml` file.
3. Push your changes to the `main` branch:
   ```bash
   git add .
   git commit -m "Updated documentation"
   git push origin main

 more detailes click [here](https://github.com/RakibCSE30/Project/wiki/Documentation)  

### Docker Setup
1. Clone the repository:<br>
   **Using HTTPS:**
    ```bash
    git clone [https://github.com/RakibCSE30/Project.git](https://github.com/RakibCSE30/Project.git)
    cd Project
    ```
   **Using SSH:**
    ```bash
    git clone git@github.com:RakibCSE30/Project.git
    cd Project
    ```

2. Update Environment Variables: Create an `.env` file in the root directory with the required variables (see Environment Variables section).

3. Start the Application: Run the following command to start all services using Docker Compose (without GPU support):
    ```bash
    docker compose up -d --build
    ```

    If you want GPU acceleration for the AI model, run this instead:
    ```bash
    docker compose -f docker-compose-ollama-gpu.yml up -d --build
    ```

This will:
- Start the React client on http://localhost:3000.
- Start the Node.js server on http://localhost:5000.
- Start MongoDB on port 27017.
- Start Ollama AI service on port 11434.

4. Access the Application:
   - Frontend (React client): http://localhost:3000
   - Backend API (Node.js server): http://localhost:5000

To stop the application, run:
    ```bash
    docker compose down
    ```

**Note: For GPU acceleration setups, you can follow [Installing the NVIDIA Container Toolkit](https://docs.nvidia.com/datacenter/cloud-native/container-toolkit/latest/install-guide.html) and [GPU Support in Docker Desktop](https://docs.docker.com/desktop/features/gpu/)**

### Manual Setup (Without Docker)
If you prefer to run the application without Docker, follow these steps:

#### 1. Backend (Node.js Server)
- Navigate to the server directory:
    ```bash
    cd server
    ```
- Install dependencies:
    ```bash
    yarn install
    ```
- Create an `.env` file in the server directory with the necessary environment variables (see Environment Variables section).
- Run the server:
    ```bash
    yarn start
    ```
This will start the Node.js server on http://localhost:5000.

#### 2. Frontend (React Client)
- Navigate to the client directory:
    ```bash
    cd client
    ```
- Install dependencies:
    ```bash
    yarn install
    ```
- Run the client:
    ```bash
    yarn start
    ```
This will start the React client on http://localhost:3000.

#### 3. MongoDB
- If you are using MongoDB locally, ensure it is running on port 27017 or update the `MONGO_URI` in the `.env` file with your connection string.

#### 4. Ollama
- If Ollama is required for AI question generation features, install and start Ollama following the official documentation and set the base URL in the `OLLAMA_BASE_URLS` environment variable to `http://localhost:11434`.

---

## Environment Variables
Create an `.env` file in both server and client directories as needed with the following variables:

- **Server Environment Variables** (server/.env):
    ```plaintext
    PORT=5000
    MONGO_URI=mongodb+srv://<username>:<password>@<cluster>.mongodb.net/?retryWrites=true&w=majority
    SECRET_KEY=my-secret-key
    TOKEN_DURATION=1h
    OLLAMA_BASE_URLS=http://smartquestion-ollama:11434 (or http://localhost:11434 if running locally without Docker)
    ```

- **Client Environment Variables** (client/.env) (optional):
    ```plaintext
    # Add any frontend specific variables here.
    ```

---

## Usage

### Running Commands
- **Starting Docker:** `docker compose up --build`
- **Shutting Down Docker:** `docker compose down`

---

## Coding Standard
To keep the source code clean and readable, the project follows standard JavaScript style conventions enforced via ESLint:
* **Variables & Functions:** Always use `camelCase` (e.g., `let userName`, `function getUserData()`).
* **Constants:** Always use `UPPERCASE` with underscores (e.g., `const MAX_LIMIT = 100`).

---

## Troubleshooting

- **Internal Server / AI Errors:**
  - Ensure `OLLAMA_BASE_URLS` is correctly configured. In Docker setups, make sure the network service name matches your Docker compose config instead of using `localhost`.
  
- **Database Connection Issues:**
  - Verify `MONGO_URI` is correct and accessible from within the Docker network (or your local environment).
  
- **Missing Dependencies:**
  - Make sure all required node modules are fresh and installed via `yarn install` inside both the `/client` and `/server` subfolders.

For further help, please refer to the [Docker documentation](https://docs.docker.com/get-started/) or [Ollama documentation](https://github.com/ollama/ollama).

---

# Project Setup So Far
## Server
- [x] Initiate nodejs server
- [x] Configure router
- [x] Connect database
- [x] Add a simple API implementation
- [ ] Add basic authentication
- [ ] Add logging
- [x] Add unit test
- [x] Add lint rules
- [x] Add documentation tool (jsdoc)
- [x] Dockerize
- [ ] Add app runner CLI

## Client
- [x] Create react app for client
- [x] Add frontend components
- [ ] Connect backend REST APIs to frontend
- [ ] Add lint rules
- [ ] Add documentation tool (storybook)
- [x] Dockerize
- [ ] Configure React Router
