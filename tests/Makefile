all: main

main: syntaxcheck
	# functional test
	ansible-playbook main.yml -i inventory -e "provision_docker__container_state=reloaded"

	# acceptance test
	ansible-playbook main.yml -i inventory --tags=initialize_docker,acceptance_test

syntaxcheck:
    # syntax check
	ansible-playbook main.yml -i inventory --syntax-check
