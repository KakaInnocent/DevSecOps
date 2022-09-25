What is Jenkins?
Open source automation tool, which uses plugins to build and test your project code continously across several pipelines.

A pipeline is a collection of jobs that brings the software from version control into the hands of the end users by using automation tools.
Start --> git version --> maven version --> docker version --> kubernetes version --> End

It ha lots of 3rd party plugins available. Plugins are the primary means of enhancing the functionality of a Jnekins environment to suit organization or user-specific needs.
Plugins can be installed using Jenkins Remote REST API, Jenkins CLI, Plugin Manager in the Web UI
e.g blueocean,perfomancem, slack, sonar, pitmutation, jacoco, kubernetes-cli, docker-workflow, dependency-check-jenkins-plugin

Normally Jenkins runs on port 8080, you can check if its running using the systemctl status jenkins. Initially you'll require the admin password to login to the jenkins portal and the password is located at /var/lib/jenkins/secrets/initialAdminPassword


After setting up jenkins, we need to install the required plugins, through either the manage jenkins UI, click manage plugins

We'll install from the command line through the jenkin-plugins directory. The txt file descrribes the plugins we are to install and their version. The bash script which will connect to jenkins connect some tokens and download the tokens. Run the script, bash plugin-installer.sh and it shpuld install all the scripts and plugins.

To create a pipeline in Jenkins go to dashboard, new item, name it with regards with what it performs, e.g for checking versions you can use. checking-versions and select pipeline, You can try a sample pipeline at the bottom, then click on build

Sometimes kubernetes might fail, why because it executes commands through the jenkins cli user, while the system might require the system user. to fix that visit the kubernetes cli documentation and you'll see we need to add user configurations detail.

We;ll need to get the config file from the vm, at the root user located at /root/.kube/config

copy the data and go to Jenkins, try and find manage credentials. Add a new credential, which is a secret and upload the contents we copied from cofig








