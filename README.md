# terraform-google-memcached

This is a module to bring up a memcached.  

memcached-terraform-gcp  
https://docs.google.com/spreadsheets/d/1F5fqGbsQDrQjZVB2E1dk-zr5OUj-Mb6P55F_kL02pZE/edit?folder=0AGzfMaGH7wbJUk9PVA#gid=0  

Deployment of a Highly Available Memcached Cluster on Oracle Cloud Infrastructure using Terraform  
https://blogs.oracle.com/cloud-infrastructure/deploying-a-highly-available-memcached-cluster-on-oracle-cloud-infrastructure  

Memcached Infrastructure  
https://github.com/abannang/OCI/tree/master/memcached-OCI  

## Inputs

| Name | Description | Type | Default | Required |
|------|-------------|:----:|:-----:|:-----:|
| location_code | A  code representing a single character for the type of physical location ('g' for Google cloud) plus a short string indicating zone or location (e.x. gusw1, guse1, gase1, etc...). This will be used as the first segment of the machine's hostname | string | - | yes |
| env | Environment | string | `` | yes |
| app_name | The third segment of the machine's hostname, referencing the major application or project name | string | - | yes |
| img_src_project | source project where image resides | string | `centos-cloud` | yes |
| image_name | centos7 base image name | string | `` | yes |
| memcached_ips | List of IP addresses to use for memcached instances. | list | - | yes |
| project_name | Project Name | string | `` | yes |
| app_tags | Application tags | string | `<list>` | no |
| machine_type | memcached machine type | string | `n1-standard-2` | no |
| allow_stopping_for_update | Whether you will allow Terraform to stop an instance to update it (e.x. service account update) | string | true | no |
| boot_disk_size | boot_disk_size | string | 100 | no |
| boot_disk_type | boot_disk_type | string | pd-ssd | no |
| subnetwork | Subnet to deploy to | string | `` | yes |
| service_account |  | map | `<map>` | yes |

## Verify

### On your instance type below command :
### ps -eaf | grep memcached
### and it should give below output :
/usr/bin/memcached -u memcached -p 11211 -m 2048 -c 1024 -t 4 -v >> /data1/applogs/memcached/memcached.log 2>&1
