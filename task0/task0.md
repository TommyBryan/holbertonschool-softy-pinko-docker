# Create First Docker image

## 1. Create a Dockerfile
```Dockerfile
# Use the latest Ubuntu as the base image
FROM ubuntu:latest

# Update package lists and upgrade installed software
RUN apt-get update && apt-get upgrade -y

# Set the default command to echo "Hello, World!"
CMD ["echo", "Hello, World!"]
```
## 2. Build the Docker image
```bash
docker build -f ./Dockerfile -t softy-pinko:task0 .
```
* ``` -f ./Dockerfile ``` --> tells Docker which file to use
* ``` -t softy-pinko:task0 ``` --> Names the image ```softy-pinko``` with tag task0
* ``` . ``` --> Current directory as build context
 ## If successful, you should see output indicating the image was built successfully.
``` ruby
[+] Building 5.7s (7/7) FINISHED
 => => naming to docker.io/library/softy-pinko:task0
```
## 3. Run the Container
```bash
docker run -it --rm --name softy-pinko-task0 softy-pinko:task0
```
Expected output:
``` bash
Hello, World!
```

## 4. Verify the Image
```bash
docker images
```
You should see `softy-pinko` listed among the images.
