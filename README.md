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
- [Hardware Recommendations](#hardware-recommendations)
- [Automation and Scripting](#automation-and-scripting)
- [Tor Network Health](#tor-network-health)
- [Community Forums](#community-forums)
- [Recognizing Contributions](#recognizing-contributions)
- [Handling Abuse Complaints](#handling-abuse-complaints)
- [Ongoing Learning](#ongoing-learning)
- [Conclusion](#conclusion)
- [Resource Links](#resource-links)

## Introduction
The Tor network plays a crucial role in preserving privacy and freedom online. By operating a Tor relay, you support a global network designed to protect users' anonymity. This guide is intended for individuals looking to contribute to this cause by setting up and maintaining a Tor relay.

## Prerequisites
- A Linux server with a public IP address and unrestricted high-speed internet connection. Recommended bandwidth: at least 1TB per month.
- Familiarity with Linux command line and system administration.

## Types of Relays
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

## Hardware Recommendations
While the specific hardware requirements for running a Tor relay can vary based on the type of relay and the expected network traffic, here are some general guidelines:

- **CPU**: A modern multi-core processor (at least 4 cores) is recommended to handle the encryption and decryption workload.
- **RAM**: A minimum of 4GB of RAM is suggested, with 8GB or more being ideal for better performance, especially for high-bandwidth relays.
- **Disk Space**: The amount of disk space required depends on the relay type. For non-exit relays, 20-30GB should suffice. Exit relays may need 100GB or more due to the need to cache more data.
- **Network**: A stable, high-speed internet connection is crucial. Bandwidth requirements vary, but a minimum of 1TB per month is recommended. The more bandwidth you can contribute, the more valuable your relay will be to the network.

Keep in mind that these are just general recommendations. The actual requirements will depend on factors such as your specific setup, the number of users your relay serves, and the amount of traffic it handles. It's always a good idea to start with more resources than you think you'll need and monitor your relay's performance to make adjustments as necessary.

## Automation and Scripting
Automating routine tasks can significantly simplify the management of your Tor relay. Here are a few areas where automation and scripting can be beneficial:

- **Log Rotation**: Use tools like `logrotate` to automate the compression, rotation, and deletion of old log files. This helps maintain disk space and makes log analysis more manageable.

- **Bandwidth Monitoring**: Write scripts to regularly monitor your relay's bandwidth usage and alert you if it exceeds predefined thresholds. This can help you avoid exceeding your ISP's data caps or detecting unusual traffic patterns.

- **Software Updates**: Create scripts to check for and apply updates to your operating system and Tor software automatically. This ensures your relay is always running the latest security patches and features.

- **Status Monitoring**: Implement scripts to check your relay's status periodically and notify you if it becomes unreachable or experiences performance issues. This allows you to quickly address any problems that arise.

- **Backup and Synchronization**: Automate the backup of your relay's configuration files and keys to a secure, off-site location. This makes it easier to recover from hardware failures or migrate to new hardware when necessary.

When creating automation scripts, it's important to follow best practices for script development, such as:

- Use version control (e.g., Git) to track changes to your scripts over time.
- Include error handling and logging to help diagnose issues.
- Ensure your scripts are secure and don't introduce new vulnerabilities.
- Test your scripts thoroughly before deploying them in production.

There are many scripting languages and tools available for automation, such as Bash, Python, Ansible, and Puppet. Choose the tools that best fit your skills and environment, and consider sharing your scripts with the Tor community to help other relay operators.

## Tor Network Health
As a Tor relay operator, it's important to stay informed about the overall health and status of the Tor network. This allows you to respond quickly to any issues that may affect your relay or the network as a whole.

- **Network Status**: Regularly check the Tor Network Status page (https://status.torproject.org/) for any reported issues or ongoing attacks on the network.

- **Critical Vulnerabilities**: Pay close attention to announcements from the Tor Project about critical vulnerabilities in Tor software. Apply patches as soon as they become available to help maintain the security of the network.

- **Bandwidth Capacity**: Monitor the total advertised bandwidth capacity of the Tor network. If there is a significant drop, it could indicate a large number of relays going offline, which may require investigation or mitigation efforts.

- **Consensus Health**: Keep an eye on the consensus document published by the directory authorities. Ensure that your relay is properly listed and that there are no signs of network partitioning or other anomalies.

- **Community Discussions**: Follow discussions on the Tor mailing lists and forums related to network health and performance. This can help you stay informed about emerging issues and participate in efforts to address them.

If you notice any issues with your relay or the broader network, report them to the appropriate Tor Project communication channels (e.g., mailing lists, bug tracker) so that they can be investigated and addressed. By actively monitoring network health and responding to issues, you help ensure the stability and reliability of the Tor network for all users.

## Community Forums
Engaging with the Tor community is an excellent way to learn from other relay operators, share your experiences, and contribute to the ongoing development and advocacy of the Tor network. Here are some key community forums to participate in:

- **Tor Mailing Lists**: The Tor Project maintains several mailing lists for different topics and audiences. The most relevant for relay operators are:
  - tor-relays@lists.torproject.org: A list for relay operators to discuss technical issues, share best practices, and coordinate network-wide efforts.
  - tor-dev@lists.torproject.org: A list for discussing the development of Tor software and protocols, which can be useful for staying informed about upcoming changes and providing feedback.

- **Tor Forum**: The Tor Project's official forum (https://forum.torproject.net/) is a web-based platform for discussions on various Tor-related topics. The "Relay Operations" section is particularly useful for relay operators.

- **IRC Channels**: The Tor Project maintains several IRC channels on the OFTC network (irc.oftc.net). The most relevant for relay operators are:
  - #tor: A general discussion channel for Tor-related topics, where you can often find Tor developers and experienced relay operators.
  - #tor-relays: A channel specifically for relay operators to discuss technical issues and share experiences.

- **Tor StackExchange**: The Tor Project has a dedicated StackExchange site (https://tor.stackexchange.com/) for asking and answering questions related to Tor. This can be a useful resource for finding solutions to common problems and sharing your own knowledge with others.

- **Social Media**: The Tor Project has an official presence on various social media platforms, such as Twitter (@torproject) and Facebook. Following these accounts can help you stay informed about news and events related to Tor.

When participating in these community forums, remember to:

- Be respectful and constructive in your interactions with others.
- Follow the rules and guidelines of each forum.
- Protect the privacy of Tor users and other relay operators by not sharing sensitive information.
- Contribute your knowledge and experiences to help others and strengthen the Tor community.

By actively engaging with the Tor community, you can help shape the future of the Tor network and support its mission of promoting privacy and freedom online.

## Recognizing Contributions
The Tor Project recognizes the valuable contributions of relay operators through various initiatives:

- **Tor Relay Medals**: The Tor Project awards digital medals to relay operators based on their uptime and bandwidth contributions. These medals are displayed on the Tor Metrics website and serve as a way to publicly acknowledge the efforts of dedicated relay operators.

- **Tor Relay Hall of Fame**: Exceptional relay operators may be inducted into the Tor Relay Hall of Fame, which honors individuals who have made significant and sustained contributions to the Tor network over time.

- **Tor Project Membership**: Relay operators who demonstrate a long-term commitment to the Tor network and actively contribute to the Tor community may be invited to become members of the Tor Project. This allows them to participate more directly in the governance and decision-making processes of the organization.

As a relay operator, your contributions are essential to the strength and resilience of the Tor network. By running a reliable and well-maintained relay, you are helping to protect the privacy and freedom of countless users around the world.

## Handling Abuse Complaints
As an exit relay operator, you may occasionally receive abuse complaints from website administrators or other third parties who observe malicious traffic originating from your relay's IP address. It's important to handle these complaints professionally and responsibly to maintain the reputation of your relay and the Tor network as a whole.

- **Respond Promptly**: Acknowledge receipt of the complaint and inform the complainant that you will investigate the issue. Aim to provide an initial response within 24-48 hours.

- **Investigate the Complaint**: Review your relay's logs and traffic patterns to determine if there is evidence of abuse or malicious activity. If necessary, consult with other relay operators or the Tor Project for guidance.

- **Take Appropriate Action**: If you find evidence of abuse, take steps to mitigate the issue, such as temporarily blocking the offending traffic or adjusting your exit policy. If the complaint is unfounded or reflects a misunderstanding of how Tor works, politely explain the situation to the complainant.

- **Communicate with the Complainant**: Keep the complainant informed about your investigation and any actions taken. Be professional and courteous in your communications, even if the complainant is frustrated or hostile.

- **Document the Incident**: Keep detailed records of the complaint, your investigation, and any actions taken. This documentation may be useful if the issue escalates or if you need to demonstrate your responsible handling of abuse complaints.

- **Seek Legal Advice**: If you receive a complaint that appears to have legal implications, such as a subpoena or cease-and-desist order, consult with a qualified attorney before responding. The Tor Project may be able to provide guidance or referrals to legal resources.

Remember that as a Tor relay operator, you are generally not responsible for the content or activities of Tor users. Your role is to provide a secure and private communication channel, not to police the behavior of individual users. By handling abuse complaints responsibly and transparently, you can help maintain the trust and integrity of the Tor network.

## Ongoing Learning
Operating a Tor relay is an ongoing learning experience. To stay informed about new developments, best practices, and emerging threats, it's important to:

- **Follow Tor Project Updates**: Regularly check the Tor Project blog (https://blog.torproject.org/) and the Tor Project website (https://www.torproject.org/) for news, announcements, and updates related to Tor software and the Tor network.

- **Participate in Tor Events**: Attend Tor-related events, such as conferences, workshops, and meetups, to learn from experts and connect with other relay operators. Many of these events are now held online, making it easier to participate from anywhere in the world.

- **Read Tor Research**: Stay up-to-date on the latest Tor-related research by following academic publications, conference proceedings, and research blogs. The Tor Project maintains a list of recent research papers on its website (https://research.torproject.org/).

- **Explore Additional Resources**: Take advantage of the many online resources available for learning about Tor, privacy, and security. Some popular resources include:
  - The Tor Project's documentation (https://2019.www.torproject.org/docs/documentation.html.en)
  - The Electronic Frontier Foundation's Surveillance Self-Defense guide (https://ssd.eff.org/)
  - The Privacy Enhancing Technologies Symposium (PETS) (https://petsymposium.org/)

- **Engage with the Tor Community**: Participate actively in Tor community forums, mailing lists, and chat channels. Share your experiences, ask questions, and learn from the knowledge and insights of other relay operators and Tor developers.

By continuously learning and staying informed, you can help ensure that your Tor relay remains secure, efficient, and effective in supporting the Tor network's mission of promoting privacy and freedom online.

## Conclusion
Running a Tor relay is a powerful way to contribute to the fight for online privacy and freedom. By following the steps and best practices outlined in this guide, you can set up and maintain a secure, reliable, and effective Tor relay that helps protect the anonymity and privacy of users around the world.

Remember that operating a Tor relay is an ongoing commitment that requires regular maintenance, monitoring, and engagement with the Tor community. By staying informed, vigilant, and proactive, you can help ensure the long-term health and resilience of the Tor network.

Thank you for your interest in supporting the Tor network and promoting online privacy and freedom. Together, we can build a stronger, more secure, and more private internet for all.

## Resource Links
- [Tor Project Official Website](https://www.torproject.org/): Visit the official Tor Project website for comprehensive resources, documentation, and the latest news. Navigate to the "Download" section to find the most up-to-date installation packages and instructions.
- [Tor Relay Configuration](https://community.torproject.org/relay/): For detailed setup and configuration instructions for your Tor relay, refer to the "Relay Configuration" or "Setup Guide" sections on the Tor Project's official website. These resources provide step-by-step guides for different operating systems and setups.
- [Tor Metrics](https://metrics.torproject.org/): To monitor the health and performance of the Tor network as well as your own relay, the Tor Metrics website offers tools and data visualizations. It's an essential resource for understanding network dynamics and the impact of your relay.
