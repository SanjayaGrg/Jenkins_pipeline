pipeline{
    agent any
    // tools {
    //     maven 'Maven 3.8.1' // Use the name configured in Global Tool Configuration
    // }
    environment {
        STAGING_SERVER = 'ec2-user@staging-server:/var/lib/tomcat9/webapps/'
        PRODUCTION_SERVER = 'ec2-user@production-server:/var/lib/tomcat9/webapps/'
        EMAIL_RECIPIENTS = 'sanjaygurun.155@gmail.com'
    }
    stages{
        stage('Build'){
            steps {
                // building the application using  tool
                echo "Building the application using a build automation tool e.g., maven"
                // sh "mvn clean install"
            }
        }
        stage('Unit and Integration Tests'){
            steps {
                echo "Running unit and integration tests using JUnit and TestNG tools respectively"
                // sh "mvn test"
            }
        }
        stage('Code Analysis'){
            steps {
                echo "Analyzing code quality so that it meets the industry requirements using sonarCube tool"
                // sh "mvn sonar:sonar"
            }
        }
        stage('Security Scan'){
            steps {
                echo "Performing security scan on the code using OWASP Markup Formatter tool"
                // sh "mvn org.owasp:dependency-check-maven:check"
            }
        }
        stage('Deploy to Staging'){
            steps {
                echo "Deploying the application to staging server using aws cli tool"
                // sh "scp target/myapp.war $STAGING_SERVER"
            }
        }
        stage('Integration Tests on Statging'){
            steps {
                echo "Running integration tests on Staging using selenium tests"
                // sh "selenium-tests.sh"
            }
        }
        stage('Deploy to Production'){
            steps {
                echo "Deploying the application to the production server"
                // sh "scp target/myapp.war $PRODUCTION_SERVER"
            }
        }
    }
    //  post {
    //     always {
    //         emailext(
    //             subject: "Pipeline Status: ${currentBuild.currentResult}",
    //             body: "Pipeline completed with status: ${currentBuild.currentResult}.",
    //             to: "$EMAIL_RECIPIENTS",
    //             attachLog: true
    //         )
    //     }
    // }
    post {
        always {
            mail to: "sanjaygurun.155@gmail.com",
            subject: "Build status Email: ${currentBuild.currentResult}",
            body: "Build completed with status: ${currentBuild.currentResult}."
        }
    }
}