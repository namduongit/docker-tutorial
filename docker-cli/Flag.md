**Docker control**
### Set container options
--name              :     Assign a name to the `container`

--rm                :     Automatically remove the container when it exits

--restart [policy]  :     Set the restart policy for the container
    + no                       : Do not automatically restart the container. (default)
    + on-failure[:max-retries] : Restart the container if it exits with a non-zero status, up to a maximum number of retries.   
    + always                   : Always restart the container if it stops. It only stops when you `docker rm -f` it.
    + unless-stopped           : It not restart when the container is stopped

-d, --detach        :     Run container in background and print container ID
-it, -i --tty       :     Run container in interactive mode with a TTY (CMD)

---
### Set Environment variables
-e, --env [key=value]   :     Set environment variables
--env-file [file]       :     Read in a file of environment variables

---
### Save volumes
-v, --volume [host_path:container_path[:options]]  :     Bind mount a volume
    + host_path          : Path on the host machine
    + container_path     : Path in the container
    + options            : Volume options (e.g., ro for read-only)

--mount [type=bind,source=host_path,target=container_path[,options]]  :     Attach a filesystem mount to the container
    + type               : Type of mount (e.g., bind)
    + source             : Path on the host machine
    + target             : Path in the container
    + options            : Mount options (e.g., ro for read-only)

--tmpfs [container_path[:options]]  :     Mount a temporary file system (tmpfs) inside the container
    + container_path     : Path in the container
    + options            : Tmpfs options (e.g., size=64m)

---
### Network settings
-p, --publish [host_port:container_port[/protocol]]  :     Publish a container
    + host_port          : Port on the host machine
    + container_port     : Port in the container
    + protocol           : Protocol (tcp or udp, default is tcp)

--network [network_name]  :     Connect a container to a network
    + network_name       : Name of the Docker network
    + alias              : Alias for the linked container

--link [container_name:alias]  :     Add link to another container
    + container_name     : Name of the container to link to
    + alias              : Alias for the linked container   