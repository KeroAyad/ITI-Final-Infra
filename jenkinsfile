pipeline {
        agent {
            kubernetes {
              yaml '''
apiVersion: v1
kind: Pod
metadata:
  name: buildah
spec:
  containers:
  - name: buildah
    image: quay.io/buildah/stable:v1.23.1
    command:
    - cat
    tty: true
    securityContext:
      privileged: true
    volumeMounts:
      - name: varlibcontainers
        mountPath: /var/lib/containers
  volumes:
    - name: varlibcontainers'''   
            }
        }        
        stages {
        stage('build') {
            steps {
                  withCredentials([usernamePassword(credentialsId: 'dockerhub_id', passwordVariable: 'PASSWORD', usernameVariable: 'USERNAME')])
                {
//                     sh "docker login -u kerolosayad -p ${PASSWORD}"
//                     sh "docker build -t kerolosayad/nodeapp:latest ."
//                     sh "docker push kerolosayad/nodeapp"
                       sh "buildah ps"
                    
                }
            }    
        }
//          stage ('deployment'){
//             steps {
            
//                     sh """
//                     kubectl apply -f app-deploy.yml -n app-deploy
//                     kubectl apply -f svc.yml -n app-deploy
//                     echo Done!
//                     """
//             }
        
//         }
    }
}
