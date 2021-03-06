# Ansible role for Heketi

Install Heketi for managing GlusterFS volumes

## Variables

```yaml
---

heketi_install_arch: 'amd64'
heketi_install_version: '9.0.0'
heketi_dl_base_url: "https://github.com/heketi/heketi/releases/download"

### Download variables
dl_url: "{{ heketi_dl_base_url }}/v{{ install_version }}/heketi-v{{ install_version }}.linux.{{ install_arch }}.tar.gz"
dl_c_url: "{{ heketi_dl_base_url }}/v{{ install_version }}/heketi-client-v{{ install_version }}.linux.{{ install_arch }}.tar.gz"
dl_file: "/tmp/heketi-v{{ install_version }}.linux.{{ install_arch }}.tar.gz"
dl_c_file: "/tmp/heketi-client-v{{ install_version }}.linux.{{ install_arch }}.tar.gz"

heketi_install_dir: '/etc/heketi'
heketi_install_client_dir: '/etc/heketi-client'

### Systemd variables
heketi_service_template: "templates/heketi.service.j2"
heketi_service_unit_dir: "/lib/systemd/system"
heketi_service_filename: "heketi.service"
heketi_service_working_dir: '/var/lib/heketi'
heketi_service_user: 'heketi'

heketi_install: true
heketi_configure: true
### Set true if you want to initialize glusterfs topology with heketi
heketi_inititalize_cluster: false

### Heketi configuration vairables
heketi_install_command_link: '/usr/bin/heketi'
heketi_cli_install_command_link: '/usr/bin/heketi-cli'
heketi_config_dir: '/etc/heketi'
heketi_config_client_dir: '/etc/heketi-client'
heketi_config_filename: 'heketi.conf'
heketi_config_client_filename: 'heketi-topology.json'
heketi_config_topology_nodes: []
heketi_data_dir: '/var/lib/heketi'
heketi_service_unit_description: 'Heketi Storage Provisioning Server'
heketi_service_pid_file: '/var/run/heketi.pid'
heketi_http_port: '8080'
heketi_tls_enabled: false
heketi_cert_file: ''
heketi_key_file: ''
heketi_use_auth: false
heketi_admin_token: 'eyJ0eXAiOiJKV1QiLCJhbGciOiJIUzI1NiJ9.eyJpc3MiOiJLdWJlQ2xvdWQgU0RTIFRva2VuIiwiaWF0IjoxNTc3MDE2Mzg5LCJleHAiOjE5MjQwODUxODksImF1ZCI6InNkcy5sYWIua3ViZS1jbG91ZC5pbnQiLCJzdWIiOiJzZHMtYWRtaW5AbGFiLmt1YmUtY2xvdWQuaW50IiwiR2l2ZW5OYW1lIjoiQWRtaW5pc3RyYXRvciIsIlN1cm5hbWUiOiJIRUtFVEkiLCJFbWFpbCI6InNkcy1hZG1pbkBsYWIua3ViZS1jbG91ZC5pbnQiLCJSb2xlIjoiQWRtaW5pc3RyYXRvciJ9.jPmSkMNoYXrkRLTc_3tpKGvNDcG-V5fqdFLq7eoPABQ'
heketi_user_token: 'eyJ0eXAiOiJKV1QiLCJhbGciOiJIUzI1NiJ9.eyJpc3MiOiJLdWJlQ2xvdWQgU0RTIFRva2VuIiwiaWF0IjoxNTc3MDE2Mzg5LCJleHAiOjE5MjQwODUxODksImF1ZCI6InNkcy5sYWIua3ViZS1jbG91ZC5pbnQiLCJzdWIiOiJzZHMtdXNlckBsYWIua3ViZS1jbG91ZC5pbnQiLCJHaXZlbk5hbWUiOiJVc2VyIiwiU3VybmFtZSI6IkhFS0VUSSIsIkVtYWlsIjoic2RzLXVzZXJAbGFiLmt1YmUtY2xvdWQuaW50IiwiUm9sZSI6IlVzZXIifQ.THWpcbG3NNhiPuCKmJyJ6UT1AQVeAfvuz4CP85NTr8A'
heketi_backup_db_to_kube_secret: false
heketi_profiling: false
heketi_node_fstab: '/etc/fstab'
heketi_node_pv_data_alignment: '256K'
heketi_node_vg_physicalextentsize: '4MB'
heketi_node_lv_chunksize: '256K'
heketi_node_xfs_sw: ''
heketi_node_xfs_su: ''
heketi_node_backup_lvm_metadata: false
heketi_node_cli_timeout: '10'
heketi_node_debug_umount_failures: true
heketi_db_name: 'heketi.db'
heketi_node_refresh_time_monitor_gluster: 120
heketi_node_start_time_monitor_gluster: 10
heketi_loglevel: 'debug'
heketi_node_auto_create_block_hosting_volume: true
heketi_node_block_hosting_volume_size: 500
heketi_node_block_hosting_volume_options: 'group gluster-block'
heketi_node_pre_request_volume_options: ''
heketi_node_post_request_volume_options: ''
heketi_node_ssh_command_sudo: true
heketi_node_brick_max_size_gb: 1024
heketi_node_brick_min_size_gb: 1
heketi_node_max_bricks_per_volume: 33

### SSH variables
heketi_node_executor: 'ssh'
heketi_node_ssh_port: '22'
heketi_node_source_ssh_keyfile: "keys/heketi_rsa"
heketi_node_source_ssh_keyfile_pub: "keys/heketi_rsa.pub"
heketi_node_ssh_keyfile: "/etc/ssh/heketi_rsa"
```

## Dependencies
None

## Examples
 - [playbook](examples/playbook.yaml)
 - [inventory](examples/inventory.yaml)

## License

MIT
