# NodeJS Microservice with Docker

## Creating the app

The app creates a server with `Express` that has a single
endpoint `/api/user/:username`. When a `GET` request reaches that endpoint,
we go and fetch the given `username`s `json` feed from Instagram and send it
back as an response.

``` bash
yarn install
yarn start
```

Navigate to [`http://localhost:8080/api/user/instagram`](http://localhost:8080/api/user/instagram)
should show Instagram's public feed as JSON.


## Creating a Dockerfile

The `Dockerfile` takes the `node:latest` base image,
copy some files in, install dependencies, expose a port and run 
the start command. Create a file called `Dockerfile` to the root of your project
and add the following set of commands to that file:

Now we can build the image with `docker build`:

``` bash
docker build -t nodejs-microservice-docker .
```

and then run it with `docker run`

```
docker run -it -p 8080:8080 nodejs-microservice-docker
```

### List all containers (only IDs)
``` bash
docker ps -aq
```

###Stop all running containers
``` bash
docker stop $(docker ps -aq)
```

###Remove all containers
``` bash
docker rm $(docker ps -aq)
```

###Remove all images
``` bash
docker rmi $(docker images -q)
```

## License

MIT
