# Run
## LHS:RHS
`80:3000` open image's port 3000 as 80 at my side
## container name
always the right most argument to the cmd line
## arguments

# Dockerfile
## FROM
Base image to inherit
## LABEL
a comment, doesn't consume a layer
### EXPOSE
just a comment, same as label
## RUN
execute in container during setup
`docker build -t my-ubuntu:1.0 .` --- `# . is current path`
## CMD
default run command, can be changed with docker run on runtime
### ENTRYPOINT
same as CMD but cannot be changed during runtime
## ENV
expose var variable
## VOLUME
specifying VOLUME in the Dockerfile is not just uncommon, but it's probably a best practice to never use VOLUME. For two reasons. The first reason we have already identified: We can not specify the host path - which is a good thing because Dockerfiles should be very agnostic to the specifics of a host machine. But the second reason is people might forget to use the --rm option when running the container. One might remember to remove the container but forget to remove the volume. Plus, even with the best of human memory, it might be a daunting task to figure out which of all anonymous volumes are safe to remove.
# Commands
## build
```bash
cd (where Dockerfile)
docker build -t <app_name> .
```
