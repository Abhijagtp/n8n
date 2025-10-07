FROM n8nio/base:22

# Install required packages (keep if needed for your workflows)
RUN apk add --no-cache --update openssh sudo shadow bash

# Allow node user to use sudo without password (if needed)
RUN echo "node ALL=(root) NOPASSWD:ALL" > /etc/sudoers.d/node && chmod 0440 /etc/sudoers.d/node

# Create workspaces directory for node user (if needed)
RUN mkdir /workspaces && chown node:node /workspaces

# Install pnpm globally (if needed for custom nodes)
RUN npm install -g pnpm

# Install n8n globally
RUN npm install -g n8n

# Switch to node user
USER node

# Configure pnpm store (if needed)
RUN mkdir -p ~/.pnpm-store && pnpm config set store-dir ~/.pnpm-store --global

# Expose the port for Render detection
EXPOSE $PORT

# Set default command: Clean n8n start, using env vars for port/DB
CMD ["n8n", "start"]