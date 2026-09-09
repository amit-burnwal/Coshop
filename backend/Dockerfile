#base image for node js
FROM node:22-bookworm-slim

WORKDIR /app

# copy package.json && package-lock.json
COPY package*.json ./

# Run the dependencies 
RUN npm ci  --omit=dev

COPY . .

EXPOSE 5000

CMD ["npm", "start"]
