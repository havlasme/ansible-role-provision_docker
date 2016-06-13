all: main

main: syntaxcheck
	ansible-playbook main.yml -i inventory -e "provision_docker__container_state=reloaded"
	ansible-playbook main.yml -i inventory --tags=initialize_docker,functional_test

syntaxcheck:
	ansible-playbook main.yml -i inventory --syntax-check
