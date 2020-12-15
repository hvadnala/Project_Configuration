To start with the project, after cloning the github repoistory.
The Maven build was supposed to fail, added proprty for jdk. 

# How reliable and available is your deployment? What could affect this?
```
    I have written the docker file and build the Image using the local docker server. Registered the Image and ran the container, output was shown on the output port 8080. The cloud formation template was able to launch intance but still some additional choices can be added like SSH details, IAM roles, S3 bucket.

```

# How automated is your answer? How suitable is the process to maintenance and updates? What changes would you make to improve the deployment process or improve maintainability?
```
    Its still not completed automated I would say. I would like to have a proper version control, where any changes pushed to master branch, it automaticly builds the maven pom.xml file, updates the image in docker registery and push thoses to to containers either using locally or using ansible playbook on cluster scale. When looking at big thing we can also take into count some other facter like, region of deployment, replica factor and integrating testing. The above defined process will be easy to maintain and do updates, we can also added further code quality using tools like sonarQube. One more thing to improve is add the monitoring and messaging tool for this application with services like CloudWatch and SNS.

```

# How scalable is your answer? What would you do allow the deployment to handle more traffic?
```
    The current auto scaling service on EC2 instance can used manually to trigger the parameters. After implementing the above defined process we can use trigger from the monitoing setup to trigger the auto scaling services that will be integrated with ec2 instance.
    
```

# How secure is your answer? Would seeing your template expose any sensitive information?
```
    It is secure to lauch the application on the AWS cloud and ouput can be checked in the commandline. But when we launch in bigger scale we will be adding region sepicfic keys, subscription ID and password. Many of this paramerters can be set in varaible group and before launching the template we can run scripts in codepipeline to get this values and inteprated these values in the template.

```

# How could you preserve log data from these instances, even if they terminate?
```
    When launching or we can change the root volume of the instances we can set up DeleteOnTermination attribute to False. Another way would be to use Elastic IP's and genrate AMI to launch the instances.
    
```