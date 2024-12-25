# Lab3

This repository contains the necessary files and instructions to build a Docker image, run it in a container, and expose the application running inside the container on GitHub Codespaces. The application will be accessible publicly via the Codespaces server port.

---

## Prerequisites

Before you begin, ensure you have the following:

- A GitHub account with access to Codespaces.
- Docker installed in your Codespaces environment (pre-installed in most cases).

---

## Steps to Build and Run the Docker Image

### 1. Clone the Repository

Start by cloning this repository into your GitHub Codespace:

```bash
git clone https://github.com/kshitijdhara/Lab3.git
cd Lab3
```

---

### 2. Build the Docker Image

Use the provided `Dockerfile` to build the Docker image. Run the following command in your Codespace terminal:

```bash
docker build -t lab3-image .
```

Here:
- `lab3-image` is the name/tag for the Docker image.

---

### 3. Run the Docker Container

Once the image is built, run a container from it, exposing the application on a specific port. Use this command:

```bash
docker run -d -p 8080:8080 lab3-image
```

Here:
- `-d` runs the container in detached mode.
- `-p 8080:8080` maps port 8080 on the container to port 8080 on the Codespaces server.
- `lab3-image` is the name of the image built in Step 2.

---

### 4. Access the Application

GitHub Codespaces automatically makes exposed ports accessible publicly. To access your application:

1. In your Codespace, click on **Ports** in the bottom panel.
2. Locate port `8080` in the list of forwarded ports.
3. Click on the URL under **Local Address** to open your application in a browser.

If you want to make sure it's publicly accessible, ensure that port `8080` is marked as **Public** in the Ports tab.

---

## Notes

- Replace `8080` with another port if your application uses a different one. Update both the `Dockerfile` (if needed) and `docker run` command accordingly.
- Ensure that your application is configured to listen on all interfaces (e.g., `0.0.0.0`) so it can be accessed externally.

---

## Troubleshooting

- If you cannot access your application, verify that:
  - The container is running: `docker ps`
  - The correct port is exposed and mapped.
  - The application inside the container is running as expected.
- Check for errors in container logs using:
  ```bash
  docker logs <container_id>
  ```

---

Feel free to reach out if you encounter any issues or need further assistance!
