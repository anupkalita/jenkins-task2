pipeline{
    agent any

    stages{
        stage ('build sql image') {
            sh "docker build -t mysql_image ./my_webapp_mysql"
        }

        stage ('build php image') {
            sh "docker build -t php_image --no-cache ./my_webapp"
        }

        stage ('create docker network') {
            sh "docker network create my_network || true" 
        }

        stage ('run sql container') {
            sh "(( docker stop sql_container || true )) && docker run --name sql_container -d -p 6033:3306 --network my_network  -v /data:/var/lib/mysql --rm mysql_image"
        }

        stage ('run php container') {
            sh "(( docker stop php_container || true )) && docker run --name php_container -d -p 80:80 --network my_network --rm php_image"
        }
        }
}