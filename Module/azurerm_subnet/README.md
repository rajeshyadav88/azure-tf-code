### Module: azurerm_subnet

Creates one or more Subnets inside an existing Virtual Network.

- **Resources**: `azurerm_subnet.frontend_subnet`
- **Inputs**:
  - **snet**: map(object)
    - **name_snet**: string — Subnet name
    - **name_vnet**: string — Parent VNet name
    - **name_rg**: string — Resource Group name
    - **address_prefixes**: list(string) — CIDR prefixes
- **Outputs**: none

#### Example
```hcl
module "snet" {
  source = "../../Module/azurerm_subnet"
  snet = {
    snet1 = {
      name_snet        = "frontend-subnet"
      name_vnet        = "example-vnet"
      name_rg          = "example-rg"
      address_prefixes = ["10.0.1.0/26"]
    }
  }
}
```

#### Prerequisites
- The referenced VNet and Resource Group must already exist.
