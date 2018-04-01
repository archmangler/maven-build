pipeline {
    agent {
        label "dynamic"
    } 
        stages {
            stage("Build"){
                steps {
                    echo 'Setting up ansible environment'
                    sh '''#!/bin/bash
                    cd ~/
                    rm -rf maven-build
                    git clone git@github.com:archmangler/maven-build.git
                    cd maven-build
                    virtualenv .env
                    source .env/bin/activate
                    pip install 'ansible==2.4.0.0'
                    ansible --version
                    eval $(ssh-agent -s)
                    ssh-add ~/.ssh/id_rsa
                    ansible-playbook --diff -vv -i hosts zk-exhibitor_build.yml
                    '''   
                }
            }   
            stage("Test"){
                steps {
                    echo 'Testing new jar file on a separate test server ...'
                }
            }
            stage("Deploy"){
                steps {
                    echo 'Deploying tested jar file to UAT environment ...'
                }
            }
    }
}
