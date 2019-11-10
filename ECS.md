# Summarize ECS 
## lowest level

### Task Definition
A Task Definition is just a set of "instructions" that specifies how to create a docker container(s), how to launch it and with what parameters/resources from AWS. These "instructions" always consist of a Docker Image, but also a number of other things like required CPU, Memory, Environment Variables, etc.

But they're just that. Just, how to make a docker container out of a docker image in context of AWS ECS.

Task Definitions can also define more than one container. So we may have a "web task definition" that consists of a Node.js docker container that references and depends on a MySQL docker container.

### Service
A Service is just manages a Task Definition in context of our cluster. We give it a Task Definition and it finds the appropriate space for it within the servers we have launched into our cluster. Additionally it can be paired with a load balancer to keep any one Task (an instance of a Task Definition) from getting over loaded.

### Container Instances
Container Instances !! Are not instances of docker images. They're just EC2 Instances that are specified to launch into our ECS Cluster. Our cluster, instead of completely viewing our instances as separate servers, instead looks at the total CPU and Memory available and makes a lot decisions for scaling based on that.

Finally our Cluster is just the "club" for all of the above. We give a number of EC2 Instances. It views them as aggregate computing power, think of it like turning multiple instances into one big instance. We define Task Definitions out of our desired Docker Images. We create a Service, hand it our Task Definition and tell it that we want X number of "Tasks" from this Task Definition. It looks through all of our Container Instances, identifies which of them have the computing power to handle our Tasks, and launches them into it.
