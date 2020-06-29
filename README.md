# Jenkins CI/CD Pipelines Workshop Quick Start Guide

**System Requirements:**
* 4GB available RAM.
* 20GB available disk storage.


**Getting started:**
1. Install prerequisites:
    * Mac users: 
        * [Hyperkit](https://minikube.sigs.k8s.io/docs/drivers/hyperkit/)
    * Linux users: 
        * [kvm2](https://minikube.sigs.k8s.io/docs/drivers/kvm2/)
    * Mac + Linux:
        * [minikube](https://kubernetes.io/docs/tasks/tools/install-minikube/).
        * [kubectl](https://kubernetes.io/docs/tasks/tools/install-kubectl/).
        * [helm](https://helm.sh/docs/intro/install/).
        * [sbt](https://www.scala-sbt.org/1.x/docs/Setup.html).
    
2. Checkout this repository and change directory to the root of the repository.

3. **[Optional]** Create a `.env` file and update your GitHub credentials and repository settings.
   See `.env.example` file for reference. 

4. Launch or reset workshop:
    ```bash
    $ ./reset-workshop.sh
   Resetting Jenkins workshop: 'cicd-jenkins-workshop-1'...
   ...
   Switched to context "cicd-jenkins-workshop-1".
   Installing Jenkins...
   Done!
   
   
   ====================================================================================
   Jenkins Admin user URL:               http://192.168.39.20:32000/login
   Jenkins Admin user name:              admin
   Jenkins Admin user password:          secret
   GitHub WebHook URL: (Ngrok tunnel)    https://123456abc.ngrok.io/github-webhook/
   ====================================================================================
    ```

5. **[Optional]** Update GitHub webhook URL in your GitHub repository settings.

6. Login to the Jenkins web UI and enter your credentials. If you see the 
`Welcome to ${WORKSHOP_NAME} Jenkins CI/CD!` screen, you are ready!


**Cleanup:**
```bash
$ (source .env.example && minikube delete --profile ${WORKSHOP_NAME})
```


**Scala Project:**
* Run unit tests:
    ```bash
    $ sbt 'testOnly -- -n UnitTest'
    ```
* Run "Slow" suite:
    ```bash
    $ sbt 'testOnly -- -n Slow'
    ```
* Run all tests:
    ```bash
    $ sbt test
    ```
