### Module: azurerm_storage_account

Creates a storage account. Note: current implementation uses hardcoded values; consider refactoring to accept variables.

- **Resources**: `azurerm_storage_account.stg`
- **Inputs**: none (hardcoded in `main.tf`)
- **Outputs**: none

#### Example
```hcl
module "stg" {
  source = "../../Module/azurerm_storage_account"
}
```

#### Notes
- Update the module to parameterize `name`, `resource_group_name`, `location`, and SKU to reuse.
