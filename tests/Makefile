all: main

main:
    # syntax check
	ansible-playbook main.yml -i inventory --syntax-check

	# functional test
	ansible-playbook main.yml -i inventory -e "provision_docker__container_state=reloaded" --skip-tags=acceptance-test\
	&& (echo 'Functional test: PASS' && exit 0)\
	|| (echo 'Functional test: FAIL' && exit 1)

	# acceptance test
	ansible-playbook main.yml -i inventory --tags=initialize-docker,acceptance-test\
	&& (echo 'Acceptance test: PASS' && exit 0)\
	|| (echo 'Acceptance test: FAIL' && exit 1)

cleanall:
	# remove docker containers
	ansible-playbook main.yml -i inventory -e "provision_docker__container_state=absent" --tags=initialize-docker
