# Docker Images

## Images

| Name    	    | DockerHub 		      | Run 		   		         	  	    |
|---------------|-------------------------|-----------------------------------------|
| [cse1001](cse1001)	    | tjoconnor/cse1001 	  | docker run -p8888:80 tjoconnor/cse1001  |
| [cse4001](cse4001) 	    | tjoconnor/cse4001 	  | docker run tjoconnor/cse4001            |
| [cse4001_vnc](cse4001_vnc)	| tjoconnor/cse4001_vnc   | docker run -p8888:80 tjoconnor/cse4001  |
| [cyber_ops](cyber_ops)		| tjoconnor/cyber_ops	  | docker run --cap-add=SYS_PTRACE --cap-add=SYS_ADMIN --cap-add=audit_control --security-opt seccomp=unconfined --privileged -ti  cyber_ops |
| [cyber_ops_vnc](cyber_ops_vnc) | tjoconnor/cyber_ops_vnc | docker run -p8888:? --cap-add=SYS_PTRACE --cap-add=SYS_ADMIN --cap-add=audit_control --security-opt seccomp=unconfined --privileged  			 |

## References

Original work by [Doro Wu](https://github.com/fcwu)

Adapted by [Frédéric Boulanger](https://github.com/Frederic-Boulanger-UPS)

## License
==================

Apache License Version 2.0, January 2004 http://www.apache.org/licenses/LICENSE-2.0

