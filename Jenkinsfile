pipeline {
    agent { label 'jenkins-slave' }
    stages {
        stage('build') {
            steps {
            	withCredentials([usernamePassword(credentialsId: 'docker-user', usernameVariable: 'USERNAME', passwordVariable: 'PASSWORD')]) {
                    sh   """
                        docker build -t hussein-ghoraba/hello-vois ./app/
                        docker push hussein-ghoraba/hello-vois
                    """
                 }
            }
        }
        stage('deploy') {
            steps {
                    sh    """
                        kubectl create ns dev
                        kubectl apply -f k8s-files -n dev
                    """
            }
        }
    }
}
