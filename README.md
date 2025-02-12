# Welcome to Docker Collaboration Project

## Project Overview
This project is a Docker-based web application that demonstrates collaboration between peers. The main objectives are to build, modify, and publish Docker images while ensuring proper attribution and functionality.

## Key Features
- 🐳 Docker-based development environment
- 🔄 Hot-reload for CSS/JS changes
- 🤝 Peer collaboration system
- 📦 Versioned image releases

## Getting Started
To get started with this project, follow these steps:

1. **Clone the repository**:
   ```powershell
   git clone https://github.com/rozariodisalva/welcome-to-docker
   cd welcome-to-docker
   ```

2. **Build and run the application**:
   ```powershell
   docker build -t my-docker-app .
   docker run -d -p 3000:3000 --name my-app my-docker-app
   ```
   Open `http://localhost:3000` in your browser.

## Collaboration Workflow
### 1. Modify Peer Image
To collaborate with a peer's image, we started by using the base image from Yanis B:
```dockerfile
FROM yanisb27/welcome-to-docker-yanis:latest
COPY ./peer-modifications/ /app/src/
```
This step involves creating a new Dockerfile that extends the peer's image. We copy our modifications into the container, ensuring that the changes are applied on top of the peer's work.

### 2. Build & Publish
After modifying the image, we built and published it:
```powershell
docker build -f Dockerfile-collab -t collab-image .
docker tag collab-image rozariodisalva/collab-image:v1
docker push rozariodisalva/collab-image:v1
```
In this step, we build the collaborative image using the `Dockerfile-collab` file. We then tag the image with a version number and push it to Docker Hub, making it available for others to use.

## Attribution
This project is based on the original work by Yanis B. You can view his Docker Hub profile [here](https://hub.docker.com/u/yanisb27).

## Troubleshooting Guide
During development, we encountered a few common issues:
| Issue | Solution |
|-------|----------|
| CSS changes not applying | Use `docker cp` to copy the updated CSS file into the running container. |
| Port conflicts | Remove any existing containers using the same port with `docker rm -f <container_name>`. |
| Cached styles in the browser | Append a timestamp to the URL to bypass the cache, e.g., `http://localhost:3000/?t=$(Get-Date -Format 'yyyyMMddHHmmss')`. |

## Summary of Changes
Throughout this project, we made several modifications:
- Updated the CSS styles to enhance the application's appearance.
- Created an attribution file to credit the original author.
- Built a collaborative Docker image based on a peer's work.
- Resolved issues related to CSS not reflecting changes and port conflicts.

## Collaboration Process
The collaboration process involved the following steps:

1. **Forking the repository**: We forked the original repository to create a copy of the project.
2. **Creating a new branch**: We created a new branch to work on our modifications.
3. **Modifying the code**: We made changes to the code, including updating the CSS styles and creating an attribution file.
4. **Building and publishing the image**: We built and published the collaborative image using the `Dockerfile-collab` file.
5. **Merging the changes**: We merged our changes into the main branch.

## Best Practices
To ensure a smooth collaboration process, we recommend the following best practices:

* Use clear and descriptive commit messages.
* Keep the code organized and well-structured.
* Use version control to track changes.
* Test the code thoroughly before merging changes.

![Collaboration Demo](https://via.placeholder.com/800x400.png?text=Docker+Collaboration+Workflow+Demo)