
install:: up
	@ansible-playbook -i .vagrant/provisioners/ansible/inventory/vagrant_ansible_inventory provision.yaml 

install-ras:: up
	@ansible-playbook -i .vagrant/provisioners/ansible/inventory/vagrant_ansible_inventory provision-ras.yaml 
stop::
	@vagrant destroy -f
up::
	@vagrant up

install-tap:: up
	@ansible-playbook -e vpn_mode=tap -i .vagrant/provisioners/ansible/inventory/vagrant_ansible_inventory provision.yaml 

install-tun:: up 
	@ansible-playbook -e vpn_mode=tun -i .vagrant/provisioners/ansible/inventory/vagrant_ansible_inventory provision.yaml 

add-client-openvpn-ubuntu::
	nmcli connection import type openvpn file template/client-01.ovpn