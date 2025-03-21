# Job Manager

### Prerequisites

* Go (v1.23.3 or higher)
* MongoDB
* Docker

### Building and Running Locally

1. Clone the repository:

```sh
git clone https://github.com/yourusername/Job-Manager-Adapter.git
cd Job-Manager-Adapter/bpp/backend
```

2. Create a `.env` file in the root directory and add your environment variables.

```sh
DB_SERVER=<mongo-db-server-address>
DB_USER=<mongo-db-username>
DB_PASSWORD=<mongo-db-password>
BPP_ID=<bpp-id>
BPP_URI=<bpp-uri>
```

3. Start the development server:

```sh
export $(cat .env | xargs) && go run main.go
```

5. The server should now be running at `http://localhost:8080`.

### Deploying Using Docker

1. Build the Go program

```sh
go build -o bpp main.go
```

2. Update the Makefile

```makefile
DOCKER_REGISTRY ?= <docker-registry>
DOCKER_REPO ?= <docker-repo>
DOCKER_IMAGE ?= bpp
DOCKER_TAG ?= <image-tag>
```

3. Build the docker image

```sh
make build-amd64
```

3. Run the docker image container

```sh
docker run --env-file ./.env -p 8080:8080 <docker-repo>/bpp:<image-tag>
```
