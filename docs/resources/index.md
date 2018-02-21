# Resources
## Cluster Specifics

 The cluster is made up of two to three types of computers. Storage Server, Head Node Server (aka Queue Server), and Compute Node(s). 


### Storage Server
 The storage server is mostly behind the scenes. You won't need to log into this server except to first create your home directory. It's name is cloud.hpc.hamilton.edu. 


### Head Node Server (aka Queue Server) ====
 The Head Node or Queue Server is where you login to the cluster and is your main interface to utilize the rest of the cluster. It is where the Queue software runs and allows you to run commands across any of the nodes in the cluster configuration. It's name is grid.hpc.hamilton.edu. 

  
### Compute Node(s)
 The Compute Nodes are a collection of many computers all with the same configuration and configured to work with the Queue software. You generally wont need to log into these either maybe only to check to make sure your processes are running smoothly. However, doing this is usually something once you've mastered some [[:documentation:unix-tutorials|Unix basics]]. The have the names in the form una0001.
