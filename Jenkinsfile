pipeline{
    agent any

    stages{
        stage ('build sql image') {
            steps{
                sh "docker build -t mysql_image ./my_webapp_mysql"
            }
        }

        stage ('build php image') {
            steps{
                sh "docker build -t php_image --no-cache ./my_webapp"
            }
        }

        stage ('create docker network') {
            steps{
                sh "docker network create my_network || true" 
            }
        }

        stage ('run sql container') {
            steps{  
                sh "docker run --name sql_container -d -p 3306:3306 --network my_network  -v /data:/var/lib/mysql --rm mysql_image"
            }
        }

        stage ('run php container') {
            steps{  
                sh "docker run --name php_container -d -p 81:80 --network my_network --rm php_image"
            }
        }
        }
}