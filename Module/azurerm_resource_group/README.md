### Module: azurerm_resource_group

Creates one or more Azure Resource Groups from a map input.

- **Resources**: `azurerm_resource_group.rg` (for_each over `var.rg`)
- **Inputs**:
  - **rg**: map(object)
    - **name_rg**: string — Resource Group name
    - **location**: string — Azure region
- **Outputs**: none

#### Example
```hcl
module "rg" {
  source = "../../Module/azurerm_resource_group"
  rg = {
    rg1 = {
      name_rg  = "example-rg"
      location = "westus"
    }
  }
}
```

#### Notes
- Each key under `rg` becomes one Resource Group.
