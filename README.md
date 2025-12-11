# Oracle Anti-Idle System 🛡️

Never let your Oracle Cloud Free Tier instance get terminated due to inactivity!

**Author:** Matt Blumberg

## 🚀 Features

- **24/7 Automatic Operation** - Keeps your instance active continuously
- **Smart Resource Management** - Configurable CPU and memory usage
- **Auto-Recovery** - Automatically restarts if stopped or crashed
- **Health Monitoring** - System health checks before operations
- **Backup & Restore** - Configuration backup management
- **Systemd Integration** - Monitoring service for ultimate reliability
- **Beautiful CLI** - Modern menu-driven interface with ASCII art
- **Multi-OS Support** - Works on Ubuntu/Debian, Oracle Linux, RHEL, and CentOS

## 📋 Requirements

- **Supported Operating Systems:**
  - Ubuntu/Debian (tested on Ubuntu 20.04/22.04)
  - Oracle Linux 7, 8, 9
  - RHEL/CentOS 7, 8, 9
- Root/sudo privileges
- systemd (init systems like SysVinit are not supported)
- Oracle Cloud Free Tier instance (or any compatible VPS)

## ⚡ Quick Start

### One-Line Installation

```bash
wget https://raw.githubusercontent.com/mattblumberg/oracle-anti-idle/main/oracle-anti-idle.sh && \
sudo chmod +x oracle-anti-idle.sh && \
sudo ./oracle-anti-idle.sh
```

### Manual Installation

1. Clone the repository:
```bash
git clone https://github.com/mattblumberg/oracle-anti-idle.git
cd oracle-anti-idle
```

2. Make the script executable:
```bash
chmod +x oracle-anti-idle.sh
```

3. Run the script:
```bash
sudo ./oracle-anti-idle.sh
```

## 🎯 Usage

### Interactive Menu

Simply run the script to access the interactive menu:

```bash
sudo ./oracle-anti-idle.sh
```

### Menu Options

1. **Toggle Anti-Idle** - Start/stop the anti-idle system
2. **Configure Parameters** - Customize CPU and memory usage
3. **Show Status** - View detailed system status
4. **Quick Setup** - Guided setup with presets
5. **Advanced Settings** - Access backup, monitoring, and more
6. **Health Check** - Perform system health assessment
7. **Help** - View help information
0. **Exit** - Exit the program

### Configuration Presets

- **Light** (10% CPU, 10% Memory) - Minimal impact
- **Standard** (15% CPU, 15% Memory) - Recommended ✓
- **Heavy** (25% CPU, 25% Memory) - Maximum prevention
- **Custom** - Set your own values

## 🔧 How It Works

The script uses `stress-ng` to generate controlled CPU and memory load, managed by `supervisor` for reliability. This activity prevents Oracle Cloud from marking your instance as idle.

### Components

1. **stress-ng** - Generates the actual CPU/memory load
2. **supervisor** - Manages stress processes and ensures they keep running
3. **systemd** - (Optional) Monitoring service for additional reliability
4. **watchdog** - Internal process monitor

## 🛡️ Reliability Features

### Auto-Recovery
- Processes automatically restart if they crash
- Supervisor restarts if it stops
- Systemd monitoring service (optional)

### Health Monitoring
- CPU temperature monitoring
- Memory availability checks
- Disk space validation
- Network connectivity verification
- Load average monitoring

### Backup System
- Automatic configuration backups
- Easy restore functionality
- Keeps last 5 backups

### Logging
- Comprehensive logging system
- Automatic log rotation (>50MB)
- Separate error and health logs
- Debug mode available

## 📊 Resource Usage

Default settings use minimal resources:
- **CPU**: 4 cores at 15% load each (adjustable)
- **Memory**: 15% of total RAM (adjustable)
- **Disk**: ~10MB for logs

## 🔐 Security

- Runs with root privileges (required for supervisor)
- No external dependencies except Ubuntu packages
- No data collection or external communication
- All operations are local to your instance

## 🐛 Troubleshooting

### Script won't start
```bash
# Check if running as root
sudo ./oracle-anti-idle.sh

# Check system compatibility
cat /etc/os-release
```

### Supervisor not found
```bash
# The script auto-installs dependencies, but if needed:

# Ubuntu/Debian:
sudo apt-get update
sudo apt-get install supervisor stress-ng

# Oracle Linux/RHEL/CentOS (requires EPEL):
sudo dnf install epel-release
sudo dnf install supervisor stress-ng
```

### High resource usage
- Use the Configure Parameters option to reduce CPU/memory usage
- Try the "Light" preset for minimal impact

### Checking logs
```bash
# View system log
sudo tail -f /var/log/oracle-anti-idle/anti-idle.log

# View error log
sudo tail -f /var/log/oracle-anti-idle/error.log

# View health log
sudo tail -f /var/log/oracle-anti-idle/health.log
```

## 🤝 Contributing

Contributions are welcome! Please feel free to submit a Pull Request.

## 📄 License

This project is licensed under the MIT License - see the [LICENSE](LICENSE) file for details.

## ⚠️ Disclaimer

This tool is designed to prevent idle timeout on Oracle Cloud Free Tier instances. Use it responsibly and in accordance with Oracle's Terms of Service. The authors are not responsible for any consequences of using this tool.

## 🌟 Support

If you find this project helpful, please give it a star ⭐

## 📝 Changelog

### v8.0.0 (Latest)
- Added Oracle Linux 7/8/9 support
- Added RHEL/CentOS 7/8/9 support
- OS-agnostic package management (apt/dnf/yum)
- Automatic EPEL repository configuration for RHEL-based systems
- systemd availability check with helpful error messages
- Correct supervisor paths per OS family

### v7.0.0
- Auto-update functionality
- Version checking from GitHub

### v6.0.0
- Ultra-reliable simplified version
- Streamlined codebase

### v5.0.0
- Enhanced reliability with systemd monitoring
- Health monitoring system
- Backup and restore functionality
- Automatic log rotation
- Lock file management
- Retry logic for operations
- Process watchdog
- Event logging

### v4.0.0
- Ubuntu/Debian optimization
- Auto-dependency installation
- Fixed state file quoting issues

### v3.0.0
- Menu-driven interface
- ASCII art and modern UI
- Comprehensive logging

## 🔗 Links

- [Oracle Cloud Free Tier](https://www.oracle.com/cloud/free/)
- [stress-ng Documentation](https://github.com/ColinIanKing/stress-ng)
- [Supervisor Documentation](http://supervisord.org/)

---

**Author:** Matt Blumberg  
Made with ❤️ to keep your Oracle Cloud instances alive!