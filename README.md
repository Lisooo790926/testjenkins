# Test Jenkins

## Purpose
Create this repo for testing jenkins behaviors and get quite understanding about Jenkin.
I have below questions what to understand.
- What is Jenkins?
- Why use Jenkins?
- How does it work?

## Step 
0. Generate the basic maven project and push into this repo 
   https://maven.apache.org/archetypes/maven-archetype-quickstart/
1. Create the AWS instance to build jenkins server and setup
   - Download the jenkins war and security copy from your local to the instance
      ``` 
      scp -i <your_instance_key>.pem ./jenkins.war <your_instance_domain>:<where_you_want_to_put> 
      ``` 
   - Install java into AWS server
   - Run Jenkins server 
      ```
      java -jar jenkins.war 
      ```
   - Initial Jenkins setting (first time login your Jenkins setting)
   - Install maven integration for creating maven job
   - Setting GitHub Server credential in Jenkins 
     (The credential should be created in your GitHub account)
   - Add SSH private key in Jenkins for git operation 
     (The SSH key should create in local, and add into GitHub, 
   - Create maven job in Jenkins and binding this repository in setting
     (Should add git public key for )
     
2. Add WebHook to bind with Jenkins url in this repository, I can decide when should the github send notificaiton to Jenkins
   (make sure add /github-webhook behind your jenkins endpoint)
3. Try to push the code change and observe what will Jenkins working 

## Test Result 
When pushing the code change, my repo will send notification to Jenkins to start the job.
The job will clone whole repo and execute mvn clean install 
Also it will generate the new report after running the Jenkins to show unit test result.
(automatically run the unitTest because of this plugin in maven project (Maven Surefire Plugin))

## Conclusion 
1. What is Jenkins -> It is DevOps tools for imporving efficiency in CICD
2. Why use Jenkins -> It totally boost the deployment or testing speed, and you could use flexible pipeline script to decide what should you do in the current Job
   And you could own multiple jobs to handle different cases, like testing, building, deploying and so on.
3. How does it work -> For basic work flow, after binding version control(VC) with Jenkins server, the VC will send the notification to Jenkins server.
   Based on different notification, then Jenkins will run the specific job to build and test or to build and deploy.
   ex :  In Samsung project, our system will run Jenkins when creating Pull Request! 
  
## Reference 
https://www.youtube.com/watch?v=nCKxl7Q_20I
https://www.youtube.com/watch?v=7KCS70sCoK0
https://www.jenkins.io/doc/book/pipeline/getting-started/
