Docker Swarm clusters

docker-machine create --driver virtualbox myvm1                              # Create VM on Virtualbox

docker-machine create -d hyperv --hyperv-virtual-switch "myswitch" myvm1 	   # create VM on Hyper-V

docker-machine ls														                             	   # list all VMs and IP

docker-machine ssh myvm1 "docker swarm init --advertise-addr <myvm1 ip>"     # wrap commands through SSH
  
docker-machine ssh myvm1 "docker node ls"								                     # view nodes in swarm

docker-machine env myvm1												                             # config shell to talk to VM

docker node ls																                               # List nodes in the swarm

docker node inspect <node>												                           # Display detailed information on one or more nodes
  
docker node rm <node>														                             # Remove a node from swarm
  
docker swarm join-token worker|manager										                   # Retrieve command to add node

docker swarm leave --force     											 	                       # Take down a single node swarm from the manager

docker stack ls                                           					# List stacks or apps

docker stack deploy -c <composefile> <appname>  						        # Run the specified Compose file
  
docker service ls                 											            # List running services associated with an app

docker service ps <service>                  								        # List tasks associated with an app 
  
docker inspect <task or container>                   						    # Inspect task or container running in a service
  
docker container ls -q                                      				# List container IDs

docker stack rm <appname>                            						    # Tear down an application
