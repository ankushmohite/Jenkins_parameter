## Install Jenkins.
sudo apt update
sudo apt install fontconfig openjdk-21-jre
java -version

sudo wget -O /etc/apt/keyrings/jenkins-keyring.asc \
  https://pkg.jenkins.io/debian-stable/jenkins.io-2026.key
echo "deb [signed-by=/etc/apt/keyrings/jenkins-keyring.asc]" \
  https://pkg.jenkins.io/debian-stable binary/ | sudo tee \
  /etc/apt/sources.list.d/jenkins.list > /dev/null
sudo apt update
sudo apt install jenkins

## Step_1: Install docker on both Jenkins master and workers...
sudo apt install docker.io -y

Then add ubuntu user to the docker group on workers.
sudo usermod -aG docker ubuntu
sudo usermod -aG docker jenkins


you can refresh the group
newgrp docker
cat /etc/group

## Step_2: create key from jenkins master.
ssh-keygen -t ed25519 -C "jenkins-deploy-key" -f ~/.ssh/id_ed25519 -N ""

<img width="940" height="277" alt="image" src="https://github.com/user-attachments/assets/edf550ac-d893-4d6a-a9eb-b6a0d235e880" />







ubuntu@ip-172-31-23-3:~$ pwd
/home/ubuntu
ubuntu@ip-172-31-23-3:~$ cd .ssh/
ubuntu@ip-172-31-23-3:~/.ssh$ ls
authorized_keys  id_ed25519  id_ed25519.pub


## Step_3: Copy public Ip an Pest into the Qa Environment like this. ( QA Env.)

chmod 700 ~/.ssh
chmod 600 ~/.ssh/authorized_keys.

# Run On Jenkins Server.
ssh -o StrictHostKeyChecking=no ubuntu@qa-ip 'echo ok'
should print: ok

## Step_4: Create credential for private key.


## Step_5:  Create credentials for dev, qa & uat.


## Step_6: Credential for docker-hub username and password.

docker login -u ankushmohite
dckr_pat__BvfBJSPK4_F9tGoAHJdfv2Nzng
