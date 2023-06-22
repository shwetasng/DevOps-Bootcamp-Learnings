## Docker Images
- Docker provides four key functionalities to build images: Dockerfiles, layer caching, build context, and multi-stage builds. 
These features collectively enable users to create efficient and reproducible images for their containerized applications.
- **DOCKERFILES :** Dockerfiles are text files that contain instructions to build Docker images. They follow a declarative syntax and define a series of steps to create an image. Dockerfiles allow you to specify the base image, copy files into the image, install dependencies, configure settings, and define runtime commands.
- **LAYER CACHING :** Docker leverages layer caching during the image building process. Each instruction in a Dockerfile creates a new layer in the resulting image. Layers are reusable and can be cached to speed up subsequent builds. When a Dockerfile is modified, only the layers affected by the changes are rebuilt, while the cached layers are reused.
- Docker images have TAGS. It's important to understand the tagging mechanism of Docker.
- **Example :** When we pull python image from the registry, we pull the latest tag which is not informative enough to provide the details about the image.
- Can you tell which python version was built in the container? Though it pulls the latest version of the python but we can't tell the version by just looking at the tag.
- We built an image on top of another existing image called **BASE IMAGE**. This adds a new layer to the building of an image.
- **ALPINE** is the tinest linux image (size = 3MB in compressed form). This image allows to perform very basic linux operations and commands.
- Larger the size of the image, larger is the time it takes for its deployment.
- Images with high vulnerability is not used generally because there exists high chances to get attacked. Images with critical sovereignity is totally not used.
- **SYNK** is a CLI tool that allow to scan your image for vulnerability and generates the report.
- Medium and low vulnerability images can be used in production and development environment.
- As long as the image is tiny, it has less vulnerability.
- ALPINE, SLIM, STRETCH, BULLSEYE, JESSIE, BUSTER are the flavors of Docker linux image.
- When pulling python image from DockerHub registry, choose the image that already has pip and other components installed on it that python requires.
- When we pull an image from the registry, the image gets saved and stored on our local machine.
- **"docker inpect python"** command is used to know the layers involved to install the python image.
- To pull the specific version of the image, use TAG.
- **Example** : "docker pull python:3.9.17-slim-buster" command is executed and we know the version of the image that we pulled.

### Why version-id is divided into 3 sections?
- Divided into 3 sections as per Semantic Versioning. The 3 sections are:- MAJOR, MINOR and PATCH.
- **PATCH :** reflects change in the variable, refactoring or bug fixing. No functionality is added with these changes. Patch number increases up with these changes.
- **MINOR :** when changes introduces new functionality, MINOR increses up. If the MINOR value is changed, PATCH is set to zero.
- **MAJOR :** when we break the functionality(remove the functionality) with the change(s). Performed very carefully as update is made by breaking the changes which can even  break the system if not done carefully.
- 
- 
