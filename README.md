
# Tomas' review of Packet Terraform/Ansible work

These are notes for work review for Packet from August and September 2017.

## Terraform

### Packngo

The golang API client for Packet API is the first step before features can be added to Terraform. I got write access to github repo (Thanks!).

#### Terraform provider

Since early summer, Terraform providers have been moved to [separate repos](https://github.com/terraform-providers). Before, they used to be in the TF main repository I guess.

Packet provider in https://github.com/terraform-providers/terraform-provider-packet. I got write access (Thanks!).




### A pattern: Adding device feature F to Terraform

F ∈ {[hw reservation](https://help.packet.net/technical/deployment-options/reserved-hardware), [custom subnet size](https://help.packet.net/technical/networking/custom-subnet-size), [custom partitioning and raid](https://help.packet.net/technical/storage/custom-partitioning-raid), [iPXE boot](https://help.packet.net/technical/infrastructure/custom-ipxe)}

From client point-of-view, the feature is usually a parameter for the device creating POST HTTP request - that makes it trivial to add to API client. However, Terraform likes to compare resource declarations from .tf files with the resorurce data that come from the API. If there is difference between what's declared and what's obtained from the API, TF will destroy and re-create the resource.


## Ansible

Hanging there:

- Module subnet assignment (floating IP addresses): https://github.com/ansible/ansible/pull/23133
- Module for projects: https://github.com/ansible/ansible/pull/27113
- Module for volumes: https://github.com/ansible/ansible/pull/27842
- Module for volume attachments: https://github.com/ansible/ansible/pull/27843

Few improvements have made it to Ansible 2.4: http://docs.ansible.com/ansible/latest/packet_device_module.html
