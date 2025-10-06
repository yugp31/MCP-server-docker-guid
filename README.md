# Setting Up an MCP Server with Docker

Lately, I’ve been exploring how AI models can interact with real-world systems — and **Model Context Protocol (MCP)** stood out as a powerful approach.  
This guide explains how to quickly set up and run an MCP server inside **Docker**, so you can experiment safely without dealing with manual dependencies.



## What is MCP?

**Model Context Protocol (MCP)** is a framework that allows AI models to connect with external tools, APIs, or databases through a standardized interface.  
It helps models extend their capabilities by fetching real-time information or performing structured actions beyond simple text generation.



## Prerequisites

Before you start, make sure you have:

- [Docker](https://docs.docker.com/get-docker/) installed  
- [Git](https://git-scm.com/) (optional, for cloning repositories)
- A terminal or command prompt

---

## Step 1: Get the MCP Server Image

You can use a prebuilt Docker image:

```
docker pull ghcr.io/modelcontextprotocol/server:latest
```

Or build it yourself from source:

```
git clone https://github.com/modelcontextprotocol/server.git
cd server
docker build -t mcp-server .
```

## Step 2: Run the MCP Server

Once the image is ready, start the server with:

```
docker run -d \
  --name mcp-server \
  -p 8080:8080 \
  mcp-server
```
Check logs to make sure it’s running correctly:
```
docker logs -f mcp-server
```

## Step 3: Connect a Client
Your MCP server will be available at:
```
http://localhost:8080
```
You can now connect any MCP-compatible client — such as an AI agent, IDE plugin, or your own scripts — to interact with it.

For setups needing persistent data or configuration, use Docker volumes:
```
docker run -d \
  --name mcp-server \
  -p 8080:8080 \
  -v $(pwd)/data:/app/data \
  mcp-server
```
---
## Handy Docker Commands

| Command                                | Description             |
| -------------------------------------- | ----------------------- |
| `docker ps`                            | Show running containers |
| `docker stop mcp-server`               | Stop the server         |
| `docker start mcp-server`              | Start it again          |
| `docker rm mcp-server`                 | Remove the container    |
| `docker exec -it mcp-server /bin/bash` | Open container shell    |

 ---
 ## Why use Docker for MCP?
- Avoids environment and dependency issues
- Easy to rebuild or reset
- Runs consistently on any OS
- Ideal for quick testing and local experiments

##  Resources

- Model Context Protocol Docs - https://modelcontextprotocol.io
- Docker Documentation - https://docs.docker.com/
---
 Tip: Docker makes experimenting with new technologies like MCP simple and risk-free — if something breaks, just restart the container and continue exploring.


## License

This guide is open for anyone to learn from or adapt.
Feel free to fork, share, or build on top of it!
