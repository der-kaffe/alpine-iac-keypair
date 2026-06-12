# alpine-iac-keypair

IAC alpine linux

## Usage

**1. Clone and configure**

```bash
git clone https://github.com/<your-user>/terraform-libvirt-alpine
cd terraform-libvirt-alpine
```

Edit `variables.tf` to match your environment:

```hcl
variable "path_to_image" { default = "/path/to/your/images" }
variable "ip"            { default = "192.168.122.101" }
variable "gateway"       { default = "192.168.122.1" }
```

**2. Deploy**

```bash
terraform init
terraform apply
```

Terraform will automatically:

- Generate a new ED25519 key pair
- Save the private key as `./id_ed25519_alpine` (chmod 0600)
- Save the public key as `./id_ed25519_alpine.pub`
- Provision the VM with the public key injected
**3. Connect**

```bash
ssh -i ./id_ed25519_alpine sysadmin@192.168.122.101
```

**4. Destroy**

```bash
terraform destroy
rm -f id_ed25519_alpine id_ed25519_alpine.pub
```
