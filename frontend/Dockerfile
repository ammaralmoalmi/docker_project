# here you can define you base file
# we have to specify the image:tag, for sure this image in docker hub
# go to docker hub and find the suitable base image and tag
FROM node:15.14-alpine
# here we should set the working directory inside container
# in this path inside container , docker will store all your source files

WORKDIR /app

# now it is time to tell your will expose your container service in which port
# in our case we are using flask and we expose in 5050
EXPOSE 3000

# RUN npm install
# we need to copy the file which has the dependancies to container
# . here refer to /app because we already set with WWOKDIR as root path
COPY package.json package-lock.json ./
# package-lock.json


# now it is the time to install dependencies, which will make new layer on base image
# in our case we have package.json which contain all dependencies needed
# we do not need to make venv because container only run this service
RUN npm install --silent

RUN npx browserslist@latest --update-db
# now we need to copy all remaining file to container

COPY . ./


# you can make another directory to map later if needed
# MKDIR data

# now excute command for you container we decide which command node
# no need to specify verion because only one image here
# npm is the service , start is the service
# RUN chown -R node:node /app/node_modules
# RUN sudo chmod -R 777 /app/node_modules
CMD ["npm", "start"]