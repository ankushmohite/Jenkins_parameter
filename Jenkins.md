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

# How to Setup Agent?

we will setup agent by using SSH Method.

So, first go to Manage Jenkins. There is an option in Node. Click on "New Node".

After we will give the Agent name & select type.

After that we mention a few more detail like Name, Remote root directory, Labels, Host. In Host we can mention Slave Private IP.

Then Add Credentials with Private key.

Then we can select Manually trusted key Verification strategy then Save.
