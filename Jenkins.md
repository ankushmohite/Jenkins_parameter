## Jenkins.


Jenkins is a CL/CD tool use to automate build and deployment process.

When developer will write the code. operation engineer should take that code, comple that code, execute unit test cases, package that code and deploy on server. all this steps instant of doning manually. so, we can automate that process by using jenkin. 

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


 ## What is SonarQube.

SonarQube is a code quality tool used to find bugs and security issues in source code.

## What is Trivy.

Trivy is a security scanning tool used to find vulnerabilities in Docker images, dependencies, and configuration files.



# How to Integrate SonarQube with Jenkins

First, we generate a token in SonarQube and add it to Jenkins credentials. Then, we configure the SonarQube Scanner and server in Jenkins. After that, we create a webhook in SonarQube to connect it with Jenkins. Finally, we add SonarQube analysis to the Jenkins pipeline to check code quality and find bugs and security issues.

## How do you integrate SonarQube with Jenkins?

**Step 1:** First, we create a token in SonarQube under Administration → Security → Users.

**Step 2:** We go to Jenkins → Manage Jenkins → Credentials and add the SonarQube token.

**Step 3:** We go to Manage Jenkins → Tools and configure the SonarQube Scanner.

**Step 4:** We go to Manage Jenkins → System and configure the SonarQube server URL and credentials.

**Step 5:** We create a webhook in SonarQube under Administration → Configuration → Webhooks and add the Jenkins webhook URL.

Finally, we configure the Jenkins pipeline to run SonarQube analysis and check the code quality.

## What is Argo CD?
Argo CD is a GitOps tool used to deploy and manage applications in Kubernetes.
Argo CD monitors the Git repository and automatically synchronizes Kubernetes service when changes are detected.

## How do you integrate Argo CD with Kubernetes?
We install Argo CD in the Kubernetes cluster then connect it to the Git repository then configure a repository path and target namespace.


# What is RBAC in Jenkins?

RBAC stands for Role-Based Access Control. It is used to manage user permissions in Jenkins based on their roles.

For example, we can create roles such as Admin, Developer, and Tester and assign different permissions to each role.

## How does RBAC work in Jenkins?

1. Install the Role-based Authorization Strategy plugin.
2. Enable the role-based authorization strategy in Jenkins security settings.
3. Go to Manage Jenkins → Manage and Assign Roles.
4. Select Manage Roles, create roles, and assign the required permissions.
5. Select Assign Roles and assign roles to Jenkins users.
6. Users can perform only the actions allowed by their assigned permissions.

## What is Jenkins Shared Library?

A Jenkins Shared Library is used to reuse common pipeline code across multiple Jenkins pipelines instead of writing the same code again and again.

We have multiple projects and use the same steps like building a Docker image, running SonarQube analysis. so, we can create a Shared Library and reuse that code in different Jenkins pipelines.
