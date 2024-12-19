
1. Pull Request  
2. Commit and push a new feature  
3. Deployment in staging  
4. Test  
5. Close PR and merge to main  
6. Deployment in production

## 1\. PR

The team agrees that a change has to be done to the app so a Pull Request is opened.  
This should be chained to the creation of a new branch from the main, let’s call it branch “\#1”

**Tools:**

- Jira to manage PR  
- Git: for version control

## 2\. Commit and push

The Java app “foo\#1” starts to be developed on a temporary namespace on Kubernetes thanks to direct access that developers have to a dedicated “staging” cluster, here they can manage only resources inside specific namespaces.  
Only Argo CD and Jenkins can delete and create namespaces.

For every git commit multiple actions are triggered on the client:

- a maven pom will perform: static code analysis, security test, unit test  
- git commit message formatting

Server side:

- docker container packaging  
- docker container push to a registry ([docker push](https://docs.docker.com/engine/reference/commandline/push/))  
- Argo CD will detect changes in the repo automatically deploying the new version of the feature app\#1 on a dedicated K8s namespace.

**Tools**:

- [precommit](https://pre-commit.com/\#intro):   
- [git hooks](https://git-scm.com/book/it/v2/Customizing-Git-Git-Hooks)  
- [docker scan](https://docs.docker.com/engine/scan/) (beta\!)  
- Static code analysis: [PMD](https://github.com/pmd/pmd) / [Semgrep](https://github.com/returntocorp/semgrep)  
- [ARGO CD](https://argo-cd.readthedocs.io/en/stable/)

**Docs**:

- [Jenkinsfile to build and deploy a docker image](https://github.com/brandonjones085/docker/blob/master/Jenkinsfile)

## 3 Jenkins Staging pipeline

A pipeline should be hooked by the push (or the pull request) to let Jenkins set the environment for ArgoCD, in order to let ArgoCD know the new branch name which will be the feature name and the temporary namespace name.

Also it will be run integration tests.

**Tools:**

**Docs:**

- [Environments Based On Pull Requests (PRs): Using Argo CD To Apply GitOps Principles On Previews](https://youtu.be/cpAaI8p4R60)

## 4 Debugging in a sync environment

Now that the branch and the K8s namespace are keeped in sync by ArgoCD, the developer can focus only on debugging the new feature until all tests are satisfied.

## 5 Code review and closing the pull request

## 6\. Deploy in production

A Jenkins pipeline will detect the push on the master branch, so it will wake up, do some integration test and deploy in production.

## FAQ:

- ### One or more Jenkins pipeline?

- ### Should developers have rights over namespace creation/deletion?

- ### When should I start the ArgoCD configuration?
