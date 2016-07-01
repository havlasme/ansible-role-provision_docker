all: main


main: main_syntax main_functional main_acceptance

main_syntax:
	ansible-playbook main.yml -i inventory --syntax-check

main_functional:
	ansible-playbook main.yml -i inventory -e "provision_docker__container_state=reloaded" --skip-tags=acceptance-test\
	&& (echo 'Functional test: PASS' && exit 0)\
	|| (echo 'Functional test: FAIL' && exit 1)

main_acceptance:
	ansible-playbook main.yml -i inventory --tags=initialize-docker,acceptance-test\
	&& (echo 'Acceptance test: PASS' && exit 0)\
	|| (echo 'Acceptance test: FAIL' && exit 1)


cleanall: clean_main

clean_main:
	ansible-playbook main.yml -i inventory -e "provision_docker__container_state=absent" --tags=initialize-docker
