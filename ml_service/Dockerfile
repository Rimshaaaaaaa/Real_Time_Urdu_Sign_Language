# Use Python 3.10 slim for compatibility with latest mediapipe
FROM python:3.10-slim

# Set working directory
WORKDIR /app

# Install system dependencies for OpenCV & MediaPipe
RUN apt-get update && apt-get install -y --no-install-recommends \
    build-essential \
    ffmpeg \
    libgl1 \
    libglib2.0-0 \
    libsm6 \
    libxext6 \
    libxrender1 \
    wget \
    curl \
    && rm -rf /var/lib/apt/lists/*

# Copy requirements
COPY requirements.txt .

# Upgrade pip
RUN pip install --upgrade pip

# Install compatible mediapipe first
RUN pip install mediapipe==0.10.15

# Install the rest of the requirements without reinstalling mediapipe
RUN pip install -r requirements.txt --no-deps

# Copy the entire project
COPY . /app

# Ensure Python prints logs immediately
ENV PYTHONUNBUFFERED=1

# Command to run the API
CMD ["python", "sign_model_api.py"]
