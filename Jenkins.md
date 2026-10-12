Jenkins is a CL/CD tool use to automate build and deployment process.

When developer will write the code. an operation engineer should take that code, comple that code, execute unit test cases, package that code and deploy on server. all this steps instant of doning manually. so, we can automate that process by using jenkin. 

CI use to automate build and test code whenever developer push changes to the git repos.

CD use to automate the process of depolying an code to an environment.


# Jenkins Master-Slave

Basically, master is responsible for managing all the slave instance.

Let us assume we have 100 build in our master. So, if we build all 100 in master. So most of the change to get the performance issue.

So, we are using slave, so jenkins use to distribute workload to the multiple slave.


# Poll SCM
Poll SCM checks Git repository at regular intervals to see if any code changes have been made. so, Jenkins automatically triggers the build.

# Build Periodically

Build Periodically in Jenkins triggers the job at the scheduled time or interval you have configured.

# How to Setup Agent?

we will setup agent by using SSH Method.

So, first go to Manage Jenkins. There is an option in Node. Click on "New Node".

After we will give the Agent name & select type.

After that we mention a few more detail like Name, Remote root directory, Labels, Host. In Host we can mention Slave Private IP.

Then Add Credentials with Private key.

Then we can select Manually trusted key Verification strategy then Save.

# Jenkins Credentials

Jenkins Credentials is a way to securely store secret information like username, password or keys. 
To keep sensitive data safe and separate from main job configuration.

Because of this, if someone views the job, they can't see the actual secret.


# Plugins

We are using plugins to add new functionality to Jenkins.

So, plugins allow Jenkins to integrate with different tools in the environment.

Example: Git, Docker, Maven.


# Jenkins Workspace

Jenkins workspace is a directory to store source code and perform build, testing, and other job-related tasks.

# Jenkins Agent

A Jenkins agent helps distribute the workload from the Jenkins master to multiple nodes.

# Procedure to Create a Job

So, in the Jenkins dashboard, there is an option in "New Item".

So, we will give the "Item Name" and select "Freestyle" or "Pipeline", which you want to do.

After that, we mention a few more details in the job, like Project Name, Description, SCM, and Branch to Build.

Then Apply & Save.

# Blue-Green Deployment.

Basically, in which we have 2 environments, Blue and Green.

We have an active environment that serves production traffic, while the inactive one is updated with new changes.


## Question: If the First Stage Fails, How Do You Continue the Remaining Stages?

I use the `catchError` block in Jenkins Pipeline. It allows the pipeline to continue executing even if a stage fails.

## Build with Parameters.
In my project, I use Build with Parameters to select the environment, such as Dev, QA, or UAT. Jenkins deploys the application to the selected environment.


1. What is SonarQube?
SonarQube is a code quality tool used to find bugs and security issues in source code.

2. What is Trivy?
Trivy is a security scanning tool used to find vulnerabilities in Docker images, dependencies, and configuration files.
