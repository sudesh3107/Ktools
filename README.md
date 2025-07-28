# Ktools
Installing Kali tools over Debian Based distros.
# How to Install Kali Linux Tools on Debian

 There are three methods to install Kali Linux penetration testing tools on Debian.

## ⚠️ Important Notes
- Adding Kali repositories **may cause system instability** due to package conflicts.
- For production systems, **use Docker (Method 3)** instead.
- Kali tools often require **root privileges** - use with caution.


## Method 1: Add Kali Repositories (Most Comprehensive)

### Step 1: Add Kali Repo & Key
```bash
# Add Kali repository
echo "deb http://http.kali.org/kali kali-rolling main non-free contrib" | sudo tee /etc/apt/sources.list.d/kali.list

# Import GPG key
wget -qO - https://archive.kali.org/archive-key.asc | sudo apt-key add -

# Update packages
sudo apt update
```

### Step 2: Install Tools
```bash
# Install ALL tools (10GB+ disk space)
sudo apt install kali-linux-everything -y
```


## OR install specific categories:
```bash
sudo apt install kali-tools-top10        # Top 10 essential tools
sudo apt install kali-tools-web          # Web app testing
sudo apt install kali-tools-wireless     # Wi-Fi hacking
sudo apt install kali-tools-forensics    # Forensic tools

```
### Step 3: Prevent Conflicts (Recommended)
```bash
# Block updates for critical packages
sudo apt-mark hold <package-name>
```

## Method 2: Manual Tool Installation (Safer)
```bash
sudo apt install nmap metasploit-framework wireshark aircrack-ng burpsuite -y
```

## Method 3: Docker Container (Safest Option)

```bash
# Install Docker
sudo apt install docker.io -y

# Run Kali container
docker run -it kalilinux/kali-rolling /bin/bash
```

# Inside container:
```bash
apt update && apt install kali-linux-headless -y
```

#### Uninstallation

```bash
# Remove Kali tools
sudo apt remove kali-linux-everything

# Purge residual files
sudo apt autoremove -y && sudo apt clean
```
