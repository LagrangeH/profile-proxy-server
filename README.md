# Reverse Proxy Server with Dynamic Subdomain Routing

This project implements a reverse proxy server that routes requests based on subdomains using Flask.

## Setup and Running

1. Make sure you have Docker installed on your system.

2. Clone this repository:
   ```
   git clone https://github.com/yourusername/reverse-proxy-server.git
   cd reverse-proxy-server
   ```

3. Build the Docker image:
   ```
   docker build -t reverse-proxy-server .
   ```

4. Run the container:
   ```
   docker run -p 5000:5000 reverse-proxy-server
   ```

The server will now be running on `http://localhost:5000`.

## Configuration

Edit the `config.yaml` file to add or modify subdomain routing rules. The format is:

```yaml
subdomain: "target_url"
```

For example:
```yaml
fb: "https://facebook.com/user/123324532"
tw: "https://twitter.com/username"
```

## Usage

Access the server using subdomains, e.g.:
- `http://fb.localhost:5000` will redirect to `https://facebook.com/user/123324532`
- `http://tw.localhost:5000` will redirect to `https://twitter.com/username`

Accessing the root domain or unknown subdomains will display a basic HTML page.

## Logs

Logs are stored in the `logs` directory within the container. To access logs, you can use Docker commands or mount a volume when running the container.

## HTTPS Support

To enable HTTPS, you would need to set up SSL certificates and modify the Flask application to use them. This is not implemented in the current version.

> [!NOTE]  
> For actual subdomain routing, you'll need to set up your DNS to point all subdomains to this server.
