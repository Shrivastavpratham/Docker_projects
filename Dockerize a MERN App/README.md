
# MERN 3-Tier Application

This is a Dockerized MERN (MongoDB, Express, React, Node.js) 3-tier application. The project consists of a frontend, a backend, and a MongoDB database, each running in its own Docker container. Docker Compose is used to manage these containers.

## Table of Contents

- [Prerequisites](#prerequisites)
- [Project Structure](#project-structure)
- [Setup](#setup)
- [Running the Application](#running-the-application)
- [Stopping the Application](#stopping-the-application)
- [Environment Variables](#environment-variables)
- [Volumes](#volumes)
- [Contributing](#contributing)
- [License](#license)

## Prerequisites

Make sure you have the following installed on your machine:

- [Docker](https://www.docker.com/get-started)
- [Docker Compose](https://docs.docker.com/compose/install/)

## Project Structure

```plaintext
root
│
├── mern
│   ├── backend
│   │   ├── Dockerfile
│   │   ├── src
│   │   │   └── ...
│   │   └── package.json
│   │
│   └── frontend
│       ├── Dockerfile
│       ├── src
│       │   └── ...
│       └── package.json
│
└── docker-compose.yml
```

- **mern/backend/**: Contains the Node.js backend source code and Dockerfile.
- **mern/frontend/**: Contains the React frontend source code and Dockerfile.
- **docker-compose.yml**: Docker Compose file to orchestrate the services.

## Setup

1. Clone the repository:

   ```bash
   git clone https://github.com/yourusername/your-repo-name.git
   cd your-repo-name
   ```

2. Ensure all necessary environment variables are set up. You can refer to the [Environment Variables](#environment-variables) section.

## Running the Application

To start the application, simply run:

```bash
docker-compose up --build
```

This will build the Docker images for both the frontend and backend and start the containers along with the MongoDB service.

- The frontend will be accessible at `http://localhost:5173`.
- The backend API will be accessible at `http://localhost:5050`.
- The MongoDB service will be running on the default MongoDB port `27017`.

## Stopping the Application

To stop the application and remove the containers, run:

```bash
docker-compose down
```

This will stop all running containers and remove them.

## Environment Variables

The environment variables are defined within the Docker Compose file and do not require a separate `.env` file. The key variables are:

- **Backend**:
  - `MONGO_URI=mongodb://mongo:27017/mydatabase`: Defines the connection string for MongoDB.
  - `PORT=5050`: The port on which the backend server runs.
  
- **Frontend**:
  - `REACT_APP_API_URL=http://backend:5050`: Defines the URL for the backend API.

## Volumes

- **mongo-data**: The MongoDB data is persisted locally using a Docker volume to ensure data is not lost when containers are stopped.

