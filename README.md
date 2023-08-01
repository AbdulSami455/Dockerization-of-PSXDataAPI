# Dockerization-of-PSXDataAPI
#Original Repo Of API Project is 

https://github.com/AbdulSami455/PSX-Data-Api

𝐖𝐡𝐚𝐭 𝐢𝐬 𝐃𝐨𝐜𝐤𝐞𝐫𝐢𝐳𝐚𝐭𝐢𝐨𝐧?
Dockerization is the process of Packaging, Deploying, and running your application. This process is done in a docker container. 
Docker is an Open-Source tool that ships your application with all functionalities as one package. You can use docker to pack your application with everything 
you need to run your application and ship it as one package. 

There are two parts of Docker 
1. Docker Engine
2. Docker Hub

𝑾𝒉𝒚 𝒚𝒐𝒖 𝒏𝒆𝒆𝒅 𝒅𝒐𝒄𝒌𝒆𝒓?
In order to Understand the need for docker, you first need to understand the need for containerization and what is really containerization is?


𝑪𝒐𝒏𝒕𝒂𝒊𝒏𝒆𝒓𝒊𝒛𝒂𝒕𝒊𝒐𝒏?
Containerization is a lightweight virtualization technology that allows you to package an application and all its dependencies, libraries, and configurations into a single container image. This container can then be deployed and run consistently across different environments without worrying about any compatibility issues. Containers provide isolation, ensuring that the application runs in the same way, regardless of the host system.


Advantages of containerization include:

𝑷𝒐𝒓𝒕𝒂𝒃𝒊𝒍𝒊𝒕𝒚:
Containers can run on any platform or cloud infrastructure that supports container runtimes, making it easy to move applications between different environments

𝑰𝒔𝒐𝒍𝒂𝒕𝒊𝒐𝒏:
Containers provide isolation between applications and the host system, preventing potential conflicts and ensuring security.


𝑹𝒆𝒔𝒐𝒖𝒓𝒄𝒆 𝑬𝒇𝒇𝒊𝒄𝒊𝒆𝒏𝒄𝒚:
Containers are lightweight and share the host OS kernel, so they consume fewer resources compared to traditional virtual machines.


𝑺𝒄𝒂𝒍𝒂𝒃𝒊𝒍𝒊𝒕𝒚:
Containers can be easily scaled up or down to accommodate varying workloads and demands.


𝗦𝘁𝗲𝗽𝘀 𝘁𝗼 𝗗𝗼𝗰𝗸𝗲𝗿𝗶𝘇𝗲 𝗙𝗮𝘀𝘁𝗔𝗣𝗜


Step 1:

𝗗𝗼𝗰𝗸𝗲𝗿𝗳𝗶𝗹𝗲
 Create a Dockerfile in the root directory of your FastAPI project. This file defines the steps to build a Docker image for your application.


 # Use the official Python base image
FROM python:3.9-slim

# Set the working directory inside the container
WORKDIR /app

# Copy the requirements.txt file and install dependencies
COPY requirements.txt .
RUN pip install --no-cache-dir -r requirements.txt

# Copy the FastAPI application files to the container's working directory
COPY . .

# Expose the port on which the FastAPI application will run
EXPOSE 8000

# Command to start the FastAPI application
CMD ["uvicorn", "main:app", "--host", "0.0.0.0", "--port", "8000"]

𝑺𝒕𝒆𝒑 2:

requirements.txt: Create a requirements.txt file in the root directory of your project. This file should list all the Python dependencies required for your FastAPI application to run.

𝑺𝒕𝒆𝒑 3:

𝑩𝒖𝒊𝒍𝒅 𝑫𝒐𝒄𝒌𝒆𝒓 𝑰𝒎𝒂𝒈𝒆

Open a terminal or command prompt, navigate to the root directory of your FastAPI project, and run the following command to build the Docker image:

docker build -t fastapi-app .

𝒔𝒕𝒆𝒑 4:

𝑹𝒖𝒏 𝒕𝒉𝒆 𝑫𝒐𝒄𝒌𝒆𝒓 𝑪𝒐𝒏𝒕𝒂𝒊𝒏𝒆𝒓:

After successfully building the Docker image, you can run the FastAPI application in a Docker container using the following command:

docker run -d -p 8000:8000 fastapi-app















