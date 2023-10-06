pipeline {
    agent any
    tools {
        maven "MAVEN3"
        jdk "OracleJDK8"
    }
    
    environment {
        SNAP_REPO = 'vprofile-snapshot'
  NEXUS_USER = 'puneet'
  NEXUS_PASS = 'Puneet@231'
  RELEASE_REPO = 'vprofile-release'
  CENTRAL_REPO = 'vpro-maven-central'
  NEXUSIP = '13.127.219.82'
  NEXUSPORT = '8081'
  NEXUS_GRP_REPO = 'vpro-maven-group'
        NEXUS_LOGIN = 'nexuslogin'
                SONARSERVER = 'sonarserver'
        SONARSCANNER = 'sonarscanner'
    }

    stages {
        stage('Build'){
            steps {
                sh 'mvn -s pom.xml -DskipTests install'
            }
            post {
                success {
                    echo "Now Archiving."
                    archiveArtifacts artifacts: '**/*.war'
        }
    }
}
stage('Test'){
            steps {
                sh 'mvn -s pom.xml test'
            }

        }

        stage('Checkstyle Analysis'){
            steps {
                sh 'mvn -s pom.xml checkstyle:checkstyle'
            }
        }
    }
}