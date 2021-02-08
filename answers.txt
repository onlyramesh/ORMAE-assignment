1. Git Repository Structure for Development and Collaboration and 
2. Plan for CI/CD(Below answer is good enough for CI/CD application deployment as well and my approach for CI/CD tools is gitlab)
   
   Services_Main_Repo(Features or Applications) This is only for Developers
   |
   |_ Feature_1_v1()
      |_ src_folder(contains code)
      |_ Dockerfile (to create an image of that service)
      |_ logs (Helps in troubleshooting/fix service error)
   |
   |_ .gitlab-ci.yml (This file defines the deployment flow of an each feature form development side)


   Devops_Repo  (for Devops team)
   |
   |_ Infrastructure_as_a_code(Using terraform we can organize the cloud resources which are required to run our application/product)
      |_ staging
         |_ Cloud_resources
      |_ Production
         |_ Cloud_resources
   |
   |_ Secrets( to store k8s cluster config files and public/private key of instances to login to ec2-machines which is necessary in devops point of view)
   |
   |_ Support( Kubernetes related things like notfications,scripts can be stored)
   |
   |_ Configuration( Using tools like ansible or chef we can write code to install required software for our products )
   |
   |_ .gitlab-ci.yml (This file defines the deployment flow of an each feature form devops side)
   
3. Deployment strategy
    
    If k8's is being used for run application, k8's cluster for staging and UAT worker nodes we can use spot instances which is cheaper than On demand which helps in optimizin the operation cost. For prod  k8's cluster Ondemand instances can be used as worker nodes.

4. See logs in all the above three environments.

    To see logs in all the above tools like integrating datadog tool with our applications which helps in application performance monitoring, and logstash and prometheus tools for check application logs and analyze.

5. Alerts and monitoring across all of the mentioned components
    
    For alerts we can write customized scripts using shell or python depends on the scenario and we can intigrate to mail or any communication channel. And for monitoring tools like ELK,Grafana and Datadog  helps in monitoring the application and instances and other usages CPU,memory,disk usage,DB total connections,DB-avergae cpu usage,even cloud service providers also has the set up for performance montitoring for each the component what they provide.
          
