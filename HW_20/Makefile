SERVERS=192.168.0.130 \
		192.168.0.50 \
		192.168.0.18 \
		192.168.0.66 \
		192.168.0.34 \
		192.168.0.2 \
		8.8.8.8 


install:: up
	@ansible-playbook -i .vagrant/provisioners/ansible/inventory/vagrant_ansible_inventory provision.yaml 
stop::
	@vagrant destroy -f
up::
	@vagrant up
test::
	@echo "############## RUN TEST in inetRouter"
	@vagrant ssh inetRouter -c "fping -q $(SERVERS)"
						
	@echo "############## RUN TEST in centralServer"
	@vagrant ssh centralServer -c "fping -q $(SERVERS)"
	@vagrant ssh centralServer -c "mtr -n -r -c 1 ya.ru"
				
	@echo "Test ok" 