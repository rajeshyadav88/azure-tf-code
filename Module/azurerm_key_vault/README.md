### Module: azurerm_key_vault

Creates one or more Azure Key Vaults and grants current principal access.

- **Resources**: `azurerm_key_vault.kv`
- **Data sources**: `azurerm_client_config.current`
- **Inputs**:
  - **kv**: map(object)
    - **name_kv**: string — Key Vault name
    - **name_rg**: string — Resource Group name
    - **location**: string — Azure region
    - **sku_name**: string — e.g., `standard`
    - **key_permissions**: list(string)
    - **secret_permissions**: list(string)
- **Outputs**: none

#### Example
```hcl
module "kv" {
  source = "../../Module/azurerm_key_vault"
  kv = {
    kv1 = {
      name_kv            = "example-kv"
      name_rg            = "example-rg"
      location           = "westus"
      sku_name           = "standard"
      secret_permissions = ["Get", "List", "Set"]
      key_permissions    = ["Get", "List", "Create"]
    }
  }
}
```
