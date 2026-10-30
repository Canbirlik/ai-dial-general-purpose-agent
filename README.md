# General Purpose Agent

A tool-augmented AI agent built with the [DIAL platform](https://github.com/epam/ai-dial) as part of a hands-on learning workshop.

This project explores how an agent can combine multiple capabilities behind a single conversational interface:

- **Web search** through a DuckDuckGo MCP server
- **Python code execution** through an MCP server
- **Image generation** through a configured model deployment
- **File content extraction** for PDF, TXT, CSV and other supported formats
- **Retrieval-Augmented Generation (RAG)** over uploaded documents

## Architecture

The agent is exposed through a DIAL application endpoint. Its tools connect to model deployments and MCP services, while Docker Compose provides the local supporting services.

![General Purpose Agent flow](agent_flow.png)

## Learning context and attribution

This repository is my personal fork of the upstream workshop project: [khshanovskyi/ai-dial-general-purpose-agent](https://github.com/khshanovskyi/ai-dial-general-purpose-agent).

I used the workshop material to practise agent design, tool integration, MCP-based services, document processing and RAG. This fork is maintained as a learning and portfolio project; the upstream repository remains the source for the original workshop structure and instructions. The fork's Git history shows changes made here.

## Technology

- Python
- EPAM DIAL / DIAL Core
- Docker Compose
- Model deployments through the DIAL adapter
- Model Context Protocol (MCP)
- RAG and document processing

## Running locally

1. Install Docker and Docker Compose, and prepare a DIAL environment with model deployments you are authorised to use.
2. Review [core/config.json](core/config.json) and replace every `YOUR_DIAL_API_ENDPOINT`, `YOUR_DIAL_API_KEY` and `YOUR_PROJECT` placeholder with values from your own DIAL environment.
3. Review [settings/settings.json](settings/settings.json). Set strong, unique encryption values and configure authentication for your environment. Do not use the sample values in production.
4. Start the supporting services with `docker compose up`.
5. Start the Python application using the instructions and dependencies in this repository, then open the local DIAL Chat instance configured for your environment.

The application and model endpoints in the sample configuration are illustrative. Adapt ports, deployment names and service URLs to match your local setup.

## Security notes

- Never commit API keys, access tokens, passwords, private endpoints or production configuration.
- The configuration files contain placeholders; supply credentials locally and keep them out of Git.
- The `test` identity-provider configuration is for local experimentation only. Configure proper JWT verification and an appropriate identity provider before exposing the service.
- Use unique secrets for DIAL encryption and authentication. Do not reuse the example values.
- Review Docker port exposure and network access before running the stack on a shared or public network.

## Repository layout

- `core/` – DIAL Core application and model configuration
- `settings/` – DIAL Core settings
- `task/` – agent application, prompts and tool implementations
- `tests/` – sample files used to exercise document-processing and RAG flows

## License and upstream

Please refer to the [upstream repository](https://github.com/khshanovskyi/ai-dial-general-purpose-agent) for the original workshop context and licensing information. This fork does not claim ownership of upstream material.
