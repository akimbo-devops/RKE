# RKE
requirement
1. Input ssh to all servers.
2. Install kubectl 
3. Install docker


- Install Ansible
    
    ```
    $ sudo apt update
    $ sudo apt install software-properties-common
    $ sudo add-apt-repository --yes --update ppa:ansible/ansible
    $ sudo apt install ansible
    ```
    
- Install rke cli
    - Download Latest Binary from this url [https://github.com/rancher/rke/releases/](https://github.com/rancher/rke/releases/)
    
    ```
    
    wget [https://github.com/rancher/rke/releases/download/v1.3.1/rke_linux-amd64](https://github.com/rancher/rke/releases/download/v1.3.1/rke_linux-amd64)
    sudo mv rke_linux-amd4 /usr/local/bin/rke
    sudo chmod +x /usr/local/bin/rke
    ```
    
- Install Docker on all node from ansible
    - SSH Key pub on deployer node must copied to all node
    - Create inventory Host (host.ini)
    
    ```
    [kube]
    10.184.0.5 ansible_user=sem
    10.184.0.6 ansible_user=sem
    10.184.0.7 ansible_user=sem
    10.184.0.8 ansible_user=sem
    ```
    
    - ansible-console -i hosts.ini
    - Install Docker to all nodes
    
    ```
    shell sudo apt-get update
    shell sudo apt-get install -y apt-transport-https ca-certificates curl gnupg lsb-release
    shell curl -fsSL https://download.docker.com/linux/ubuntu/gpg | sudo gpg --dearmor -o /usr/share/keyrings/docker-archive-keyring.gpg
    shell echo "deb [arch=$(dpkg --print-architecture) signed-by=/usr/share/keyrings/docker-archive-keyring.gpg] https://download.docker.com/linux/ubuntu$(lsb_release -cs) stable" | sudo tee /etc/apt/sources.list.d/docker.list > /dev/null
    shell sudo apt-get update
    shell sudo apt-get install docker-ce docker-ce-cli containerd.io -y
    ```
    
- RKE Config
-
