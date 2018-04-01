
Sample ansible script and Jenkinsfile to demonstrate pipeline-as-code in Jenkins, along with wrapping IAC operations within ansible run from the same pipeline.
Part of overall implementation of CI/CD for infrastructure.

Implementation steps:

- Create a Jenkins pipeline defined entirely in Jenkinsfile (Groovy DSL)
- Pull Ansible script from GitHub repo
- Run ansible script against remote server for build
- preserve security at all points (if needs be use environment variable provided via Jenkins build env variables) 

Keywords:

- IAC
- Pipeline-as-Code
- CI/CD
