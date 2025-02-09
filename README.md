
### **Step-by-Step Guide to Install Docker on a VM **

1. **Update the package list:**
   This step ensures that you have the latest repository information for your system's packages:
   ```
   sudo apt update
   ```

2. **Install Docker:**
   Install Docker using the `docker.io` package, which is available in the default Ubuntu repositories:
   ```
   sudo apt install docker.io -y
   ```
   - The `-y` flag automatically confirms the installation, so you don't need to manually type "yes" during the installation process.

3. **Check Docker Service Status:**
   After installing Docker, check if the Docker service is running:
   ```
   sudo systemctl status docker
   ```
   - If Docker is running, you should see "active (running)" in the status.
   - If it's inactive, you'll need to start it manually.

4. **Start Docker (if it's not running):**
   If the Docker service is not running, start it with this command:
   ```
   sudo systemctl start docker
   ```

5. **Enable Docker to Start at Boot:**
   To ensure Docker starts automatically when the system boots up, enable the Docker service:
   ```
   sudo systemctl enable docker
   ```

6. **Add the User to the Docker Group:**
   To allow your user (e.g., `devadin`) to run Docker commands without needing `sudo`, add the user to the Docker group:
   ```
   sudo usermod -aG docker devadin
   ```
   - The `-aG` option adds the user to the specified group (`docker`) without removing them from other groups.

7. **Log Out and Log Back In:**
   After adding the user to the Docker group, log out and log back in (or restart the session) for the group membership to take effect.

8. **Verify Docker Installation:**
   Once logged back in, verify that Docker is installed and working properly:
   ```
   docker --version
   ```
   This command should output the version of Docker installed.

   Then, you can run a test container to make sure everything is functioning:
   ```
   docker run hello-world
   ```
   - This command downloads a test image from Docker Hub and runs it. If successful, it will print a message saying "Hello from Docker!"

By following these steps, Docker will be installed on your VM, and your user will be able to run Docker commands without `sudo`.
----------------------------------

### Lets create a Docker Image for app.py:

Step1: Create the app.py File
Step2: Create a Dockerfile
Step3: Build the Docker Image

 ```
  docker build -t neelima/first-docker-image:latest .
   ```
The command docker build is used to build a Docker image from a Dockerfile.
-t: This flag is used to specify a tag for the image. The tag is composed of two parts:
neelima/first-docker-image: This part represents the username/repository name for the image. It's useful for pushing the image to Docker Hub or a similar registry.
:latest: This is the tag or version of the image. The latest tag is a default tag that generally refers to the most recent version of the image.
. (dot): The dot represents the current directory, which tells Docker to look for a Dockerfile in the current directory to build the image. If you are in the directory where the Dockerfile is located, this is the right place to execute the command.
Step4: Run the Docker Container:
```
docker run -it neelima/first-docker-image:latest
 ```

The docker run command runs a Docker container from the specified image.
-it: These flags allow you to run the container in interactive mode.
neelima/first-docker-image:latest: This is the name of the image you built earlier. You are telling Docker to run a container from this image.

The output of the docker run command will be the sum of the 2 numbers
``` The output 
The sum of 1.5 and 6.3 is 7.8
```






