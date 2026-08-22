## Install Jenkins

```bash
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

Check the generated keys:

ubuntu@ip-172-31-23-3:~$ pwd
/home/ubuntu

ubuntu@ip-172-31-23-3:~$ cd .ssh/

ubuntu@ip-172-31-23-3:~/.ssh$ ls
authorized_keys  id_ed25519  id_ed25519.pub



<img width="940" height="277" alt="image" src="https://github.com/user-attachments/assets/edf550ac-d893-4d6a-a9eb-b6a0d235e880" />


## Step_3: Copy public Ip an Pest into the Qa Environment like this. ( QA Env.)

chmod 700 ~/.ssh 
chmod 600 ~/.ssh/authorized_keys

<img width="940" height="228" alt="image" src="https://github.com/user-attachments/assets/00615a58-9d44-47fd-9504-70c346ffcb58" />


# Run On Jenkins Server.
Test SSH connectivity from the Jenkins server:

ssh -o StrictHostKeyChecking=no ubuntu@qa-ip 'echo ok'
should print: ok

## Step_4: Create credential for private key.

<img width="940" height="493" alt="image" src="https://github.com/user-attachments/assets/c3b34ac8-ec6b-4b6e-8f02-20b2c03c7535" />


## Step_5:  Create credentials for dev, qa & uat.

<img width="940" height="521" alt="image" src="https://github.com/user-attachments/assets/8f533581-67f5-4fde-8257-6a41c4f602a0" />



## Step_6: Credential for docker-hub username and password.

<img width="940" height="594" alt="image" src="https://github.com/user-attachments/assets/919b9f5e-4957-4815-b429-d4e70b109f27" />


docker login -u ankushmohite
dckr_pat__BvfBJSPK4_F9tGoAHJdfv2Nzng
