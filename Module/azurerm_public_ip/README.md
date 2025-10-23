### Module: azurerm_public_ip

Creates one or more Public IPs.

- **Resources**: `azurerm_public_ip.pip`
- **Inputs**:
  - **pip**: map(object)
    - **name_pip**: string — Public IP name
    - **name_rg**: string — Resource Group name
    - **location**: string — Azure region
    - **allocation_method**: string — `Static` or `Dynamic`
- **Outputs**: none

#### Example
```hcl
module "pip" {
  source = "../../Module/azurerm_public_ip"
  pip = {
    pip1 = {
      name_pip          = "example-pip"
      name_rg           = "example-rg"
      location          = "westus"
      allocation_method = "Static"
    }
  }
}
```
