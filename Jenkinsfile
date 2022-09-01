pipeline {
    agent any
    
    
    stages{
       stage ('Build') {
           
                steps{
                    // sh 'ls'
                     //sh ' cp Hello.cpp  / '
                    // sh 'cd / && ls '
                     sh 'docker run -t -d  --name fubuntu ubuntu:focal'
                     sh 'docker exec --user root fubuntu apt-get update'
                     sh 'docker exec --user root fubuntu  apt install -y build-essential'
                     sh 'docker exec --user root fubuntu apt install -y git'
                     sh '  docker exec fubuntu mkdir hello_1.0-1_amd64 && docker exec fubuntu mkdir hello_1.0-1_amd64/DEBIAN'
                     sh ' docker exec fubuntu bash -c " cd hello_1.0-1_amd64 && mkdir usr && cd usr && mkdir bin "'
                     sh 'docker exec fubuntu ls && docker exec fubuntu bash -c "cd hello_1.0-1_amd64 && ls "'
                     sh " docker exec fubuntu bash -c ' cd hello_1.0-1_amd64/DEBIAN &&  echo   'Package:hello' > control && echo 'Version:1.0'  >> control && echo 'Architecture:amd64' >> control &&  echo 'Maintainer:Gokay' >> control &&   echo 'Description:Test' >> control' "
                     sh 'docker exec fubuntu bash -c " cd hello_1.0-1_amd64/DEBIAN && cat control"'
                     sh '  docker exec fubuntu git clone https://github.com/Goookay/Jenkins-repo.git'
                     sh '  docker exec fubuntu bash -c "g++ Jenkins-repo/Hello.cpp &&  mv a.out hello " '
                     //sh '   bash -c  cd  hello_1.0-1_amd64/usr &&   mkdir bin  '
                     sh ' docker exec fubuntu cp hello hello_1.0-1_amd64/usr/bin'
                     sh ' docker exec fubuntu mv hello helo'
                     sh 'docker exec fubuntu dpkg-deb --build hello_1.0-1_amd64'
                     sh 'docker exec fubuntu apt install ./hello_1.0-1_amd64.deb'
                    sh ' docker exec fubuntu  dpkg -i hello_1.0-1_amd64.deb'
                    
                     sh ' docker exec fubuntu hello'
                     sh 'docker exec fubuntu bash -c " cd / && ls"'    
                    sh 'docker exec fubuntu ls'
                     
                }
                
                }
               
                
            
        stage ('push image') {
            steps {
                sh 'docker login -u gokayturhanoglu -p dckr_pat_gZ4ONxlUmgPDwm1-3UyJLqxwFE8'
                sh 'docker commit  fubuntu gokayturhanoglu/jenkins_deneme:1'
                sh 'docker images'
                sh 'docker push gokayturhanoglu/jenkinsdeneme'
               
            }
        }
    }
}
    
