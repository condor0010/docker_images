If you need help with the installation of docker click here.
Keep in mind that the instructions are tailored for the CSE1001 course, but the steps will be the same. 

Pull/run commands:
These commands include the bind/mount of a folder from the docker to your host computer. You can remove '-v' and the file path following it if you don't want to do that, and you can add -rm after run if you'd like the container to remove itself after every time you use it.

Windows: 
```
docker run -v "$(PWD):/root/workspace" --cap-add=SYS_PTRACE --cap-add=SYS_ADMIN --cap-add=audit_control --security-opt seccomp=unconfined --privileged -ti --name=cyber_ops tjoconnor/cyber_ops
```

Linux/Intel Mac:
```
docker run --cap-add=SYS_PTRACE --cap-add=SYS_ADMIN --cap-add=audit_control --security-opt seccomp=unconfined --privileged -ti --name=cyber_ops tjoconnor/cyber_ops
```

M1/M2 Mac:
```
docker run --cap-add=SYS_PTRACE --cap-add=SYS_ADMIN --cap-add=audit_control --security-opt seccomp=unconfined --privileged --platform linux/amd64  -ti --name=cyber_ops tjoconnor/cyber_ops
```
