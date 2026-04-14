# Azure Resource Group Terraform Module

[![Terraform](https://img.shields.io/badge/Terraform-1.x-623CE4.svg)](https://terraform.io)
[![Azure](https://img.shields.io/badge/Azure-Resource%20Manager-0078D4.svg)](https://azure.microsoft.com)
[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](https://opensource.org/licenses/MIT)

This repository provides a Terraform module for provisioning an Azure Resource Group, serving as a foundational component for Azure infrastructure deployments.

## Table of Contents

- [Overview](#overview)
- [Prerequisites](#prerequisites)
- [Usage](#usage)
- [Inputs](#inputs)
- [Outputs](#outputs)
- [Resources](#resources)
- [Customization](#customization)
- [Testing](#testing)
- [Contributing](#contributing)
- [License](#license)

## Overview

This Terraform configuration establishes the necessary provider setup and creates a single Azure Resource Group. It is designed to be modular and can be integrated into larger infrastructure-as-code projects.

The module includes:
- Terraform provider requirements specification
- Azure Resource Manager provider configuration
- Resource Group resource definition

## Prerequisites

Before deploying this module, ensure the following are in place:

- **Terraform**: Version 1.0 or later, compatible with AzureRM provider 4.68.0
- **Azure CLI**: Installed and configured with appropriate authentication (`az login`)
- **Azure Permissions**: Contributor or Owner role on the target subscription
- **Azure Subscription**: Active subscription with sufficient quota for resource groups

## Usage

### Basic Deployment

1. **Clone the Repository**:
   ```bash
   git clone <repository-url>
   cd <repository-directory>
   ```

2. **Initialize Terraform**:
   ```bash
   terraform init
   ```

3. **Review Deployment Plan**:
   ```bash
   terraform plan
   ```

4. **Apply Configuration**:
   ```bash
   terraform apply
   ```

5. **Cleanup Resources** (when no longer needed):
   ```bash
   terraform destroy
   ```

### Integration with Other Modules

This resource group can serve as a foundation for additional Azure resources. Reference the resource group in other Terraform configurations using:

```hcl
data "azurerm_resource_group" "example" {
  name = "example-resources"
}
```

## Inputs

| Name | Description | Type | Default | Required |
|------|-------------|------|---------|----------|
| resource_group_name | The name of the Azure Resource Group | `string` | `"example-resources"` | No |
| location | The Azure region for the Resource Group | `string` | `"West Europe"` | No |

## Outputs

| Name | Description |
|------|-------------|
| resource_group_id | The ID of the created Resource Group |
| resource_group_name | The name of the created Resource Group |
| resource_group_location | The location of the created Resource Group |

## Resources

This module creates the following Azure resources:

- **azurerm_resource_group.example**: A logical container for Azure resources, providing scope for access control, monitoring, and billing.

## Customization

### Modifying Resource Properties

Edit the `resource` block in `main.tf` to customize:

- **Name**: Ensure uniqueness within your subscription
- **Location**: Choose from available Azure regions
- **Tags**: Add metadata for organization and cost tracking

### Advanced Configuration

For production deployments, consider:
- Implementing remote state storage
- Adding resource locks for critical environments
- Integrating with Azure Policy for governance

## Testing

Run the following commands to validate the configuration:

```bash
# Format code
terraform fmt -check

# Validate syntax
terraform validate

# Run tests (if using Terratest or similar)
# Add your testing framework commands here
```

## Contributing

We welcome contributions to improve this module. Please follow these guidelines:

1. Fork the repository
2. Create a feature branch (`git checkout -b feature/amazing-feature`)
3. Commit your changes (`git commit -m 'Add amazing feature'`)
4. Push to the branch (`git push origin feature/amazing-feature`)
5. Open a Pull Request

### Development Standards

- Follow Terraform best practices
- Include comprehensive documentation
- Add tests for new functionality
- Ensure backward compatibility

## License

This project is licensed under the MIT License - see the [LICENSE](LICENSE) file for details.

---

For questions or support, please open an issue in this repository.
