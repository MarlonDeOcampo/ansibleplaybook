## How to install semaphone-ansible with postgres using docker

- docker deploy stack using semaphore-stack.yaml

- ssh to node you specifically installed the semaphore and then docker container exec to it

- create .ssh folder then cd to it

```
    mkdir ~/.ssh
    cd ~/.ssh
```

- ssh-keygen creating the default id_rsa key

- after creating ssh key, copy ssh-copy-id to all target nodes

```sh
    ssh-keygen 
    ssh-copy-id -i id_rsa.pub node@ipaddress
```

### Accessing the web ui of Semaphore

- access the web ui using the ip address of the node where u did installed the semaphore

```
    ipaddress:3000
```

- you will be asked to login using "admin" user and "changeme" password

- you will be asked to create project

- go to keystore tab to create an ssh-key store

1. click the add new key button
2. input a key name
3. select ssh key type
4. leave the username and paraphrase blank(if you ever have created the ssh without password, which is recommended)
5. copy paste the content of the created id_rsa file. (not the id_rsa.pub)
6. press create

### adding repository

1. Make sure that you have already setup the github repository that contains all the playbook you intended to use with the semaphore
2. Press "New Repository" button
3. Input repository name you like
4. got to the github repository the get the http link by pressing the code dropdown then copy the https link
5. paste the link in the url or path input field
6. input the branch 
7. select the access key which you need to create in the key store tab if ever your repo is private, select none from the dropdown only if its public

### creating environment for ssh connection

1. go to environment tab
2. click new environemnt button
3. in the extra variable part, insert the  "ANSIBLE_HOST_KEY_CHECKING": "False" inside the curly brace then save

### Creating inventory

1. go to inventory tab
2. click new inventory button
3. insert any name that you like
4. in the credentials, select the ssh key we created in the key store
5. select static yaml from the type
6. copy paste your the code from from the ready made ansible inventory that you have, or create a new code if you do not have any then save

### Creating templates

1. Go to the template tab
2. click new template\
3. insert any name that you like
4. input the name of the playbook. the playbook name should be the same name of what in your githun repository
5. select inventory from the dropdown
6. select the repository and environment that we've created before
7. click create

-  now try to run the template with the dry run option checked so that we can see if there some error first before running it 