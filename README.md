# CI/CD and Jenkins

# CI/CD

- Continuous Integration(CI): Developers merge/commit code to master branch multiple times a day, fully automated build and test process which gives feedback within few minutes, by doing so, you avoid the integration hell that usually happens when people wait for release day to merge their changes into the release branch.
- Continous Delivery: is an extension of continuous integration to make sure that you can release new changes to your customers quickly in a sustainable way. This means that on top of having automated your testing, you also have automated your release process and you can deploy your application at any point of time by clicking on a button. In continuous Delivery the deployment is completed manually.
- Continuous Deployment: goes one step further than continuous delivery, with this practice, every change that passes all stages of your production pipeline is released to your customers, there is no human intervention, and only a failed test will prevent a new change to be deployed to production.

# Jenkins

![image](https://user-images.githubusercontent.com/74541774/122433631-51d2b080-cf8e-11eb-9d78-acf2ba59faa9.png)

## How it works

- Connect your machine to GitHub using SSH
- GitHub connect with Jenkins also using SSH
- Jenkins sends information to the Master Node.
- The Master Node sends the information to the Agent Node
- Agent Node carries out automated tests
- If tests are successfull, the Master Node sends the information to AWS.
- Diagram process:
![image](https://user-images.githubusercontent.com/74541774/122433737-66af4400-cf8e-11eb-96a4-4412876629f4.png)
