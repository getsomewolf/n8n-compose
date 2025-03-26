# n8n-compose

A Docker Compose setup for running n8n workflow automation with Traefik as a reverse proxy.

## Description

This project provides a ready-to-use Docker Compose configuration for n8n that works both in local development and production environments. It uses Traefik as a reverse proxy to handle routing and optional TLS certificate management.

## Prerequisites

- Docker and Docker Compose installed
- Basic understanding of Docker concepts
- Domain name (for production deployment)

## Quick Start

1. Clone this repository:
    ```bash
    git clone https://github.com/getsomewolf/n8n-compose.git
    cd n8n-compose
    ```

2. Configure the environment:
    ```bash
    # Copy and modify the example .env file
    cp .env.example .env  # (if not already present)
    # Edit .env to match your requirements
    ```

3. Start the services:
    ```bash
    docker-compose up -d
    ```

4. Access n8n at: http://n8n.localhost (for local development)

## Windows Hosts Configuration

To use the `.localhost` domain on Windows, you need to add it to your hosts file:

1. Open Notepad as Administrator (right-click Notepad and select "Run as administrator")
2. Open the file: `C:\Windows\System32\drivers\etc\hosts`
3. Add the following line at the end of the file:
    ```
    127.0.0.1    n8n.localhost
    ```
4. Save the file and close Notepad
5. You may need to flush your DNS cache by running `ipconfig /flushdns` in Command Prompt

Now you'll be able to access the n8n interface at http://n8n.localhost in your browser.

## Configuration

The following environment variables can be configured in the `.env` file:

| Variable | Description | Default |
|----------|-------------|---------|
| SUBDOMAIN | Subdomain for n8n | n8n |
| DOMAIN_NAME | Domain name | localhost |
| GENERIC_TIMEZONE | Timezone for n8n | UTC |
| PROTOCOL | HTTP protocol | http |
| ENABLE_TLS | Enable HTTPS | false |
| SSL_EMAIL | Email for Let's Encrypt | your@email.com |

### Local Development

For local development, use:
```
DOMAIN_NAME=localhost
PROTOCOL=http
ENABLE_TLS=false
```

### Production Deployment

For production, uncomment and set these values:
```
DOMAIN_NAME=yourdomain.com
PROTOCOL=https
ENABLE_TLS=true
SSL_EMAIL=your@email.com
```

## Project Structure

```
n8n-compose/
├── docker-compose.yml    # Docker Compose configuration
├── .env                  # Environment variables
├── local-files/          # Directory mounted to n8n container
└── LICENSE               # Apache 2.0 License
```

## Customization

You can customize the n8n instance by modifying the environment variables in the `docker-compose.yml` file or by adding additional services as needed.

## License

This project is licensed under the Apache License 2.0 - see the [LICENSE](LICENSE) file for details.
