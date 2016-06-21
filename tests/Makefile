all: main

main: syntaxcheck
	# functional test
	ansible-playbook main.yml -i inventory -e "provision_docker__container_state=reloaded" --skip-tags=acceptance-test\
	&& (echo 'Functional test: PASS' && exit 0)\
	|| (echo 'Functional test: FAIL' && exit 1)

	# acceptance test
	ansible-playbook main.yml -i inventory --tags=initialize-docker,acceptance-test\
	&& (echo 'Acceptance test: PASS' && exit 0)\
	|| (echo 'Acceptance test: FAIL' && exit 1)

syntaxcheck:
    # syntax check
	ansible-playbook main.yml -i inventory --syntax-check\
	&& (echo 'Syntax check: PASS' && exit 0)\
	|| (echo 'Syntax check: FAIL' && exit 1)

cleanup:
	# remove docker containers
	ansible-playbook main.yml -i inventory -e "provision_docker__container_state=absent" --tags=initialize-docker
