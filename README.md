# Docker Swarm clusters

#### Create external Hyper V switch 
$ethernet = Get-NetAdapter -Name ethernet
New-VMSwitch -Name externalSwitch -NetAdapterName $ethernet.Name -AllowManagementOS $true -Notes 'Parent OS, VMs, LAN'
#### Create VM on Virtualbox
docker-machine create --driver virtualbox myvm1                              
#### create VM on Hyper-V
docker-machine create -d hyperv --hyperv-virtual-switch "myswitch" myvm1 	  
#### list all VMs and IP
docker-machine ls														                             	   
#### wrap commands through SSH
docker-machine ssh myvm1 "docker swarm init --advertise-addr <myvm1 ip>
#### view nodes in swarm
docker-machine ssh myvm1 "docker node ls"								                     
#### config shell to talk to VM
docker-machine env myvm1												                             
#### List nodes in the swarm
docker node ls																                               
#### Display detailed information on one or more nodes
docker node inspect <node>
#### Remove a node from swarm  
docker node rm <node>				
#### Retrieve command to add node
docker swarm join-token worker|manager										                   
#### Take down a single node swarm from the manager
docker swarm leave --force     											 	                       
#### List stacks or apps
docker stack ls                                           				           
#### Run the specified Compose file
docker stack deploy -c <composefile> <appname>  						                 
#### List running services associated with an app
docker service ls                 											                     
#### List tasks associated with an app 
docker service ps <service>                  								                 
#### Inspect task or container running in a service
docker inspect <task or container>                   						             
#### List container IDs
docker container ls -q                                      				         
#### Tear down an application
docker stack rm <appname>                 						             
