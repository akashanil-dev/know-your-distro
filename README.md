# **Know Your Distro – Docker Setup Guide**

This guide explains how to run the **Know Your Distro** game using Docker.

---

## **Step 0: Get the Game Files**

### **Option A — Clone the Repository**

```bash
git clone https://github.com/akashanil-dev/know-your-distro
cd know-your-distro
```

### **Option B — Download ZIP**

Download the ZIP directly:
[https://github.com/akashanil-dev/know-your-distro/archive/refs/heads/master.zip](https://github.com/akashanil-dev/know-your-distro/archive/refs/heads/master.zip)

Extract the ZIP and open the folder.

---

## **Step 1: Open Terminal**

Open **PowerShell** or **Command Prompt** and navigate to the project folder.

Example:

```powershell
cd C:\Users\YourName\Downloads\know-your-distro
```

You should see `index.html` when running:

```powershell
ls
```

---

## **Step 2: Create the Dockerfile**

Create a file named **Dockerfile** (no extension).

PowerShell:

```powershell
New-Item Dockerfile -type file
```

Open the file in Notepad or VS Code and paste the following:

```dockerfile
# Use a lightweight Nginx image as the base
FROM nginx:alpine

# Copy all files from the current Windows directory to the Nginx html directory
COPY . /usr/share/nginx/html

# Expose port 80 (this is the port Nginx listens on inside the container)
EXPOSE 80
```

Save the file.

---

## **Step 3: Build the Docker Image**

Build the Docker image using:

```powershell
docker build -t linux-runner-game .
```

---

## **Step 4: Run the Container**

Start the container:

```powershell
docker run -d -p 8080:80 --name my-game linux-runner-game
```

---

## **Step 5: Play the Game**

Open your web browser and visit:

```
http://localhost:8080
```

---

## **Useful Commands**

Stop the container:

```powershell
docker stop my-game
```

Remove the container:

```powershell
docker rm my-game
```

Remove the image:

```powershell
docker rmi linux-runner-game
```

---
