# CI/CD and Jenkins

# CI/CD

- Continuous Integration(CI): Developers merge/commit code to master branch multiple times a day, fully automated build and test process which gives feedback within few minutes, by doing so, you avoid the integration hell that usually happens when people wait for release day to merge their changes into the release branch.
- Continous Delivery: is an extension of continuous integration to make sure that you can release new changes to your customers quickly in a sustainable way. This means that on top of having automated your testing, you also have automated your release process and you can deploy your application at any point of time by clicking on a button. In continuous Delivery the deployment is completed manually.
- Continuous Deployment: goes one step further than continuous delivery, with this practice, every change that passes all stages of your production pipeline is released to your customers, there is no human intervention, and only a failed test will prevent a new change to be deployed to production.

## Jenkins

![image](https://user-images.githubusercontent.com/74541774/122433631-51d2b080-cf8e-11eb-9d78-acf2ba59faa9.png)

## Create Jenkins key

1. `cd ~/.ssh`
2. `ssh-keygen -t rsa -b 4096 -C "youremail@mail.com`
3. `victorjenkins` name of your ssh key file
4. You have two keys, `victornovoa.pub` = public key and `victorjenkins` = private key
5. The public key will be used in your GitHub and private key in Jenkins to clone your repo.

## Build a job in Jenkins

1. Click create new job
2. Select freestyle projects, give it a name and click ok
3. Give a description and select discard old builds in the general section, max builds- select as 3
4. Build section: under build step select execute shell
5. Commands: date
6. Dashboard Click on the job you created and select build now
7. If successfull, the project should display in blue in the build history

## Configure the job on Jenkins

1. First select configure inside the job you created
2. Go to GitHub -> your repo -> under code select HTTP and copy the link. Past link in Jenkins Github Project heading
3. Go to GitHub -> your repo -> under code select SSH and copy the link
4. In Jenkins Configure -> Source Code Management -> Repository URL -> paste the SSH link
5. For credentials click add  and select Jenkins
		- Kind: select SSH Username and private key
		- Username: victorjenkinsprivate
		- Select the private key you created from gitbash
		- Paste the key and click add
6. In GitHub -> in your repo -> go to settings -> click Deploy keys in side tab -> Click Add Deploy key
7. Copy your public key in gitbash using `cat victorjenkins`
8. Paste the key as a deploy key in GitHub.
9. In Jenkins -> Source Code Management -> Credentials -> Select your private key from the drop down.
		- For Branches to build enter */main
10. Build Triggers: Select GitHub hook trigger for GitScm#
11. Office 365 Connector: Select Restric where this project can be run and in Label Expression enter: sparta-ubuntu-node
12. Build Environment: Select provide Node and npm bin/folder to PATH
13. Build -> Execute shell -> enter the commands:
		- cd app
		- npm install
		- npm test
14. Click save
15. Build now
16. If successfull the job should appear in blue.

## How it works

- Connect your machine to GitHub using SSH
- GitHub connect with Jenkins also using SSH
- Jenkins sends information to the Master Node.
- The Master Node sends the information to the Agent Node
- Agent Node carries out automated tests
- If tests are successfull, the Master Node sends the information to AWS.
- Diagram process:
![image](https://user-images.githubusercontent.com/74541774/122433737-66af4400-cf8e-11eb-96a4-4412876629f4.png)
