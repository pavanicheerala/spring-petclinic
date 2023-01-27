pipeline {
    agent  { label 'JDK11MVN' }
    parameters {
        choice(name: 'BRANCH_TO_BUILD', choices: ['main'], description: 'Branch to build')
        string(name: 'MAVEN_GOAL', defaultValue: 'package', description: 'maven goal')

    }
    stages {
        stage('vcs') {
            steps {
                git branch: 'JDK11MVN', url: 'https://github.com/muthyalasaikiran/spring-petclinic.git'
                git branch: "${params.BRANCH_TO_BUILD}", url: 'https://github.com/muthyalasaikiran/spring-petclinic.git'
            }

        }
        stage('build') {
            steps {
                sh '/opt/apache-maven-3.8.7/bin/mvn package'
                sh "/opt/apache-maven-3.8.7/bin/mvn ${params.MAVEN_GOAL}"
            }
        }
        stage('archive results') {
            steps {
                junit '**/surefire-reports/*.xml'
            }
        }
    }
}
