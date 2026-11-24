@Library("Shared") _
pipeline{
    
    agent {label "one"}
    stages{
        stage("Hello"){
            steps{
                script{
                    hello()
                }
            }
        }
        stage("Code"){
          steps{
             echo "This is clonning the code" 
             git url: "https://github.com/Bishesna18/django-notes-app", branch:"main"
             echo "Code cloning sucessful"
          }  
        }
       stage("Build"){
        steps{
            script{
            docker_build("notes-app","latest","bishesna")
            }
        }   
       }
       stage("Test"){
          steps{
            echo "This is testing"
        }    
       }
       stage("Push"){
           steps{
               script{
                   docker_push("notes-app","latest","bishesna")
               }
               }
           
       }
       stage("Deploy"){
          steps{
            echo "this is deploying"
            sh "docker compose down && docker compose up -d"
        }    
       }
    }
    
}
