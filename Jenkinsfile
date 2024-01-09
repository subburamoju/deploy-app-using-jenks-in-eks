pipeline {
    agent any

    stages {
        stage('select k8') {
            steps {
              sh 'kubectl config use-context arn:aws:eks:us-east-1:449203461473:cluster/devops17-eks-gy2tck9g'    
            
        }
        }
        stage('connect k8') {
            steps {
                sh '''
                  kubectl get nodes
                  #if [ $? == 0 ]
                  #then
                  #{
                   # echo "sucessfully connected to cluster"
                  #}
                  #else{
                  # echo "unable to connect to cluster"
                   #exit 1
                  #}
                  
                '''
            }
        }
        stage('deploy k8 files') {
            steps {
                
              sh '''
                          kubectl apply -f $WORKSPACE/deploy.yaml
              '''
                
            }
        }
        stage('validate deployment') {
            steps {
                sh '''
                 kubectl get po
                 #if [ $? == 0 ]
                 #then
                 #{
                 #  echo "sucessfully connected to cluster"
                  #}
                  #else{
                   #echo "unable to connect to cluster"
                   #exit 1
                  #}
                '''
            }
        }
    }
}
