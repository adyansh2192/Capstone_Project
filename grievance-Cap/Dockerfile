# Base image
FROM node:18

# Set working directory
WORKDIR /app

# Copy package files first (better caching)
COPY package*.json ./

# Install dependencies
RUN npm install

# Copy the rest of the app
COPY . .

# --- Datadog Config ---
# Environment variables for Datadog Agent
ENV DD_API_KEY=3c09566c85aeeefb491439ff72289b54
ENV DD_SITE=datadoghq.com
ENV DD_LOGS_ENABLED=true
ENV DD_APM_ENABLED=true
ENV DD_ENV=dev
ENV DD_SERVICE=grievance-portal
ENV DD_VERSION=1.0.0

# Expose backend port
EXPOSE 3001

# Start app with Datadog tracing
CMD ["node", "-r", "dd-trace/init", "app.js"]
