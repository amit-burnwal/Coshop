# -------------- Stage 1----------------------------
# base Image
FROM dhi.io/node:26-dev AS build

# Working directory
WORKDIR /app

# Copy fron source to destination
COPY . .

# Install the dependency
RUN npm install --legacy-peer-deps

# Frontend Build
RUN npm run build

#........................Stage 1 END---------------------------------------

#----------------------Stage 2 Start ---------------------------------

# Light weight image for run the application
FROM dhi.io/node:26 AS runner

# Working Directory
WORKDIR /app

# Copying required files from builder to current stage 2
COPY --from=builder /app/dist /app/dist
COPY --from=builder /app/node_modules /app/node_modules
COPY --from=builder /app/package*.json ./
COPY ./vite.config.js ./vite.config.js


# To Run the application
CMD ["node","./node_modules/.bin/vite", "preview", "--host", "0.0.0.0", "--port", "4173"]


