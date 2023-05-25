pipeline {
    agent any
    tools {
        maven "MAVEN3"
        jdk "OracleJDK8"
    }
    environment {
        SNAP_REPO = 'vprofile-snapshot'
        NEXUS_USER = 'admin'
        NEXUS_PASS = '123'
        RELEASE_REPO = 'vpofile-release'
        CENTRAL_REPO = 'vpro-maven-central'
        NEXUSIP = '172.31.83.208'
        NEXUSPORT = '8081'
        NEXUS_GRP_REPO = 'vpro-maven-group'
        NEXUS_LOGIN = 'nexuslogin'
    }

    stages {
        stage ("BUILD") {
            steps {
                sh 'mvn -s settings.xml -DskipTests install'
            }
            post {
                success {
                    echo "Now Archiving."
                    aechiveArtifacts artifacts: '**/.war'
                }
            }
        }

        stage ("Test") {
            steps {
                sh 'mvn -s settings.xml test'
            }
        }

        stage ("Checkstyle Analysis") {
            steps {
                sh 'mvn -s settings.xml checkstyle:checkstyle'
            }
        }
    } 
}