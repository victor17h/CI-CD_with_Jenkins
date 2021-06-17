# CI/CD and Jenkins

# CI/CD

- Continuous Integration(CI): Developers merge/commit code to master branch mul>
- Continous Delivery: is an extension of continous integration to make sure tha>
- Continuous Deployment: goes one step further than continuous delivery, with t>

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
