
limit::
	ansible-playbook -i .vagrant/provisioners/ansible/inventory/vagrant_ansible_inventory -l $(L) provision.yaml

install:: up
	@ansible-playbook -i .vagrant/provisioners/ansible/inventory/vagrant_ansible_inventory provision.yaml 
stop::
	@vagrant destroy -f
up::
	@vagrant up
test::
	@echo "############## RUN PING TEST VLAN ISOLATED"
	@echo "Run testClient1"
	@vagrant ssh testClient1 -c "fping -q 10.10.10.1 10.10.10.254"
	@echo "Run testClient2"
	@vagrant ssh testClient2 -c "fping -q 10.10.10.1 10.10.10.254"

