# terraform-self-hosted-adf-integration-runtime
Terraform component stands up a self-hosted Azure Data Factory integration runtime on an Azure VM

## Getting started
Simply run terraform plan and apply
```bash
terraform init
terraform plan && terraform apply -auto-approve
```

## Cleanup
```bash
terraform destroy -auto-approve
```

## Useful links
* [Using terraform with Azure VM extensions](https://jackstromberg.com/2018/11/using-terraform-with-azure-vm-extensions/)
* [Azure VM extension schema for Windows custom scripts](https://docs.microsoft.com/en-us/azure/virtual-machines/extensions/custom-script-windows)
* [Create and configure a self-hosted integration runtime](https://docs.microsoft.com/en-us/azure/data-factory/create-self-hosted-integration-runtime#setting-up-a-self-hosted-integration-runtime)
* [Create self host IR and make it workable in azure VMs](https://github.com/Azure/azure-quickstart-templates/tree/master/101-vms-with-selfhost-integration-runtime)

## Alternative using combination az cli and ARM template
```bash
az deployment group create  \
    --resource-group self-hosted-adf-ir-poc \
    --name rollout01 \
    --template-uri https://raw.githubusercontent.com/Azure/azure-quickstart-templates/master/101-vms-with-selfhost-integration-runtime/azuredeploy.json \
    --parameters @azuredeploy.parameters.json
```
Note: this approach requires prerequisite resources. Inspect `azuredeploy.parameters.json` for more detail.
