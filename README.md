# install-terraform-ec2

Here's how you can format your steps for GitHub README in Markdown:

markdown
Copy
Edit
# Installing Terraform on Ubuntu

Ensure that your system is up to date and you have installed the necessary packages: **gnupg**, **software-properties-common**, and **curl**. These packages will help verify HashiCorp's GPG signature and install HashiCorp's Debian package repository.

### 1. Update Your System and Install Dependencies

```bash
sudo apt-get update && sudo apt-get install -y gnupg software-properties-common
2. Install the HashiCorp GPG Key

wget -O- https://apt.releases.hashicorp.com/gpg | \
gpg --dearmor | \
sudo tee /usr/share/keyrings/hashicorp-archive-keyring.gpg > /dev/null
3. Verify the Key's Fingerprint

gpg --no-default-keyring \
--keyring /usr/share/keyrings/hashicorp-archive-keyring.gpg \
--fingerprint
The gpg command will report the key fingerprint:


/usr/share/keyrings/hashicorp-archive-keyring.gpg
-------------------------------------------------
pub   rsa4096 XXXX-XX-XX [SC]
AAAA AAAA AAAA AAAA
uid           [ unknown] HashiCorp Security (HashiCorp Package Signing) <security+packaging@hashicorp.com>
sub   rsa4096 XXXX-XX-XX [E]
Tip:
Refer to the Official Packaging Guide for the latest public signing key. You can also verify the key on HashiCorp Security under Linux Package Checksum Verification.

4. Add the Official HashiCorp Repository to Your System

echo "deb [signed-by=/usr/share/keyrings/hashicorp-archive-keyring.gpg] \
https://apt.releases.hashicorp.com $(lsb_release -cs) main" | \
sudo tee /etc/apt/sources.list.d/hashicorp.list
5. Download the Package Information from HashiCorp

sudo apt update
6. Install Terraform from the New Repository

sudo apt-get install terraform
Tip:
Now that you have added the HashiCorp repository, you can install other tools like Vault, Consul, Nomad, and Packer with the same command.

7. Verify the Installation
Verify that the installation worked by opening a new terminal session and listing Terraform's available subcommands.


terraform -help
You should see output similar to:


Usage: terraform [-version] [-help] <command> [args]

The available commands for execution are listed below.
The most common, useful commands are shown first, followed by
less common or more advanced commands. If you're just getting
started with Terraform, stick with the common commands. For the
other commands, please read the help and docs before usage.
##...
Add any subcommand to terraform -help to learn more about what it does and available options.


terraform -help plan
Troubleshoot
If you get an error that Terraform could not be found, it means your PATH environment variable was not set up properly. Please go back and ensure that your PATH variable contains the directory where Terraform was installed.

8. Enable Tab Completion
If you use either Bash or Zsh, you can enable tab completion for Terraform commands. To enable autocomplete, first ensure that a config file exists for your chosen shell.


touch ~/.bashrc
Then install the autocomplete package:


terraform -install-autocomplete
Once the autocomplete support is installed, you will need to restart your shell.


touch ~/.zshrc
Then install the autocomplete package:

terraform -install-autocomplete
Once the autocomplete support is installed, you will need to restart your shell.

You have now successfully installed and configured Terraform on your Ubuntu instance! Let me know if you run into any issues.

This markdown format will ensure that your instructions are properly formatted when viewed on GitHub.






