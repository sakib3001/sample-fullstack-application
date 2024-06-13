# This is the base image used 
FROM node:18-alpine

# The working dir for the to-do app 
WORKDIR /app

# Copy all the package.json 
COPY package*.json .

#  Install the required things to run the frontend 
RUN npm install 

# Exposing a port 
EXPOSE 3000 

# Run the frontend 
CMD ["npm","run","dev"]