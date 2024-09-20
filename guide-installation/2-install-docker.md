# Docker Installation Guide

## What is Docker?

Docker is a platform for developing, shipping, and running applications in containers. Containers are lightweight, standalone, executable packages that include everything needed to run a piece of software, including the code, runtime, system tools, libraries, and settings.

Key benefits of Docker:
1. Consistency: Ensures that applications work the same in development, testing, and production environments.
2. Isolation: Keeps applications and their dependencies separate from the host system and other containers.
3. Portability: Allows applications to run on any system that supports Docker, regardless of the underlying operating system.
4. Efficiency: Uses fewer resources than traditional virtual machines.

## Installation Guide

### Windows

1. System Requirements:
   - Windows 10 64-bit: Pro, Enterprise, or Education (Build 16299 or later)
   - Hyper-V and Containers Windows features must be enabled

2. Download Docker Desktop for Windows:
   - Visit [Docker Desktop for Windows](https://www.docker.com/products/docker-desktop)
   - Click "Download for Windows"

3. Install Docker Desktop:
   - Double-click the installer file
   - Follow the installation wizard
   - When prompted, ensure "Use WSL 2 instead of Hyper-V" is selected

4. Start Docker Desktop:
   - Search for Docker in the Start menu and launch it
   - Wait for Docker to start (you'll see a whale icon in the taskbar)

5. Verify installation:
   - Open a command prompt
   - Run `docker --version` to check the installed version
   - Run `docker run hello-world` to verify Docker can pull and run images

### macOS

1. System Requirements:
   - macOS 10.14 (Mojave) or newer

2. Download Docker Desktop for Mac:
   - Visit [Docker Desktop for Mac](https://www.docker.com/products/docker-desktop)
   - Click "Download for Mac"

3. Install Docker Desktop:
   - Double-click the .dmg file
   - Drag the Docker icon to the Applications folder

4. Start Docker Desktop:
   - Open Docker from the Applications folder
   - Wait for Docker to start (you'll see a whale icon in the menu bar)

5. Verify installation:
   - Open Terminal
   - Run `docker --version` to check the installed version
   - Run `docker run hello-world` to verify Docker can pull and run images

### Linux (Ubuntu)

1. Update package index:
   ```
   sudo apt-get update
   ```

2. Install prerequisites:
   ```
   sudo apt-get install apt-transport-https ca-certificates curl software-properties-common
   ```

3. Add Docker's official GPG key:
   ```
   curl -fsSL https://download.docker.com/linux/ubuntu/gpg | sudo apt-key add -
   ```

4. Set up the stable repository:
   ```
   sudo add-apt-repository "deb [arch=amd64] https://download.docker.com/linux/ubuntu $(lsb_release -cs) stable"
   ```

5. Update package index again:
   ```
   sudo apt-get update
   ```

6. Install Docker CE:
   ```
   sudo apt-get install docker-ce
   ```

7. Verify installation:
   - Run `docker --version` to check the installed version
   - Run `sudo docker run hello-world` to verify Docker can pull and run images

## Post-Installation Steps

1. Create a Docker Hub account:
   - Visit [Docker Hub](https://hub.docker.com/) and sign up
   - This allows you to push and pull images from Docker Hub

2. Familiarize yourself with basic Docker commands:
   - `docker pull`: Download an image from Docker Hub
   - `docker run`: Create and start a container
   - `docker ps`: List running containers
   - `docker images`: List downloaded images
   - `docker build`: Build an image from a Dockerfile

3. Try running a simple web server:
   ```
   docker run -d -p 80:80 nginx
   ```
   This command runs an Nginx web server in a container. Visit `http://localhost` in your browser to see it in action.

## Troubleshooting

- If you encounter permission issues on Linux, you may need to add your user to the docker group:
  ```
  sudo usermod -aG docker $USER
  ```
  Log out and back in for this to take effect.

- On Windows, ensure Hyper-V is enabled if you're not using WSL 2.

- If Docker fails to start, check system requirements and ensure virtualization is enabled in BIOS.

For more detailed troubleshooting, refer to the [official Docker documentation](https://docs.docker.com/).