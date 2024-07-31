# Basic Firewall Setup on Linux

This project demonstrates how to set up a basic firewall on a Kali Linux virtual machine using UFW (Uncomplicated Firewall).

## Steps

1. **Install UFW**:

   ```bash
   sudo apt update
   sudo apt install ufw
   ```

2. **Enable UFW**:

   ```bash
   sudo ufw enable
   ```

3. **Configure Major Firewall Rules**:

   - **Allow SSH**:

     ```bash
     sudo ufw allow ssh
     ```

   - **Allow HTTP**:

     ```bash
     sudo ufw allow 80/tcp
     ```

   - **Allow HTTPS**:

     ```bash
     sudo ufw allow 443/tcp
     ```

   - **Block FTP**:

     ```bash
     sudo ufw deny 21
     ```

   - **Allow MySQL**:

     ```bash
     sudo ufw allow 3306/tcp
     ```

   - **Allow Specific IP**:

     ```bash
     sudo ufw allow from 192.168.1.10
     ```

   - **Deny Specific IP**:

     ```bash
     sudo ufw deny from 203.0.113.5
     ```

   - **Allow Specific Subnet**:

     ```bash
     sudo ufw allow from 192.168.1.0/24
     ```

   - **Deny Specific Subnet**:

     ```bash
     sudo ufw deny from 203.0.113.0/24
     ```

   - **Allow Port Range**:

     ```bash
     sudo ufw allow 1000:2000/tcp
     ```

   - **Deny Port Range**:

     ```bash
     sudo ufw deny 6000:7000/tcp
     ```

   - **Allow Outbound Traffic**:

     ```bash
     sudo ufw default allow outgoing
     ```

   - **Deny Outbound Traffic**:

     ```bash
     sudo ufw default deny outgoing
     ```

   - **Allow Established Connections**:
     ```bash
     sudo ufw allow in on eth0 to any port 1024:65535 proto tcp
     sudo ufw allow in on eth0 to any port 1024:65535 proto udp
     ```

4. **Check UFW Status**:
   ```bash
   sudo ufw status verbose
   ```

## Notes

- Ensure you replace the IP addresses and port numbers with those relevant to your network environment.
- Use `sudo ufw status` to view the current firewall rules in a summary format.
- Review and adjust the rules according to your security requirements.

## Troubleshooting

- **Firewall Rules Not Applying**:

  - Verify the UFW service is running: `sudo systemctl status ufw`
  - Check for syntax errors in the commands.

- **Network Connectivity Issues**:
  - Ensure that necessary ports for critical services are allowed.
  - Use tools like `nmap` to verify open ports and services.

## References

- [UFW Documentation](https://help.ubuntu.com/community/UFW)
- [Kali Linux Official Documentation](https://www.kali.org/docs/)
