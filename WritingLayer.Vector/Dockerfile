# This tells Docker to use Python 3.14
FROM python:3.14-slim

# Set the working directory in the container to /app
WORKDIR /app

# Install system dependencies that are required for some Python packages.
RUN apt-get update && apt-get install -y \
    build-essential \
    curl \
    && rm -rf /var/lib/apt/lists/*

# This copies the list of dependencies to the container and installs them.
COPY requirements.txt .
RUN pip install --no-cache-dir -r requirements.txt

# This copies the rest of the application code to the container.
COPY . .

# Expose port 8000 for the application to be accessible outside the container.
EXPOSE 8000

# Start the application using the command specified in main.py.
CMD ["python", "main.py"]