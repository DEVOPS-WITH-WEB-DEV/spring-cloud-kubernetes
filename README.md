# kubernetes-configmap-reload

Pre-requisites[ TAKE AMAZON LINUX2 SYSTEM t2.micro]:
--------
    - Install Git
    
    yum install git -y
    
    - Install Java
    
    yum install java -y
   
    - Install Maven
    
    cd /opt/
    wget http://mirrors.estointernet.in/apache/maven/maven-3/3.6.3/binaries/apache-maven-3.6.3-bin.tar.gz
    tar xvzf  apache-maven-3.6.3-bin.tar.gz
    vi /etc/profile.d/maven.sh
    export MAVEN_HOME=/opt/apache-maven-3.6.3
    export PATH=$PATH:$MAVEN_HOME/bin
    
    
    - Install Jenkins
    
      sudo wget -O /etc/yum.repos.d/jenkins.repo https://pkg.jenkins.io/redhat-stable/jenkins.repo
      sudo rpm --import https://jenkins-ci.org/redhat/jenkins-ci.org
      sudo yum install jenkins -y 
      sudo systemctl start jenkins
    
    
    - Install Docker
    
    yum install docker -y
    systemctl start docker
    systemctl enable docker
    usermod -aG docker jenkins [ Add jenkins user to docker group ]
    
    - Install Python
    
    yum install python3 -y
    
    - Install Ansible 
    
    amazon-linux-extras install ansible2 -y
    
    

    

    
Clone code from github:
-------
    git clone https://github.com/praveen1994dec/spring-cloud-kubernetes.git
    cd spring-cloud-kubernetes/kubernetes-configmap-reload
    
Build Maven Artifact:
-------
    mvn clean install
 
Build Docker image for Springboot Application
--------------
    docker build -t praveen1994dec/kubernetes-configmap-reload .
  
Docker login
-------------
    docker login
    
Push docker image to dockerhub
-----------
    docker push praveen1994dec/kubernetes-configmap-reload
    
Deploy Spring Application:
--------
    kubectl apply -f kubernetes-configmap.yml
    
Check Deployments, Pods and Services:
-------

    kubectl get deploy
    kubectl get pods
    kubectl get svc
    

