### Module: azurerm_key_vault_secret_password

Creates one or more password secrets in Key Vault.

- **Resources**: `azurerm_key_vault_secret.password`
- **Data sources**: `azurerm_key_vault.kv`
- **Inputs**:
  - **kvsp**: map(object)
    - **pswdname**: string — Secret name
    - **pas_value**: string — Secret value
    - **name_kv**: string — Key Vault name
    - **name_rg**: string — Resource Group name
- **Outputs**: none

#### Example
```hcl
module "kvsp" {
  source = "../../Module/azurerm_key_vault_secret_password"
  kvsp = {
    p1 = {
      pswdname  = "password-secret"
      pas_value = "Passw@rd123"
      name_kv   = "example-kv"
      name_rg   = "example-rg"
    }
  }
}
```
