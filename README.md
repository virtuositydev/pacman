# pacman
Pac-Man

## Applications Components and Versions
1. WebApp: NodeJS Boron (v6.9 - v6.17)
2. Database: MongoDB 3.4

## MongoDB setup
1. Install locally or Docker, reference [MongoDB's documentation](https://www.mongodb.com/docs/manual/administration/install-community/)

## NodeJS WebApp setup
### WebApp's Configurations (Environment Variables)
1. MongoDB's hostname: MONGO_SERVICE_HOST
2. MongoDB's port: MY_MONGO_PORT
3. Other configurations, reference [config.js in this repo](lib/config.js)

### Install dependencies

```
npm install
```

### Getting started

```
npm run start
```

### Development

```
npm run dev
```

## Create Application Container Image

*This section is for reference only, familiarity with Docker is required

### Docker Container Image

The [Dockerfile](docker/Dockerfile) performs the following steps:

1. It is based on Node.js Version 6 (Boron).
2. It then copies the Pac-Man game into the configured application directory.
3. Exposes port 8080 for the web server.
4. Starts the Node.js application using `npm start`.

To build the image run:

```
docker build -t <registry>/<user>/pacman-nodejs-app -f ./docker/Dockerfile .
```

You can test the image by running:

```
docker run -p 8000:8080 <registry>/<user>/pacman-nodejs-app
```

And going to `http://localhost:8000/` to see if you get the Pac-Man game.

Once you're satisfied you can push the image to the container registry.

```
docker push <registry>/<user>/pacman-nodejs-app
```

### Building using an s2i image

```
s2i build . centos/nodejs-6-centos7 pacman
```
