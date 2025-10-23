### Module: azurerm_key_vault_secret_username

Creates one or more username secrets in Key Vault.

- **Resources**: `azurerm_key_vault_secret.username`
- **Data sources**: `azurerm_key_vault.kv`
- **Inputs**:
  - **kvsu**: map(object)
    - **username**: string — Secret name
    - **user_value**: string — Secret value
    - **name_kv**: string — Key Vault name
    - **name_rg**: string — Resource Group name
- **Outputs**: none

#### Example
```hcl
module "kvsu" {
  source = "../../Module/azurerm_key_vault_secret_username"
  kvsu = {
    u1 = {
      username   = "username-secret"
      user_value = "devopsadmin"
      name_kv    = "example-kv"
      name_rg    = "example-rg"
    }
  }
}
```
