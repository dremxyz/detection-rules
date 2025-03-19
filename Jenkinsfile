def remote=[:]
remote.name = 'jenkins'
remote.host = '108.61.103.19'
remote.allowAnyHosts = true

pipeline {
    agent any
    environment {
        SSH_CREDS=credentials('jenkins_ssh')
    }
    stages {
        stage('Connect and Run Commands') {
            steps {
                script {
                    remote.user=env.SSH_CREDS_USR
                    remote.password=env.SSH_CREDS_PSW
                    }
                sshCommand(remote: remote, command: "cd /root/detection-rules/ && git pull")
                sshCommand(remote: remote, command: "cd /root/detection-rules/ && python3 -m venv detection-rules-build/ && source detection-rules-build/bin/activate && python3 -m detection_rules kibana import-rules -d custom_rules/ -o")
                }
            }
        }
        post {
            always {
                sleep 5
            }
        }
    }
