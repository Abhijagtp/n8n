FROM n8nio/base:22

# Install required packages
RUN apk add --no-cache --update openssh sudo shadow bash

# Allow node user to use sudo without password
RUN echo "node ALL=(root) NOPASSWD:ALL" > /etc/sudoers.d/node && chmod 0440 /etc/sudoers.d/node

# Create workspaces directory for node user
RUN mkdir /workspaces && chown node:node /workspaces

# Install pnpm globally
RUN npm install -g pnpm

# Install n8n globally
RUN npm install -g n8n

# Switch to node user
USER node

# Configure pnpm store
RUN mkdir -p ~/.pnpm-store && pnpm config set store-dir ~/.pnpm-store --global

# Set default command to start n8n
CMD ["n8n"]
