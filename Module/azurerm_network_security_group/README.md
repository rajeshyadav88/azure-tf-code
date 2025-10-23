### Module: azurerm_network_security_group

Creates one or more Network Security Groups with an inbound rule.

- **Resources**: `azurerm_network_security_group.nsg`
- **Inputs**:
  - **nsg**: map(object)
    - **name_nsg**: string — NSG name
    - **name_rg**: string — Resource Group name
    - **location**: string — Azure region
    - **name_security_rule**: string — Security rule name
    - **destination_port_range**: string — e.g., `22`
- **Outputs**: none

#### Example
```hcl
module "nsg" {
  source = "../../Module/azurerm_network_security_group"
  nsg = {
    nsg1 = {
      name_nsg               = "example-nsg"
      name_rg                = "example-rg"
      location               = "westus"
      name_security_rule     = "ssh"
      destination_port_range = "22"
    }
  }
}
```
