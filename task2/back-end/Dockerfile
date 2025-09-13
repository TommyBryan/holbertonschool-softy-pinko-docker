# Use the latest Ubuntu image
FROM ubuntu:latest

# Set the working directory to /app
WORKDIR /app

# Copy all files to the container's /app directory
COPY . /app/

# Set environment variable for the port
ENV PORT=5252

# Update package lists and upgrade installed software
RUN apt-get update && apt-get upgrade -y \
    # Install python3 and python3-pip
    && apt-get install python3 -y \
    && apt-get install python3-pip -y

RUN pip install flask --break-system-packages

# Set the default command to run the Flask app
CMD ["python3", "api.py"]
