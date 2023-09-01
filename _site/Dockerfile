# Use the official Ruby image as the base image
FROM ruby:3.1-slim-bullseye

# Install required packages
RUN apt-get update && apt-get install -y --no-install-recommends \
    build-essential \
    git \
    && rm -rf /var/lib/apt/lists/*

# Install Jekyll
RUN gem update --system && gem install jekyll && gem cleanup

# Set the working directory inside the container
WORKDIR /site

# Copy the entrypoint script to the appropriate location
COPY docker-entrypoint.sh /usr/local/bin/
RUN chmod +x /usr/local/bin/docker-entrypoint.sh

# Expose port 4000
EXPOSE 4000

# Set the default command to execute when the container starts
ENTRYPOINT ["docker-entrypoint.sh"]

# Default command arguments
CMD ["bundle", "exec", "jekyll", "serve", "--force_polling", "-H", "0.0.0.0", "-P", "4000"]
