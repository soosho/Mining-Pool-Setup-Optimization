# Miningcore Mining Pool Restart Guide

This guide provides instructions for restarting your Miningcore mining pool server after a system reboot or shutdown.

## Server Restart Procedure

### 1. Start Cryptocurrency Daemons

First, you must initialize the cryptocurrency daemons:

```bash
# Start the Maza daemon
mazad

# Start the eMark daemon
emarkd
```

> **Important**: Allow the daemons to fully synchronize before proceeding to the next step.

### 2. Launch Miningcore Using Screen

Using `screen` ensures your mining pool continues running even if your SSH session disconnects:

```bash
# Create a new screen session named "Miningcore"
screen -S Miningcore

# Navigate to the Miningcore build directory
cd core/build

# Launch Miningcore with the configuration file
./Miningcore -c uu.json
```

### 3. Managing Your Screen Session

- **Detach from screen session**: Press `Ctrl + A + D`
- **Reattach to screen session**: Run `screen -r Miningcore`
- **Reattach if only one screen exists**: Simply run `screen -r`

## Configuration

The mining pool configuration file is located at:

```
/root/core/build/uu.json
```

This JSON file controls all aspects of your mining pool including:
- Supported coins
- Port configurations
- Payout settings
- Pool fees
- Difficulty settings

## Additional Information

- Once Miningcore is running, miners can immediately connect to your pool
- No additional services need to be started manually
- Always start cryptocurrency daemons before launching Miningcore
- The configuration file can be modified to adjust pool settings as needed

## Troubleshooting

If you experience issues after restart:
1. Verify both cryptocurrency daemons are running and synchronized
2. Check the Miningcore logs for any error messages
3. Ensure your configuration file is valid JSON with no syntax errors

---

*Last updated: 2025-06-12*
