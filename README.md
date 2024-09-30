# shardeum_installation_node
Here's the adapted version of the instructions for a GitHub README file:

```markdown
# Shardeum Validator Setup Guide

## Minimum Hardware Requirements
- **250 GB SSD storage**
- **Quad-core CPU (less than 10 years old)** for self-hosting
- **Dual-core CPU** if using newer Xeons/EPYC in hosted environments
- **16 GB RAM** + 4 GB virtual memory recommended
- **Hosting**: 8 GB RAM + 8 GB virtual memory

## Terminal Access
Access the terminal interface for Shell CLI commands:
- **Linux**: `Ctrl + Alt + T`
- **MacOS**: `Cmd + Space`, then type "Terminal"

## Install Package Managers
We will use `curl` to download files:
```bash
# Linux
sudo apt-get install curl

# MacOS
brew install curl
```

## Update Package Managers
```bash
# Linux
sudo apt update

# MacOS
brew update
```

## Install Docker and Docker Compose
```bash
# Install Docker
sudo apt install docker.io

# Verify Docker installation
docker --version # Should return version 20.10.12 or higher

# Install Docker Compose
sudo curl -L "https://github.com/docker/compose/releases/download/1.29.2/docker-compose-$(uname -s)-$(uname -m)" -o /usr/local/bin/docker-compose

# Set permissions
sudo chmod +x /usr/local/bin/docker-compose

# Verify Docker Compose installation
docker-compose --version # Should return version 1.29.2 or higher
```

## Install and Configure Shardeum Validator
Run the following commands:
```bash
curl -O https://raw.githubusercontent.com/shardeum/validator-dashboard/main/installer.sh && chmod +x installer.sh && ./installer.sh
```
Follow the setup prompts:
- Allow bug reporting: `y/n`
- Enable web-based dashboard: `y/n`
- Set a password for the dashboard
- Define custom ports for the web interface (default 8080)
- Set external/internal IP (auto-detected or manual)
- Define P2P ports (default 9001 and 10001)
- Choose installation directory (default `~/.shardeum`)

## Access Validator Dashboard
Open your browser and go to:
```
https://localhost:8080/
```
Ignore the warning and proceed. Log in using the password you set earlier.

## Start Validator
From the dashboard, navigate to the **Maintenance** page and click **Start Node**. Alternatively, use the CLI:
```bash
operator-cli start
```

## Monitor Validator Performance
Check node performance on the **Performance** page. For CLI:
```bash
operator-cli status
```

## Connect Wallet to Shardeum Testnet
Connect your wallet to the Shardeum Validator and stake SHM tokens (minimum 10 SHM) to activate the validator.

## Stake SHM via GUI
1. Go to the **Settings** page.
2. Connect your wallet.
3. Enter the stake amount (e.g., 10 SHM).
4. Click **Stake** and sign the transaction.

## Stake SHM via CLI
For CLI staking, ensure you're in the root directory:
```bash
cd .shardeum
./shell.sh

# Set private key (use testnet tokens only)
export PRIV_KEY=<private_key>
echo $PRIV_KEY

# Stake 10 SHM
operator-cli stake 10

# Check stake info
operator-cli stake_info <wallet_address>

# Unstake SHM
operator-cli unstake
```

## Update Validator
Before updating, stop the validator:
```bash
exit
cd ..
```
Run the update script:
```bash
curl -O https://raw.githubusercontent.com/shardeum/validator-dashboard/main/installer.sh && chmod +x installer.sh && ./installer.sh

# Start the GUI manually if needed
operator-cli gui start
```

## Validator Commands
To see all CLI commands, run:
```bash
operator-cli help
```

## Uninstall Validator
To remove the validator, delete the Shardeum folder:
```bash
rm -rf .shardeum
```

---

For more information, refer to the [Shardeum Validator Documentation](https://shardeum.org/validator/docs).
```

This structure provides a clear, easy-to-follow format suitable for a GitHub README file.
