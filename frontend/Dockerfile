# -------------- Stage 1----------------------------
# base Image
FROM node:20-alpine

# Working directory
WORKDIR /app

# Copy fron source to destination
COPY . .

# Install the dependency
RUN npm install --legacy-peer-deps

# Frontend Build
RUN npm run build

# Run the application
CMD ["npm","run","preview"]
