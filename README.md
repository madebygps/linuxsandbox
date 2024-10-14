# Linux Sandbox

This Terraform configuration sets up a Linux virtual machine (VM) in Azure with the following features:

- Auto-shutdown at a specified time (in UTC, 24-hour format)
- Restricted access to specified IP addresses
- SSH public key stored in an Azure Key Vault
- Configurable VM size and Ubuntu version

## Prerequisites

- [Terraform](https://www.terraform.io/downloads.html) installed
- Azure subscription
- SSH public key store in Keyvault secret

## Configuration

Before running the Terraform scripts, you need to configure the following variables in `main.tf`:

- `resource_group_name`: Name of the resource group
- `location`: Azure region for resources (default: `eastus`)
- `admin_username`: Admin username for the VM
- `vm_size`: Size of the VM (default: `Standard_B1ls`)
- `ubuntu_version`: Ubuntu version for the VM (default: `22.04-LTS`)
- `auto_shutdown_time`: Time to auto-shutdown the VM (in UTC, 24-hour format, default: `2200`)
- `allowed_ip_addresses`: List of IP addresses allowed to connect to the VM
- `key_vault_name`: Name of the Azure Key Vault containing the SSH public key
- `key_vault_rg`: Resource group of the Azure Key Vault
- `ssh_public_key_secret_name`: Name of the secret in Key Vault containing the SSH public key

## Usage

1. Initialize Terraform:

    ```sh
    terraform init
    ```

2. Plan the deployment:

    ```sh
    terraform plan
    ```

3. Apply the deployment:

    ```sh
    terraform apply
    ```

4. To destroy the resources:

    ```sh
    terraform destroy
    ```

## Notes

- Ensure that the Azure Key Vault and the secret containing the SSH public key are already created and accessible.
- The auto-shutdown feature helps in saving costs by shutting down the VM at the specified time.

## License

This project is licensed under the MIT License. 