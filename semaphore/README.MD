## How to install semaphone-ansible with postgres using docker

- docker deploy stack using semaphore-stack.yaml

- ssh to node you specifically installed the semaphore, then create ssh key

- after creating ssh key, copy ssh-copy-id to all target nodes

```sh
    ssh-keygen -t rsa -f semaphore_rsa
```