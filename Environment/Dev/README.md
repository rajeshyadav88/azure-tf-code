### Environment: Dev

Composes all modules to provision a sample environment.

#### Files
- `provider.tf`: Configures AzureRM provider (v4.14.0). Ensure subscription is correct.
- `variable.tf`: Declares variables consumed by `main.tf`.
- `terraform.tfvars`: Sample values for all modules (maps of objects).
- `main.tf`: Wires modules together using `depends_on` for ordering.

#### Variables
Declared in `variable.tf` as map-typed groupings. Each corresponds to a module input:
- `rg`, `vnet`, `snet`, `pip`, `nic`, `kv`, `kvsu`, `kvsp`, `vm`, `nsg`, `nsg-nic-assoc`

See `terraform.tfvars` for example structures:
```hcl
rg = {
  rg1 = { name_rg = "zenai-rg", location = "westus" }
}
# ... others similar to this pattern
```

#### Usage
```bash
# initialize
terraform init

# validate and plan
terraform validate
terraform plan -var-file="terraform.tfvars"

# apply
terraform apply -var-file="terraform.tfvars"

# destroy
terraform destroy -var-file="terraform.tfvars"
```

#### Module Wiring
```hcl
module "rg"   { source = "../../Module/azurerm_resource_group" rg = var.rg }
module "vnet" { source = "../../Module/azurerm_virtual_network" depends_on = [module.rg] vnet = var.vnet }
module "snet" { source = "../../Module/azurerm_subnet" depends_on = [module.vnet] snet = var.snet }
module "pip"  { source = "../../Module/azurerm_public_ip" depends_on = [module.rg] pip = var.pip }
module "nic"  { source = "../../Module/azurerm_network_interface" depends_on = [module.pip, module.snet] nic = var.nic }
module "kv"   { source = "../../Module/azurerm_key_vault" depends_on = [module.rg, module.pip] kv = var.kv }
module "vm"   { source = "../../Module/azurerm_virtual_machine" depends_on = [module.nic, module.kv] vm = var.vm }
module "nsg"  { source = "../../Module/azurerm_network_security_group" depends_on = [module.vm] nsg = var.nsg }
module "assoc"{ source = "../../Module/azurerm_network_interface_security_group_association" depends_on = [module.nic, module.nsg, module.vm] nsg-nic-assoc = var.nsg-nic-assoc }
module "kvsu" { source = "../../Module/azurerm_key_vault_secret_username" depends_on = [module.kv] kvsu = var.kvsu }
module "kvsp" { source = "../../Module/azurerm_key_vault_secret_password" depends_on = [module.kv] kvsp = var.kvsp }
```

#### Notes
- `azurerm_storage_account` example module uses hardcoded values; parameterize before production use.
- Key Vault access policies use the current caller's tenant/object id. Ensure the executing principal has permissions.
