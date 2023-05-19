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
        RELEASE_REPO = 'vprofile-release'
        CENTRAL_REPO = 'vpro-maven-central'
        NEXUSIP = '172.31.91.38'
        NEXUSPORT = '8081'
        NEXUS_GRP_REPO = 'vpr-maven-group'
        NEXUS_LOGIN = 'nexuslogin'
    }

    stages {
        stage ("Build") {
            steps {
                sh 'mvn -s setting.xml -DskipTests install'
            }
        }
    }
}