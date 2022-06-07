# install-kubernetes-via-ansible
### this is v1 branch which single master

- following up the tags as step in `top.yaml` file

  >  \# common setting of system
  >
  > $ ansible-playbook -t common top.yaml

- If we need to deploy internal time service, Please follow command:

  > \# this is time server 
  >
  > $ ansible-playbook -t chrony-main top.yaml

  >  \# this is time client
  >
  > $ ansible-playbook -t chrony-client top.yaml

- Then, proceed to deploy kubernetes

  > \# sign certificate
  >
  > $ ansible-playbook -t tls top.yaml

- Implement to deploy `docker` and `etcd`

  > $ ansible-playbook -t docker top.yaml
  >
  > $ ansible-playbook -t etcd top.yaml

- If master role as purpose

  > $ ansible-playbook -t master top.yaml

- If worker node

  > $ ansible-playbook -t node top.yaml

- other remaining steps

  > $ ansible-playbook -t ha top.yaml
  >
  > $ ansible-playbook -t plugin top.yaml

- if need append new  work node to cluster, Please follow the command as below

  > $ ansible-playbook  -l new -t common top.yaml 
  >
  > $ ansible-playbook -l new -t docker top.yaml
  >
  > $ ansible-playbook -l new -t node top.yaml

### **Troubleshooting**

---

#### **expected warning**

- when running step of `upgrade` may occur lost connection issue as relevant nodes were rebooted

  ![expected warning 06](https://gitee.com/bingo4933/blogimage/raw/master/img/Image%206.png)

- when deployment to master component, might occur `existed` issue as it's already existed.

  ![expected warning 07](https://gitee.com/bingo4933/blogimage/raw/master/img/Image%207.png)
