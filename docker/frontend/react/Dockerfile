#Here we will use node as the base image.
FROM node:latest

#create a working directory inside the container.
WORKDIR /app

#ENV NODE_ENV=production

#copy the files from the host to the container.
COPY ["package.json", "package-lock.json*", "./"]

RUN npm install

COPY . .

CMD [ "npm", "start" ]