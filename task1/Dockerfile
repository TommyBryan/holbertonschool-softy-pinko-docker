# Use the latest Ubuntu image
FROM ubuntu:latest

# Set the working directory to /app
WORKDIR /app

# Copy all files to the container's /app directory
COPY . /app/

# Update package lists and upgrade installed software
RUN apt-get update && apt-get upgrade -y \
    # Install python3 and python3-pip
    && apt-get install -y python3 python3-pip \
    # Remove EXTERNALLY-MANAGED if it exists to allow pip installs
    && rm -f /usr/lib/python*/EXTERNALLY-MANAGED

# Install Flask using pip3
RUN pip3 install flask

# Set the default command to run the Flask app
CMD ["python3", "api.py"]
