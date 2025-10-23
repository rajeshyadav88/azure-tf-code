### Azure IaC Modules and Environment

This repository contains reusable Terraform modules and a sample environment composition under `Environment/Dev`.

#### Modules
- `Module/azurerm_resource_group` — Create Resource Groups
- `Module/azurerm_virtual_network` — Create Virtual Networks
- `Module/azurerm_subnet` — Create Subnets
- `Module/azurerm_public_ip` — Create Public IPs
- `Module/azurerm_network_interface` — Create NICs attached to PIP and Subnet
- `Module/azurerm_network_security_group` — Create NSGs with inbound rule
- `Module/azurerm_network_interface_security_group_association` — Associate NICs to NSGs
- `Module/azurerm_key_vault` — Create Key Vaults and access policies
- `Module/azurerm_key_vault_secret_username` — Create username secrets
- `Module/azurerm_key_vault_secret_password` — Create password secrets
- `Module/azurerm_virtual_machine` — Create Linux VMs using NIC + KV secrets
- `Module/azurerm_storage_account` — Example storage account (hardcoded)

Each module has its own README with inputs, resources, data sources, and example usage.

#### Environment: Dev
See `Environment/Dev/README.md` for provider configuration, variable structure, and end-to-end usage with `terraform init/plan/apply/destroy`.

#### Quickstart
```bash
cd Environment/Dev
terraform init
terraform plan -var-file="terraform.tfvars"
terraform apply -var-file="terraform.tfvars"
```

#### Conventions
- All modules accept a map input and use `for_each` to create multiple resources.
- Inputs follow a consistent naming pattern: `name_*`, `location`, and references to related resources.
- Keep secrets in Key Vault. Avoid plaintext in `terraform.tfvars` for production.
