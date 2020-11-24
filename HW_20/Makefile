SERVERS=192.168.0.2 \
		192.168.0.1 \
		192.168.255.1 \
		192.168.255.2 \
		8.8.8.8 \
		192.168.255.5 \
		192.168.255.6 

install:: up
	@ansible-playbook -i .vagrant/provisioners/ansible/inventory/vagrant_ansible_inventory provision.yaml 
stop::
	@vagrant destroy -f
up::
	@vagrant up
test::
	@echo "############## RUN TEST in inetRouter"
	@vagrant ssh inetRouter -c "fping -q $(SERVERS)"
	@vagrant ssh inetRouter -c "curl -Is  192.168.0.2  | head -n 1"

						
	@echo "############## RUN TEST in centralServer"
	@vagrant ssh centralServer -c "fping -q $(SERVERS)"
	@vagrant ssh centralServer -c "mtr -n -r -c 1 ya.ru"
	@vagrant ssh centralServer -c "curl -Is  192.168.0.2  | head -n 1"

	
	@echo "############## RUN TEST in inetRouter2"
	@vagrant ssh inetRouter2 -c "fping -q $(SERVERS)"
	@vagrant ssh inetRouter2 -c "curl -Is  192.168.0.2  | head -n 1"

	@echo "############## RUN TEST in localhost to 192.168.50.10"
	@curl -Is 192.168.50.10 | head -n 1
	@echo "Test ok" 