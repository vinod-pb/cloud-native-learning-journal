Write 3 key differences between VM and container in your own words 

#VM  
       - Run on Hypervisor (e.g., VMware, Hyper-V)
       - Won't share the host os, have the own isolation OS
       - Each VM has its **own full OS kernel + libraries**.
       - **Heavyweight** (GBs in size, long boot times).
        
#Container
        -  light weight (MBs in size, start in seconds)., share the host os kernel
         -  manage container life cycle  with #K8
         -  Run on container run time #docker #conatinerd

  Why are containers more lightweight than VMs?
    containers, No need to bundle a full OS itself and its stateless processes
   What role does the image play in container lifecycle?
    - **Blueprint** for a container: contains app code + dependencies.
     - Life cycle
     -    **Build** → Create image from Dockerfile.
     -    **Ship** → Push to registry (Docker Hub, ECR, etc.).
     -    **Run** → Container runtime pulls & runs the image.
     
### [[12-Factor App]] Tie-In (Statelessness)

- Factor VI: **Processes** → Apps run as **stateless processes**.    
- #Containers embody this:    
    - Store **state externally** (DB, cache, object storage).        
    - Enables **[[scale up/down]]** easily.        
    - Improves **[[resilience]]** (failed container can be replaced).

[[Inspect & Manage Images]]

`docker pull <image>         # Download image from registry`
`docker images               # List local images`
`docker history <image>      # Show image layers`
`docker rmi <image>          # Remove an image`

[[Run Containers]]

`docker run hello-world      # Run test container`
`docker run -it ubuntu bash  # Run interactively inside Ubuntu`
`docker run -d -p 8080:80 nginx   # Run Nginx, map port 8080→80`
`docker run --name myapp myimage:1.0   # Run container with name`
`docker run -e ENV=dev myapp:1.0       # Pass env variables`


[[Manage Containers]]
`docker ps                   # List running containers`
`docker ps -a                # List all (including stopped)`
`docker stop <container_id>  # Stop a container`
`docker rm <container_id>    # Remove a container`
`docker logs <container_id>  # View logs`
`docker exec -it <container_id> bash   # Exec into running container`

### Reflection Questions (Day 2)

1. In your own words: **How are containers different from VMs?**
	  Containers are lightweight processes running on a container runtime (Docker, containerd) that share the host OS kernel. VMs each need their own full OS, which makes them heavier.    
2. Why do cloud-native apps prefer **stateless containers**?
	Stateless containers allow easy scaling and resilience because any instance can be killed or replaced without losing state (state is externalized).    
3. What role does a **Docker image** play in the container lifecycle?
	A Docker image is the **blueprint** for containers. You build it, push it to a registry, and then pull it to run containers consistently anywhere.    
4. Suppose your container crashes — how do you recover the application state?
      If a container crashes, the state is not inside it — it must be recovered from external storage (database, persistent volume, object storage, etc.).
5. When you run `docker run -p 8080:80 nginx`, what does the **port mapping** mean?
       `-p 8080:80` maps **container’s port 80** (Nginx webserver) to **host’s port 8080**. So you reach the container service via `http://localhost:8080`.
6. Why does Docker use **layers** when building images?
    Docker uses layers to speed up builds and save storage. Each Dockerfile step is cached; if one layer changes, only that and the ones after it rebuild.
