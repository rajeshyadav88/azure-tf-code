### Module: azurerm_virtual_network

Creates one or more Azure Virtual Networks.

- **Resources**: `azurerm_virtual_network.vnet`
- **Inputs**:
  - **vnet**: map(object)
    - **name_vnet**: string — VNet name
    - **name_rg**: string — Resource Group name
    - **location**: string — Azure region
    - **address_space**: list(string) — CIDR blocks
- **Outputs**: none

#### Example
```hcl
module "vnet" {
  source = "../../Module/azurerm_virtual_network"
  vnet = {
    vnet1 = {
      name_vnet     = "example-vnet"
      name_rg       = "example-rg"
      location      = "westus"
      address_space = ["10.0.0.0/16"]
    }
  }
}
```

#### Prerequisites
- The specified Resource Group must already exist.
