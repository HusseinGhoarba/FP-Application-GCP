pipeline {
    agent { label 'jenkins-slave' }
    stages {
        stage('build') {
            steps {
            	withCredentials([usernamePassword(credentialsId: 'docker-user', usernameVariable: 'USERNAME', passwordVariable: 'PASSWORD')]) {
                    sh   """
                        docker login -u $USERNAME -p $PASSWORD
                        docker build -t husseinghoraba/hello-vois ./app/
                        docker push husseinghoraba/hello-vois
                    """
                 }
            }
        }
        stage('deploy') {
            steps {
                    sh    """
                        kubectl apply -f kubernetes -n dev
                    """
            }
        }
    }
}
