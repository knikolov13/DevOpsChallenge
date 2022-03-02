# DevOpsChallange

*Prerequisites:*
  -	Install latest version of  [Git bash](https://git-scm.com/downloads)
  -	Install latest version of [VirtualBox](https://www.virtualbox.org/wiki/Downloads)
  -	Install latest version of  [Vagrant](https://www.vagrantup.com/intro/getting-started/install.html)

 1) *Instructions:*
  - `git clone https://github.com/knikolov13/DevOpsChallenge.git`
  - `cd DevOpsChallenge`
  - Run ```vagrant up``` command
  - Once the setup is completed, run ````vagrant ssh node1````
  - Run ````docker stack deploy -c /vagrant/docker-compose-stack.yml demo````
  - Once the infrastructure is up and running, open localhost:8080 in a browser of your choice

2) Configure WordPress
  - Configure you language and press continue button
  - Configure user credentials and press install button
  - Once configuration is successful, log in with your credentials
  - Create your first blog

3) Clean up
  - Exit the docker swarm manager and execute ````vagrant destroy````
