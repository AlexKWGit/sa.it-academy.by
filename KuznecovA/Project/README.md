# Project report

### **Project's reporter:** Kuznecov Alexandr

### **Group number:** m-sa2-28-24

### Description of application for deployment:

1. **Name of application:**  BookListApp
2. **Programming language is this application written in:**  Python (Flask)
3. **Data Base:**  MariaDB
4. **Git repository:**  [->Click here<-](https://github.com/AlexKWGit/BookListApp)

### Pipeline.
![progect_shem]( https://github.com/AlexKWGit/sa.it-academy.by/blob/md-sa2-28-24/KuznecovA/Project/Project.png)

### Technologies which were used in project

**Orchestration:**  Kubernetes
**Automation tools:**  Ansible, Github Actions, ArgoCD.
**SCM:**  GitHub
**Other tools:**  Docker, Helm.

### CI description: 

The application is written in Python. The MariaDB database is deployed on a separate host.
There are three repositories on github for organizing the ci/cd pipeline. One repository stores the application code.
The second repository contains the Helm Chart. Deployment is organized using ArgoCD.
Part of the CI project is organized using GitHub Action.
When sending changes to the git repository, github Action actions are launched.
The first task of the action launches the installation of python, its dependencies via requirements.txt.
Next, a check for valid code compilation is performed.
Next, the python code is launched to work with the database on the remote host.
The application code checks the existence of the table in the database.
If the table does not exist, the table is created. If the table has already been created, a new record with the fields
(ID, book title, author and year of publication) is added to it. Next, the docker image is built and sent to the repository https://jfrog.it-academy.by:443/artifactory/public/alexk/.
The second part of the action is changing the "tag" variable in the values.yaml file and sending these changes to the repository using Helm Chart.

### Deployment flows short description:

AgroCD syncs with Helm repository, deploys application to kubernetes cluster.

### Rollback flow description and implementation:
Rollback from ArgoCD web interface.

### Links:
1. [Git repository with application project](https://github.com/AlexKWGit/BookListApp/)
2. [Git repository with Helm pages](https://github.com/AlexKWGit/helm-test/)
3. [Git repository with ArgoCD](https://github.com/AlexKWGit/argo-flux-test/)
