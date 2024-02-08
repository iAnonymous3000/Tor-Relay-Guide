# Tor Relay: Complete Setup and Administration Guide

## Table of Contents
- [Introduction](#introduction)
- [Prerequisites](#prerequisites)
- [Types of Relays](#types-of-relays)
- [Step 1 – Install Tor](#step-1--install-tor)
- [Step 2 – Configure Tor Settings](#step-2--configure-tor-settings)
- [Step 3 – Start Your Relay](#step-3--start-your-relay)
- [Step 4 – Monitoring and Management](#step-4--monitoring-and-management)
- [Security Practices](#security-practices)
- [Exit Relay Considerations](#exit-relay-considerations)
- [Advanced Configuration Examples](#advanced-configuration-examples)
- [Backup and Recovery](#backup-and-recovery)
- [Engagement with the Tor Network](#engagement-with-the-tor-network)
- [Accessibility and Internationalization](#accessibility-and-internationalization)
- [Feedback Mechanism](#feedback-mechanism)
- [Legal and Ethical Considerations](#legal-and-ethical-considerations)
- [Success Stories](#success-stories)
- [Version Control](#version-control)
- [Conclusion](#conclusion)
- [Resource Links](#resource-links)

## Introduction
The Tor network plays a crucial role in preserving privacy and freedom online. By operating a Tor relay, you support a global network designed to protect users' anonymity. This guide is intended for individuals looking to contribute to this cause by setting up and maintaining a Tor relay.

## Prerequisites
- A Linux server with a public IP address and unrestricted high-speed internet connection. Recommended bandwidth: at least 1TB per month.
- Familiarity with Linux command line and system administration.

## **Types of Relays**
- **Bridges, Guards, Middle Relays, and Exits**: Understand the role and requirements of different relay types within the Tor network to decide which one you can and should run.

## Step 1 – Install Tor
**Before installation, ensure your system is up to date:**
- For Debian/Ubuntu systems: 
  ```
  sudo apt update && sudo apt upgrade
  ```
- For RHEL/CentOS systems:
  ```
  sudo yum update
  ```

**It's crucial to install Tor using the Tor Project's official repository to ensure you're using the most up-to-date and secure version:**
1. **For Debian/Ubuntu:**
   - First, add the Tor Project's official repository:
     ```
     sudo apt install apt-transport-https gnupg2
     echo "deb https://deb.torproject.org/torproject.org $(lsb_release -sc) main" | sudo tee /etc/apt/sources.list.d/tor.list
     ```
   - Then, add the Tor Project's signing key:
     ```
     curl https://deb.torproject.org/torproject.org/apt-signing-key.asc | gpg --dearmor | sudo tee /usr/share/keyrings/tor-archive-keyring.gpg >/dev/null
     ```
   - Finally, update your package list and install Tor:
     ```
     sudo apt update && sudo apt install tor
     ```

2. **For RHEL/CentOS:**
   - The Tor Project does not directly provide a repository for RHEL/CentOS. However, you can enable the EPEL repository to install Tor, but this might not always give you the latest version. For the most up-to-date instructions on adding a repository for Tor on these systems, please refer to the [Tor Project official documentation](https://support.torproject.org/rpm/).

## Step 2 – Configure Tor Settings
Configure your relay in `/etc/tor/torrc`. Essential settings:
- `ORPort 443`
- `Nickname MyRelay`
- `ContactInfo myemail@example.com`

## Step 3 – Start Your Relay
Enable and start Tor with `systemctl` to ensure it runs on boot.

## Step 4 – Monitoring and Management
- Once your relay is configured and connected to the Tor network, it will automatically be recognized and listed in the Tor Metrics (formerly known as Tor Atlas) within a few hours to a day. **No manual registration is required.**
- Use tools like `vnstat`, `munin`, and `nyx` for real-time performance monitoring.

## Security Practices

Ensuring the security of your Tor relay is paramount for the integrity of the Tor network and your own operational safety. Here are comprehensive practices to enhance your Tor relay's security:

### System and Software Updates
- **Keep Updated**: Regularly update your operating system and Tor software to the latest versions to patch security vulnerabilities.

### Firewall Configuration
- **Access Control**: Utilize a firewall to limit access only to necessary ports for your Tor relay and any other services you run. This minimizes the attack surface for potential intruders.

### Fail2ban for Intrusion Prevention
- Implement `fail2ban` to protect against brute-force attacks by monitoring log files for repeated failed login attempts and banning the offending IP addresses.

### Enhance SSH Security
- **Key-Based Authentication**: Disable password authentication for SSH and use SSH keys instead. This significantly reduces the risk of unauthorized access.
- **Change Default SSH Port**: Altering the default SSH port (22) to a non-standard port can decrease exposure to automated attacks.
- **SSH Access Control**: If feasible, implement IP whitelisting for SSH connections to further enhance security.

### Security Extensions and Modules
- Employ security modules like SELinux or AppArmor to enforce access controls and limit potential damage from vulnerabilities.

### Time Synchronization
- **Accurate Timekeeping**: Use Network Time Protocol (NTP) to ensure your relay's clock is synchronized, which is critical for Tor operations.

### Diverse Operating System Selection
- **Contribute to Network Diversity**: Opting for underrepresented operating systems in the Tor network, such as BSD variants, can enhance overall security through diversity.

### Monitoring and Logging
- **Regular Checks**: Monitor system and Tor logs for unusual activities that might indicate security issues. Automated tools like `logwatch` can assist by providing summarized daily reports.

### Secure Configuration of Relay
- **Exit Policies**: For exit relays, configure minimal exit policies to reduce legal risks and abuse complaints, allowing only necessary ports.
- **Relay Contact Information**: Include accurate contact information in your relay configuration to facilitate communication for security or operational issues.

### Engage with Security Communities
- **Stay Informed**: Follow security forums, blogs, and mailing lists related to Tor and cybersecurity to stay updated on new threats and best practices.

### Legal Preparedness
- **Abuse Response Templates**: Prepare template responses for common abuse complaints. The Tor Project provides resources for handling such communications effectively.

Adhering to these security practices will not only help in maintaining the security and reliability of your Tor relay but also contribute to the robustness of the entire Tor network. Security is an ongoing commitment, necessitating regular updates, vigilance, and adaptation to emerging threats and evolving best practices.

## Exit Relay Considerations
Consult with local digital rights organizations or the Tor legal team for advice on running an exit relay in your jurisdiction.

## Advanced Configuration Examples
Includes settings for `MyFamily` and `ReduceExitPolicy`.

## Backup and Recovery
- Emphasize the importance of regular backups for critical configuration and key files, along with recovery strategies.

## Engagement with the Tor Network
- Encourage active participation in the Tor community through mailing lists, IRC, and forums for support and sharing experiences.

## Accessibility and Internationalization
Call for contributions to make the Tor network more accessible and diverse, including translation efforts.

## Feedback Mechanism
Engage with the community through GitHub for feedback, issues, and contributions. Be prepared to manage community engagement actively.

## Legal and Ethical Considerations
Stay informed about your local laws regarding Tor relay operation. Engage with local digital rights organizations for support and advice.

## Success Stories

The Tor network has been instrumental in facilitating secure, private, and unrestricted access to the internet for users worldwide. From circumventing censorship to protecting personal privacy, the stories of those who rely on Tor are as varied as they are inspiring. Here, we share a collection of success stories that showcase the profound impact of Tor across different contexts and communities.

### Breaking Through Censorship
In regions where access to information is restricted, Tor serves as a vital lifeline. Users from countries with stringent internet controls report successfully using Tor to bypass government filters, accessing everything from social media to independent news sites. This not only enables them to stay informed but also to share their own stories with the world.

### Safeguarding Journalistic Integrity
For journalists working under the threat of surveillance and repression, Tor is an essential tool for secure communication. It allows them to connect with sources confidentially and report on sensitive issues without compromising their safety or the safety of their informants. Through Tor, stories that would otherwise be silenced reach the global stage.

### Empowering Activists
Activists leveraging Tor to coordinate efforts and disseminate information illustrate the network's role in social and political movements. In environments where surveillance is used to stifle dissent, Tor provides a shield, enabling activists to organize and advocate for change without fear of reprisal.

### Protecting Individual Privacy
Ordinary internet users turn to Tor for a myriad of personal privacy concerns. From evading tracking by advertisers to safeguarding personal communications, Tor offers individuals control over their digital footprint. This privacy empowers users to explore, communicate, and transact on their terms.

### Assisting At-Risk Individuals
Tor has been a critical resource for individuals in dangerous or abusive situations seeking help and information without leaving a trace. Whether escaping domestic violence, avoiding stalkers, or securing sensitive medical information, Tor provides a safe avenue for at-risk users to find support and resources anonymously.

These narratives underscore the significance of the Tor network in promoting internet freedom, privacy, and security. They reflect the collective experience of a community that values and depends on Tor for a multitude of reasons, each story reinforcing the importance of maintaining and strengthening this vital resource.

The Tor Project is dedicated to fostering a safe, accessible, and open internet for all. We invite you to join us by sharing your story, contributing to the network, or supporting our mission in any way you can. Together, we can continue to make a difference in the lives of millions around the globe.

## Version Control
Please check the [Tor Project official website](https://www.torproject.org/) for any significant updates or changes in newer versions.

## Conclusion
Running a Tor relay is a powerful contribution to a more private and free internet. This guide aims to equip you with the necessary knowledge and tools to make your relay operation successful and impactful.

## Resource Links
- [Tor Project Official Website](https://www.torproject.org/): Visit the official Tor Project website for comprehensive resources, documentation, and the latest news. Navigate to the "Download" section to find the most up-to-date installation packages and instructions.
- [Tor Relay Configuration](https://community.torproject.org/relay/): For detailed setup and configuration instructions for your Tor relay, refer to the "Relay Configuration" or "Setup Guide" sections on the Tor Project's official website. These resources provide step-by-step guides for different operating systems and setups.
- [Tor Metrics](https://metrics.torproject.org/): To monitor the health and performance of the Tor network as well as your own relay, the Tor Metrics website offers tools and data visualizations. It's an essential resource for understanding network dynamics and the impact of your relay.
