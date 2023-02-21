pipeline{
agent any
stages{
  stage('Update GIT') {
            steps{
                catchError(buildResult: 'SUCCESS', stageResult: 'FAILURE') {
                    withCredentials([string(credentialsId: 'github',  passwordVariable: 'GIT_PASSWORD', usernameVariable: 'GIT_USERNAME')]) {
    

                     
                        sh "git config user.email rajdeepsingh642@gmail.com"
                        sh "git config user.name rajdeepsingh642"
                        //sh "git switch master"
                        sh "cat deployment.yaml"
                        sh "sed -i 's+rajdeepsingh642/gitops-argocd-project.*+rajdeepsingh642/gitops-argocd-project:${DOCKERTAG}+g' deployment.yaml"
                        sh "cat deployment.yaml"
                        sh "git add ."
                        sh "git commit -m 'Done by Jenkins Job changemanifest: ${env.BUILD_ID}'"
                        sh "git push https://${GIT_USERNAME}:${GIT_PASSWORD}@github.com/${GIT_USERNAME}/gitops-argocd-manifest.git HEAD:main"
                    }
                }
            }
    }
    
      }
    }
