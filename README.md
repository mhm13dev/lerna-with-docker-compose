# Nest.js API, Vite React Client with Lerna + Docker Compose

This is a monorepo project that contains a Nest.js API and a Vite React client. The project uses `Lerna` to manage the monorepo and `Docker Compose` to run the services.

## Prerequisites

Before you begin, ensure you have following installed on your machine:

👉 Node.js (LTS version)
👉 NPM
👉 Docker Desktop (including Docker Compose)

## Getting Started

💥💥💥 **DO NOT "npm install" from host! Always install packages from inside a running docker container!!!** 💥💥💥

To get started, clone the repository and run the following commands:

```bash
# Create .env file in packages/api
cd packages/api
cp .env.example .env

# Create .env file in packages/client
cd packages/client
cp .env.example .env
```

## Running the Project

To run the project, use the following command:

```bash
# Start Development
docker compose --profile development up -d

# Stop Development
docker compose --profile development down

# Production
docker compose --profile production up -d

# Stop Production
docker compose --profile production down
```

## Installing Packages

💥💥💥 **DO NOT "npm install \<package-name\>" from host! Always install packages from inside a running docker container!!!** 💥💥💥

To install packages, use the following flow:

👉 Open Docker Desktop
👉 Open the container in which you want to install packages
👉 Open the Exec Console
👉 Run the following command:

```bash
npm install <package-name>
```

💥 It is important to install packages from inside the container to ensure that the correct dependencies are installed which can work cross-platform.

Following the above steps will install the packages in the `node_modules` directory of the _container_ which is mounted to the `node_modules` directory of the _host machine (your computer)_ ensuring the IDE intellisense works correctly.

## Accessing the Services

You can check the Ports for every service in the `docker-compose.yml` file.

👉 API: http://localhost:3000
👉 Client: http://localhost:3001

## Directory Structure

The project has the following directory structure:

```
├── docker-compose.yml
├── Dockerfile (for development)
├── package.json
├── package-lock.json
├── README.md
├── node_modules (Root node_modules)
├── packages
│   ├── api
│   |   ├── ...
│   │   ├── Dockerfile (project specific Dockerfile)
│   │   ├── package.json
│   │   ├── README.md
│   │   ├── .env.example
│   │   ├── .env (project specific environment variables)
│   │   ├── node_modules (project specific node_modules)
│   │   ├── src
│   │   │   ├── ... (Nest.js code)
│   │   │   └── main.ts
│   │   └── nest-cli.json
│   └── client
│       ├── ...
│       ├── Dockerfile (project specific Dockerfile)
│       ├── package.json
│       ├── README.md
│       ├── .env.example
│       ├── .env (project specific environmentl variables)
│       ├── node_modules (project specific node_modules)
│       ├── public
│       ├── src
│       │   ├── ... (React code)
│       │   └── main.tsx
│       └── vite.config.ts
└── lerna.json
```

## Author

👉 [Mubashir Hassan](https://mhm13.dev)
