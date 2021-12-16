# Run
## LHS:RHS
`80:3000` open image's port 3000 as 80 at my side
## container name
always the right most argument to the cmd line
## arguments

# Build layers
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
