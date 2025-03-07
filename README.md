# How to deploy the Smart Aquaculture workshop to the Red Hat Demo Platform

## Request a cluster on the Red Hat Demo Platform
- Use the [OpenShift GitOps Blank Environment](https://catalog.demo.redhat.com/catalog/babylon-catalog-prod?category=Open_Environments&item=openshift-cnv.ocp4-cnv-gitops.prod). 
- Click `Order`. 
- Activity: `Practice / Enablement`. 
- Purpose: `Practice for a workshop`. 

## How to deploy the Smart Aquaculture workbench

- Clone the [smart-aquaculture-rhsummit](https://github.com/computate-org/smart-aquaculture-rhsummit) repo to your computer. 
- Connect to your target OpenShift cluster in the CLI with the oc command. 
- Update the `WORKBENCH_NAMES` section of the `roles/overlay-vars/vars/overlay-vars.yaml` file to add as many users as you want to deploy. These vars are preconfigured to work with OpenShift Local by default, so customizations are required for other OpenShift clusters. 
- Inside of the `smart-aquaculture-rhsummit` repo, run the Ansible Playbook to deploy all features. 

```bash
ansible-playbook playbooks/deploy-all.yaml
```

After the Ansible scripts complete, there will be OpenShift Jobs running in each of the workbench-user namespaces to finish setting up the VSCode environments for each user. Any user with the `WORKBENCH_ADMIN: true` variable in the overlay-vars role will have extra tasks performed to load the FIWARE related AI model into the search engine. 
