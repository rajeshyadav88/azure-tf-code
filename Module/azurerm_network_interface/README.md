### Module: azurerm_network_interface

Creates one or more Network Interfaces and wires them to existing Public IPs and Subnets.

- **Resources**: `azurerm_network_interface.nic`
- **Data sources**: `azurerm_public_ip.pip`, `azurerm_subnet.frontend_subnet`
- **Inputs**:
  - **nic**: map(object)
    - **name_nic**: string — NIC name
    - **location**: string — Azure region
    - **name_rg**: string — Resource Group name
    - **name_ip**: string — IP configuration name
    - **private_ip_address_allocation**: string — e.g., `Dynamic`
    - **name_pip**: string — Existing Public IP name
    - **name_snet**: string — Existing Subnet name
    - **name_vnet**: string — Parent VNet name
- **Outputs**: none

#### Example
```hcl
module "nic" {
  source = "../../Module/azurerm_network_interface"
  nic = {
    nic1 = {
      name_nic                      = "example-nic"
      location                      = "westus"
      name_rg                       = "example-rg"
      name_ip                       = "vm-ipcfg"
      private_ip_address_allocation = "Dynamic"
      name_pip                      = "example-pip"
      name_snet                     = "frontend-subnet"
      name_vnet                     = "example-vnet"
    }
  }
}
```

#### Prerequisites
- Public IP and Subnet must already exist.
