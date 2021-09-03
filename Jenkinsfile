pipeline{
agent {label 'master'}
stages{
stage("maven site"){
steps{
sh "mvn -f /root/pro/gs-maven/complete/pom.xml clean package"
//sh "mvn -f /root/pro/gs-maven/complete/pom.xml site"
}
}
stage("deploy-httpd"){
steps{
sh """
scp -o StrictHostKeyChecking=no   /root/pro/gs-maven/complete/target/gs-maven-0.1.0.jar     192.168.231.130:/var/www/html/
ssh root@192.168.231.130 systemctl restart httpd
"""
}
}
}
}
