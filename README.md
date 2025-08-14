<div align="center">
  <img src="docs/karen.png" alt="Karen" width="200"/>
</div>

# Karen 

AI assistant to create issues on GitHub when stuff doesn't work. You know, a complainer.

This repository is based on the setup in shalayev/hani: 
* Goose as the AI assistant.
* Docker Model Runner as the LLM runtime.
* MCP gateway for tools: 
  - uses Github (official) MCP server with the following tools on the allow list: 
    - list_issues,create_issue,add_issue_comment
* ttyd for browser experience, cloudflare quick tunnels for showing off. 

# Setup

Enable Docker Model Runner in Docker.
Set up the personal access token for GitHub in the `.mcp-secrets.env` 

Edit the `.env` if you want to use another model. 
Optionally pre-pull the model you're going to use: 
```
docker model pull $MODEL_N
```

# Run

```
docker compose up --build
```

Open [localhost:7681](http://localhost:7681). Complain about some open source software, for example:

```
so shelajev/hani is really hard to configure for custom use cases. Like they mention goosehints but have absolutely no examples of how to use it!
```

# Extend

You can use this setup to create other AI assistants.
Edit the `.env` file to specify the model you want to use, the mcp servers from Docker MCP catalog, and the filter for the tools to allow. 
Note: local models are very sensitive to context, so try to limit the amount of tools and servers you include, or they easily get confused. 

Edit the `goosehints.md` file to include your system prompt aka. business logic. When you are building a trader assistant, probably it's a good place to explain what, for example, a bear spread is, and include other domain-specific knowledge.

Rerun the compose command to apply the changes.





