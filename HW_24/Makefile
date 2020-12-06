SERVERS=192.168.0.2 \
		192.168.0.1 \
		192.168.255.1 \
		192.168.255.2 \
		8.8.8.8 \
		192.168.255.5 \
		192.168.255.6 
limit::
	ansible-playbook -i .vagrant/provisioners/ansible/inventory/vagrant_ansible_inventory -l $(L) provision.yaml

install:: up
	@ansible-playbook -i .vagrant/provisioners/ansible/inventory/vagrant_ansible_inventory provision.yaml 
stop::
	@vagrant destroy -f
up::
	@vagrant up
test::
	@echo "############## RUN TEST VLAN ISOLATED"
	@echo "Run testClient1"
	@vagrant ssh testClient1 -c "fping -q 10.10.10.1 10.10.10.254"
	@echo "Run testClient2"
	@vagrant ssh testClient2 -c "fping -q 10.10.10.1 10.10.10.254"

