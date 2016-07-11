all: syntax functional acceptance

syntax:
	ansible-playbook test.yml -i inventory --syntax-check

functional:
	ansible-playbook test.yml -i inventory -e "provision_docker__container_state=reloaded" --skip-tags=acceptance-test\
	&& (echo 'Functional test: PASS' && exit 0)\
	|| (echo 'Functional test: FAIL' && exit 1)

acceptance:
	ansible-playbook test.yml -i inventory --tags=initialize-docker,acceptance-test\
	&& (echo 'Acceptance test: PASS' && exit 0)\
	|| (echo 'Acceptance test: FAIL' && exit 1)

clean:
	ansible-playbook test.yml -i inventory -e "provision_docker__container_state=absent" --tags=initialize-docker
