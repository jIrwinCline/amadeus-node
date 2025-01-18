# Flight booking engine using Node + Amadeus API

This repository contains a reworked node api repo for an Amadeus flight booking engine


Go ahead and put your secrets in a .env

```
AMADEUS_CLIENT_ID=YOUR_API_KEY
AMADEUS_CLIENT_SECRET=YOUR_API_SECRET
```

# Development Environment Setup

This repository is configured to work within a **Dev Container** for a consistent and pre-configured development environment.

## Prerequisites

Before opening the Dev Container, ensure you have the following installed:

1. [Docker](https://www.docker.com/)
   - Docker Desktop (Windows/macOS) or Docker Engine (Linux)
2. [Visual Studio Code](https://code.visualstudio.com/)
3. [Dev Containers Extension](https://marketplace.visualstudio.com/items?itemName=ms-vscode-remote.remote-containers)
   - Install via the Extensions Marketplace in VS Code.


Open the Dev Container

Press `Ctrl+Shift+P (or Cmd+Shift+P on macOS)` to open the Command Palette.
Type and select `Dev Containers: Reopen in Container`.

...Wait for Initialization

The container will build and set up based on the configuration in the `.devcontainer/` folder. This may take a few minutes the first time.

Start Coding!
Once the container is running, your development environment will be ready with all necessary dependencies installed.

## Alternative Development Environments

Running with Docker

```
docker-compose build
```
Start your application

```
docker-compose up
```

## Running the code (no Docker)

For authentication add your API key/secret to your environmental variables.

```
export AMADEUS_CLIENT_ID=YOUR_API_KEY
export AMADEUS_CLIENT_SECRET=YOUR_API_SECRET
```

Install the dependences and start the server:

```
cd server
npm install
npm start
```

Install the dependences and start the client:

```
cd client
npm install
npm run build && npm run serve
```

## License

This library is released under the [MIT License](LICENSE).

## Help

You can find us on [StackOverflow](https://stackoverflow.com/questions/tagged/amadeus) or join our developer community on
[Discord](https://discord.gg/cVrFBqx).

