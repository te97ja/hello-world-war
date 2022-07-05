pipeline {
  agent { label 'slave' }
    stages {
      stage ('setting up parameters')
      {
        steps{
          script {
                    properties([
                      parameters([
                        choice(
                          choices: ['choice1', 'choice2']
                          name : 'parameters'
                        )
                      ])
                    ])

          }
        }
      }
        stage('clone step') {
            steps {
                sh 'git clone https://github.com/te97ja/hello-world-war.git'
            }
        }
                  stage('build step') {
            steps {
                sh 'mvn package'
            }
                  }
                            stage('deploy') {
            steps {
                sh 'sudo cp /home/slave3/workspace/git_SCM/target/hello-world-war-1.0.0.war /home/slave3/workspace/git_SCM/target/hello-world-war-pipeline.war'
                sh 'sudo cp /home/slave3/workspace/git_SCM/target/hello-world-war-pipeline.war /opt/apache-tomcat-9.0.64/webapps'
            }
        }
    }
}
