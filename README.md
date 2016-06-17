Automates pre-deployment setup for ruby applications run with puma.

Assumes the a functional and built out applicatin server as the target.
Currently assumes running as root, but sudoers should allow use of `become: yes` in the future.

### Use:
`ansible-playbook staging.yml --extra-vars="vars_file=someapp.staging.vars.yml"`
`ansible-playbook staging.yml --extra-vars="vars_file=someapp.training.vars.yml"`

### Required Information:
see `roles/setup/README.md`

```yaml
---
# Application pre-deployment variables file
app_name: myapp
user_gid:  123456
user_uid:  987654
app_port: 30600
deploy_users:
  - user1
  - user2
dependency_mysql: no
dependency_resque: no
solr_core_path:
solr_home:
app_hosts:
db_hosts:
solr_host:
apache_hosts:
deploy_root: /hydra-dev
```

Get app gid and uid from ITS' UUID api/tool.

## Expected support existing on targer deployment machines.
all:
* python

database:
* python mysqldb module is required


### Testing with Vagrant using virtual box provider
1. install external ansible roles `ansible-galaxy install -r dependencies.yml`
1. install vagrant
2. install virtual-box
3. run `vagrant up` from project directory
5. Manually provision vagrant host using:
```bash
ansible-playbook --private-key=.vagrant/machines/default/virtualbox/private_key -u vagrant -i inventory/vagrant playbook.predeploy.yml --extra-vars="config_file=./demo.yml"
```


