This Repository contains the code for my Master thesis.

**Topic**: 

Hyperledger Testbed auf dem Kubernetes Cluster: Automatisierter Verteilung eines Verteiltes Enterprise Blockchain
Netzwerks zur Analyse

Hyperledger Testbed on Kubernetes Cluster: Automated Deployment of a Distributed Enterprise Blockchain Network for Analysis

**STUDENT**: Sahil Kalra MTK 03680993 (sahil.kalra@tum.de, sahilkalra1991@gmail.com)

**ADVISOR**: Nasirifard, Pezhman, M.Sc. https://campus.tum.de/tumonline/visitenkarte.show_vcard?pPersonenId=69107A54C9A9AFFE&pPersonenGruppe=3

**SUPERVISOR**: Jacobsen, Hans-Arno, Prof. Dr. rer. pol. https://campus.tum.de/tumonline/visitenkarte.show_vcard?pPersonenId=D04C0FA2A1AB7B18&pPersonenGruppe=3


**Setup**:
1. clone the repo `git clone git@github.com:sahilkalra1991/master_thesis.git`
2. `git submodule sync; git submodule update --init`
2. `sudo apt install python-pip`
2. `pip install virtualenv`
2. `virtualenv --python=python3 venv`
3. `source venv/bin/activate`
4. `pip install -r requirements.txt`
5. `pip install -r kubespray/requirements.txt`
6. infra_setup command
7. cluster_setup command


**Environment Variables**: Set the following
* `OS_USERNAME`: Username to access Openstack cluster
* `OS_PASSWORD`: Password for the Openstack user 
* `OS_IMAGE_SSH_KEY`: Path to ssh privite key file for Openstack instances
* `INVENTORY_DIR_PATH`: Path to inventory directory e.g. "$pwd/inventory"


**Configuration**:
Provide cluster details in `inventory/infra/group_vars/os-infra.yml`

TODO: Add more configuration details


**Ansible Commands**:
  * **infra_setup**: `ansible-playbook -i inventory/infra/hosts.ini -v infra_setup.yaml`
    * Create OS instances
    * Creates inventory/cluster/hosts.ini
  * **infra_delete**: `ansible-playbook -i inventory/infra/hosts.ini -v infra_delete.yaml`
    * Deletes OS instances
  * **cluster_setup**: `ansible-playbook -i inventory/cluster/hosts.ini -v cluster_setup.yaml `
    * Setup nodes: DNS, LB, NFS, basic config on all
    * Creates k8s cluster using kuberspray
    * Creates inventory/blockchain/hosts.ini