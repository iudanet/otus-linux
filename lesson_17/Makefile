install::
	@ansible-playbook -i .vagrant/provisioners/ansible/inventory/vagrant_ansible_inventory provision.yaml 

test::
	@vagrant ssh inetRouter -c "fping \
							192.168.0.130 \
							192.168.0.50 \
							192.168.0.18 \
							192.168.0.66 \
							192.168.0.34 \
							192.168.0.2 \
							192.168.255.6 \
							192.168.255.10"
	@echo "Test ok" 