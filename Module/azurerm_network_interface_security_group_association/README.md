### Module: azurerm_network_interface_security_group_association

Associates one or more NICs with NSGs.

- **Resources**: `azurerm_network_interface_security_group_association.nsg-nic-assoc`
- **Data sources**: `azurerm_network_interface.nic`, `azurerm_network_security_group.nsg`
- **Inputs**:
  - **nsg-nic-assoc**: map(object)
    - **name_nic**: string — NIC name
    - **name_nsg**: string — NSG name
    - **name_rg**: string — Resource Group name
    - **name_security_rule**: string — used for dependency alignment
- **Outputs**: none

#### Example
```hcl
module "nic-assoc" {
  source = "../../Module/azurerm_network_interface_security_group_association"
  nsg-nic-assoc = {
    assoc1 = {
      name_nsg           = "example-nsg"
      name_rg            = "example-rg"
      name_nic           = "example-nic"
      name_security_rule = "ssh"
    }
  }
}
```
