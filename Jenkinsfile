properties([
    parameters([
	string(name: 'DATA', defaultValue: 'Welcome to the nginx server!!', description: 'Enter the message that need to be displayed in nginx server')
    ])
])

pipeline {
    agent any
    environment {
        ANSIBLE_BECOME_PASS = credentials('ansible-sudo-password') 
    }
    stages {
        stage('Run Ansible Playbook') {
            steps {
                sh "ansible-playbook -i inventory nginx-playbook.yml --extra-vars 'message=\"${params.DATA}\"'"
            }
        }
    }
}
