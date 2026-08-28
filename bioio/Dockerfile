# Base image for Python 3.12
FROM python:3.12-slim

# Set up a working directory
WORKDIR /app

# Copy requirements file
COPY requirements.txt ./

# Create and activate a virtual environment, then install dependencies
RUN apt-get update && apt-get install -y --no-install-recommends procps && \
    python -m venv /venv && \
    /venv/bin/pip install --no-cache-dir -r requirements.txt && \
    rm -rf /var/lib/apt/lists/* /root/.cache/pip requirements.txt

# Set environment variables
ENV PATH="/venv/bin:$PATH"
