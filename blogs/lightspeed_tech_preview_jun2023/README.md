# Welcome to the Ansible Lightspeed with IBM Watson Code Assistant Technical Preview

## Overview

[**Blog Link**](https://www.ansible.com/blog/welcome-to-the-ansible-lightspeed-technical-preview)

[**Instruction video**](https://youtu.be/yfXcGB7l0II)

In the June 2023, Ansible announced the technical preview release of [Ansible LightSpeed with IBM Watson Code Assistant](https://www.redhat.com/en/engage/project-wisdom). This blog provides guidance on enabling Ansible Lightspeed in Visual Studio code and generating Ansible task suggestions.

![install_extension](./img/install_extension.gif)

![gh_login](./img/gh_login.gif)

![accept_t_c](./img/accept_t_c.gif)

## Blog example content

The blog used an Ansible Playbook to demonstrate some of Ansible LightSpeed's capabilities. You can watch the [recorded video](https://youtu.be/yfXcGB7l0II) for a full demonstration.

>ℹ️ **Note**
>
> Watson Code Assistant, the Large Language Model used to generate Ansible content suggestions, continues to learn and improve, and suggestions will differ as later versions of the model are released. The Ansible task suggestions generated in the blog will therefore differ from the time of publication.

### Ansible Playbook examples

#### Ansible vault password

```yaml
ansible123!
```

#### Playbook files

[Deploy Cockpit on RHEL](./deploy_monitoring.yml)  
[Provision AWS instance and initial instance configuration](./provision_instances.yml)

![generate_suggestion](./img/generate_suggestion.gif)

![best_practices](./img/second_task.gif)

![remaining_tasks](./img/3_4_task.gif)

![context](./img/module_defaults.gif)

![training_matches](./img/training_matches.gif)
