# Use Python 3.10 slim for compatibility
FROM python:3.10-slim

# Set working directory
WORKDIR /app

# Install system dependencies for OpenCV, MediaPipe, and general ML libraries
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

# Upgrade pip and install Python dependencies
RUN pip install --upgrade pip
RUN pip install -r requirements.txt

# Copy the rest of the application code
COPY . /app

# Ensure Python prints logs immediately (good for Render logs)
ENV PYTHONUNBUFFERED=1

# Expose port if your Flask API runs on default 5000
EXPOSE 5000

# Default command to run your API
CMD ["python", "sign_model_api.py"]
