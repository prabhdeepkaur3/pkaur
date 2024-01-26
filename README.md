<!-- # Runnning web application using Docker -->
1.Open the Ubuntu terminal and Navigate to the directory which contains the dockerfile.

2.Now we will make the docker image in this directory using the 'docker build' command and '-t' flag to tag the image with specified name which is 'kaur_prabhdeep_coding_assignment11' in this case. We will end this command with '.' to build it in the same directory. Hence the command would be ' docker build -t kaur_prabhdeep_coding_assignment11 .'

This step will create a docker image named 'kaur_prabhdeep_coding_assignment11' using the dockerfile in the current directory.

3.After creating the docker image we will run the docker container using 'docker run' command to run the container from the image that we created in the 2nd step(kaur_prabhdeep_coding_assignment11).
We will use the 'p' flag to map ports between the host machine nad container. In this case the host port is 7775 and the port that is mapped on container is 3000. After this we will write the name of the image 'kaur_prabhdeep_coding_assignment11'.The command would be 'docker run -p 7775:3000 kaur_prabhdeep_coding_assignment11'.
This will start the docker container based on the 'kaur_prabhdeep_coding_assignment11' image, and will map the post 7775 from host to port3000 in the containner.

4.Now we can open any of the web browser and search 'localhost:7775'. It will display the web application that we created using the react.

<!-- content of dockerfile -->
Dockerfile:
 1.In the dockerfile the first command is 'FROM node:13.12.0-alpine' this specifies the docker image. It uses the official Node.js image with the version 13.12.0 based on Alpine which is a lightweight Linux distribution, which results in smaller docker images. 

 2.The second command is 'WORKDIR /kaur_prabhdeep_coding_assignment11'. In this command thee WORKDIR sets the working directory for the subsequent instructions in the dockerfile. This is the place where the application code will be placed inside teh docker file.

 3.After this we run this command 'ENV PATH /app/node_modules/.bin:$PATH'.This adds the /app/node_modules/.bin directory to the system's PATH environment variable. It is used to include the local binary directories in the PATH so that the npm scripts installed locally can be executed easily.

 4.Next command is 'COPY package.json ./
COPY package-lock.json ./
RUN npm install --silent
RUN npm install react-scripts@3.4.1 -g --silent'. These line of code copy the package.json and package-lock.json files into the container and then it installs the Node.js dependencies for the application using npm install. The --silent flag is used to suppress unnecessary output during the installation process. Additionally, it installs the react-scripts globally, it is done when working with Create React App.

5.'COPY . ./', this code copies the entire content of local project directory into the working directory of the docker container which is 'kaur_prabhdeep_coding_assignment11'

6.'EXPOSE 3000', This line tells the docker that the container will listen on port 3000 during runtime.

7.'CMD ["npm", "start"]', This line contians the command to run when the container starts. In this case, it runs the npm script "start" which typically starts the development server for the React application.