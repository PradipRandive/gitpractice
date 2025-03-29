pipeline{
    agent any
    stages{
        stage("SCM Checkout"){
            steps{
                git branch: 'master', url: 'https://github.com/PradipRandive/maven-project.git'
            }
            
        }
        stage("mvn validate"){
            steps{
                gwithMaven(globalMavenSettingsConfig: '', jdk: 'JAVA_HOME', maven: 'MVN_HOME', mavenSettingsConfig: '', traceability: true) {
                    sh 'mvn validate'
                }
            }
            
        }
        stage("mvn compile"){
            steps{
                gwithMaven(globalMavenSettingsConfig: '', jdk: 'JAVA_HOME', maven: 'MVN_HOME', mavenSettingsConfig: '', traceability: true) {
                    sh 'mvn compile'
                }
            }
            
        }
        stage("mvn package"){
            steps{
                gwithMaven(globalMavenSettingsConfig: '', jdk: 'JAVA_HOME', maven: 'MVN_HOME', mavenSettingsConfig: '', traceability: true) {
                    withSonarQubeEnv(credentialsId: 'sonarqube') {
                      sh 'mvn package sonarqube:sonarqube'
                   }
                }
            }
            
        }
    }
}
