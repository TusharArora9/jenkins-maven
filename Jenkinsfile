pipeline{
agent any
stages{
stage("maven site"){
steps{
sh "mvn -f /root/project/pom.xml clean package"
//sh "mvn -f /root/project/pom.xml site"
}
}
stage("deploy-httpd"){
steps{
sh """
scp -r /root/project/target/gs-maven-0.1.0.jar  192.168.231.129:/var/www/html/
ssh root@192.168.231.129 systemctl restart httpd
"""
}
}
}
}
