# secure-ollama-server

This repo contains a simple autheticated version of the ollama server.

Authentication is done using Caddy.

## How to Use

In order to use this package, perform the following actions:

1. Create a `.env` file using the same format as the provided `.env.template`. Add your required username and password there.

2. Start the ollama server.

### Starting the ollama server

**Option 1: With gpu support**

```sh
docker compose -f docker-compose.yaml -f docker-compose.gpu.yaml up -d
```

**Option 2: Cpu only**
```sh
docker compose -f docker-compose.yaml -f docker-compose.gpu.yaml up -d
```

### Using the password protected ollama server

In order to use the server, we have to add the username and the password we specified in the `.env` file (separated by `:`). An example in curl can be seen bellow:

```sh
curl -u user:password 127.0.0.1:8200/api/generate -d '{"model" : "phi", "prompt" : "Is the sky green?", "stream" : false}'
```

**Note**: The port for accessing the server is `8200` as it's specified in docker-compose.yaml