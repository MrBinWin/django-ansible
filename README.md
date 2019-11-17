## Ansible based deployment system of Django

### How to use:
* Add id_rsa.pub key to a node(s) into /root/.ssh/authorized_keys
to have root access via ssh from your local machine
* Adjust settings in hosts and group_vars/* configs if needed
* Initially you will need a database dump in /files/db/prod_init.pgsql created by:
`pg_dump --no-password --format=c -U {{ db_user }} {{ db_name }} > prod_init.pgsql`
Further dev and preprod will search dumps in /backup/day/{{ production_db_name }}.pgsql
* Run `ansible-playbook deploy_dev.yml` from the directory that contains
ansible.cfg to deploy site.dev
* Run `ansible-playbook deploy_preprod.yml` to deploy preprod-site.dev
* Run `ansible-playbook deploy_prod.yml` to deploy prod-site.dev or site.com