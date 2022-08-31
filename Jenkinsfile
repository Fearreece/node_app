pipeline{
    agent any
    stages{
        stage("Test"){
            steps{
                echo('This is the building stage')
            }
        }
        stage("Build stage"){
            steps{
                echo('This is the build stage')
                sh '''
                   ssh -i /var/lib/jenkins/project1.pem -t -o StrictHostKeyChecking=no ubuntu@ec2-34-229-57-35.compute-1.amazonaws.com
                   sudo rm -rf ~/node_app
                   mkdir ~/node_app
                   cd ~/node_app
                   sudo git init
                   sudo git config --global --add safe.directory /var/lib/jenkins/node_app
                   sudo git remote add origin https://github.com/Fearreece/node_app.git
                   sudo git pull origin main
                   sudo npm install
                   sudo npm start
                '''
            }
        } 

    }
}