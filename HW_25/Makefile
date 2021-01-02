
limit::
	ansible-playbook -i .vagrant/provisioners/ansible/inventory/vagrant_ansible_inventory -l $(L) provision.yaml

install:: up ansible-freeipa
	@ansible-playbook -i .vagrant/provisioners/ansible/inventory/vagrant_ansible_inventory provision.yaml 
stop::
	@vagrant destroy -f
up:: 
	@vagrant up

ansible-freeipa:
	git clone git@github.com:freeipa/ansible-freeipa.git