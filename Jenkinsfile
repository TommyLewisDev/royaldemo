pipeline{
    agent any 
    
    
    stages {
        stage("build stage"){
            steps{ 
                   
                   script{

                                    
                    sh '''
                     
                     sudo apt-get update 
                     sudo apt install docker.io -y
                     sudo curl -LO https://storage.googleapis.com/kubernetes-release/release/v1.23.6/bin/linux/amd64/kubectl
                     sudo install -o root -g root -m 0755 kubectl /usr/local/bin/kubectl
                     sudo chmod +x kubectl
                     mkdir -p ~/.local/bin
                     mv ./kubectl ~/.local/bin/kubectl
                     sudo curl https://raw.githubusercontent.com/helm/helm/master/scripts/get-helm-3 > get_helm.sh
                     sudo chmod 700 get_helm.sh
                     sudo ./get_helm.sh
                     sudo helm version
                     aws eks update-kubeconfig --name eksdemo --region us-west-2
                     kubectl delete deployment web ||echo "deployment web doesn't exist.."
                     kubectl delete svc web ||echo "svc web doesn't exist"
                     kubectl create deployment web --image=gcr.io/google-samples/hello-app:1.0 --replicas=2
                     kubectl expose deployment web --type=NodePort --port=8080



                    '''

                   }
                      }
            

            }


}
}




        

    
