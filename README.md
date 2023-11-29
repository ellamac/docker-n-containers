# Practice 4 - Docker and containers

Let's create a Docker contains from an Node.js web application. In this practice, you will learn about creating Docker containers and
running them. Along the way, you will learn about the Express.js web development framework.

Requirements:
- Docker
- Recent Node.js installation.

Steps to complete:

1. Create a simple Express.js web application. It can be super simple, or more complicated if you like.
   Make sure you can see it in your browser before moving forward.
   See instructions from http://expressjs.com/en/starter/hello-world.html

2. Create a "dockerfile" for this application. This is the main configuration file for Docker, and has to be named like that.
   You can find lots of examples from the Internet, or you can use the below dockerfile as an example.

3. Create a Docker image using the "docker build" command.

4. Run your container with "docker run", for example: "docker run -p 3000:3000 your-express-app"

5. Access the application using your web browser, for example "http://localhost:3000".

----------------
Example "dockerfile" for Node.js/ExpressJS use:

# Use an official Node.js runtime as a parent image
FROM node:latest

# Set the working directory in the container
WORKDIR /usr/src/app

# Copy package.json and package-lock.json (if available)
COPY package*.json ./

# Install any dependencies
RUN npm install

# Bundle your app's source code inside the Docker image
COPY . .

# Your app binds to port 3000 so you'll use the EXPOSE instruction to have it mapped by the docker daemon
EXPOSE 3000

# Define the command to run your app
CMD [ "npm", "start" ]
