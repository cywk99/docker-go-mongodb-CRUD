# Pull base image
FROM golang:1.14.0-stretch

# Where our file will be in the docker container 
WORKDIR /opt/go-app
# Install git
RUN apt update && apt upgrade -y && \
    apt install -y git \
    make openssh-client
# Copy the source from the current directory to the working 
# Directory inside the container 
# Source also contains go.mod and go.sum which are dependency files
COPY . .

# Get Dependency
RUN go mod download
# Install Air for hot reload
RUN curl -fLo install.sh https://raw.githubusercontent.com/cosmtrek/air/master/install.sh \
    && chmod +x install.sh && sh install.sh && cp ./bin/air /bin/air
# The ENTRYPOINT defines the command that will be ran when the 
# container starts up
# In this case air command for hot reload go apps on file changes

# CMD ["go","run","."]
# RUN air init

CMD air