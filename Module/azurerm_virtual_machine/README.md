### Module: azurerm_virtual_machine

Creates one or more Linux Virtual Machines, retrieving credentials from Key Vault and attaching an existing NIC.

- **Resources**: `azurerm_linux_virtual_machine.vm`
- **Data sources**: `azurerm_key_vault.kv`, `azurerm_key_vault_secret.username`, `azurerm_key_vault_secret.password`, `azurerm_network_interface.nic`
- **Inputs**:
  - **vm**: map(object)
    - **name_vm**: string — VM name
    - **name_rg**: string — Resource Group name
    - **location**: string — Azure region
    - **vm_size**: string — e.g., `Standard_F2`
    - **name_username**: string — Key Vault secret name for username
    - **name_password**: string — Key Vault secret name for password
    - **name_nic**: string — Existing NIC name
    - **name_kv**: string — Key Vault name hosting the secrets
- **Outputs**: none

#### Example
```hcl
module "vm" {
  source = "../../Module/azurerm_virtual_machine"
  vm = {
    vm1 = {
      name_vm       = "example-vm"
      name_rg       = "example-rg"
      location      = "westus"
      vm_size       = "Standard_F2"
      name_username = "username-secret"
      name_password = "password-secret"
      name_nic      = "example-nic"
      name_kv       = "example-kv"
    }
  }
}
```

#### Notes
- Password authentication is enabled; consider SSH for production.
