# here you can define you base file
# we have to specify the image:tag, for sure this image in docker hub
# go to docker hub and find the suitable base image and tag
FROM python:latest

# here we should set the working directory inside container
# in this path inside container , docker will store all your source files

WORKDIR /app

# now it is time to tell your will expose your container service in which port
# in our case we are using flask and we expose in 5050
EXPOSE 5050

# we need to copy the file which has the dependancies to container
# . here refer to /app because we already set with WWOKDIR as root path
COPY Pipfile ./
COPY Pipfile.lock ./
# COPY Pipfile Pipfile.lock ./

# now it is the time to install dependencies, which will make new layer on base image
# in our case we have pipfile which contain all dependencies needed
# we do not need to make venv because container only run this service
RUN pip install pipenv

# here this command will copy all dapendencies Pipfile and Pipfile.lock to requirements
RUN pipenv lock --requirements > requirements.txt

# now this will install all dependencies in requirments file
RUN pip install -r requirements.txt

# now we need to copy all remaining file to container

COPY . ./

# you can make another directory to map later if needed
# MKDIR data

# now excute command for you container we decide which command python
# no need to specify verion because only one image here
# and main file

CMD ["python","main.py"]