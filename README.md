# HOW TO

I will describe how to test, build, deploy, and run the docker-compose

## Requirements
- Installing `docker`
- I used Windows 10 x64

## Files

The folder contains 7 files
- `docker-compose.yml` This is the main file for managing Docker containers. I created 4 services including `hello1`, `hello2`, `nginx-proxy` and `redis`. 
`hello1` and `hello2` services will run in port 8000 with `Dockerfile` and also run command `node hello-1` and `node hello-2` which will run `hello-1.js` and `hello-2.js` respectively.
`nginx-proxy` contains main configuration of nginx which is inside folder `./nginx`. This will run in port 80. You can open your browser to [http://localhost](http://localhost).
`redis` is the redis image, and it will run redis command to start redis server.
- `Dockerfile` 
- `hello-1.js` and `hello-2.js` This files are not changed from the homework.
- `package.json` contains dependencies to be installed including `express` and `redis`
- `Jenkinsfile`
- `./nginx/Dockerfile` has Dockerfile to be run by `nginx-proxy` service. It will just install nginx and put `./nginx/nginx.conf` into `/etc/nginx/conf.d/default.conf` which is the directory for default configuration of nginx.
- `./nginx/nginx.conf` contains main configutation for nginx. It will listen to port 80 (which you can just simply open browser to [http://localhost](http://localhost)), and it will route to specified files for `hello-1.js` and `hello-2.js` using path.

## How to run it

After installing `docker`, `docker-compose`, you can simply run `docker-compose up --build` in the root directory of this folder.

## How to test it

You can now open the browser [http://localhost/](http://localhost). And go to the following routes
- `hello-1.js` use [http://localhost/hello1](http://localhost/hello1). This will route to `http://hello1:8000/hello1/` which is port 8000 that `hello-1.js` is ready to be connected
- `hello-2.js` use [http://localhost/hello2](http://localhost/hello2). This will route to `http://hello2:8000/hello2/` which is port 8000 that `hello-2.js` is ready to be connected
And then you can check the console that you run docker for the result.
