# Sobeam deployment 0.0.1

This repository ensures the continuous delivery of Sobeam, triggered by a downstream CI server upon a pull request to the development or master branch. It utilizes a multi-node setup (production and development) to connect to the target server and execute the necessary instructions for deploying Sobeam.

# Jenkins Agent:
The agent will consume resources only during the initial connection to the target server. Once the connection is established and the required JAR files are transferred, it will function as a simple SSH connection without any active processes running on the target server.

# security:
- Jenkins and target server communicate through ssh tunnels which are secure 
- Secrets are stored in jenkins as credentials and passed through the ssh tunnel

# NOTE: ( for more scalability use kubernetes ) 