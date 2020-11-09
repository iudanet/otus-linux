install::
	@ansible-playbook -i .vagrant/provisioners/ansible/inventory/vagrant_ansible_inventory provision.yaml 

test::
	@vagrant ssh inetRouter -c "ping -c1 192.168.0.2"
	@vagrant ssh inetRouter -c "ping -c1 192.168.0.34"
	@vagrant ssh inetRouter -c "ping -c1 192.168.0.66"
	@vagrant ssh inetRouter -c "ping -c1 192.168.0.18"
	@vagrant ssh inetRouter -c "ping -c1 192.168.0.50"
	@vagrant ssh inetRouter -c "ping -c1 192.168.0.130"
	echo "Test ok"