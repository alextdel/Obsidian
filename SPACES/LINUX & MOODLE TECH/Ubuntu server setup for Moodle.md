**up::** [[Linux & Moodle MOC]]
**index::** [[+Index for Personal]]

**tags::** #Linux #Moodle #AWS #setup_notes  
# Ubuntu server setup for Moodle

**Created:**  19 February 2024 at  11:15 hours.
___
For setup and securing Moodle servers on AWS Ubuntu:
- See below for [[Ubuntu server setup for Moodle]]
- Click here for [[Security and performance for Moodle on AWS Ubuntu]]
---
## Setting Up a Production Moodle Server on Ubuntu with Git Versioning

This guide outlines the steps to create a Moodle server on a clean Ubuntu installation using Git for version control, including configuration for PHP, webserver, security, and firewall. Remember, this is a general guide, and adjustments may be needed based on your specific requirements and server setup.

**Preparation:**

1. **Choose an Ubuntu Version:** Select a Long Term Support (LTS) version for stability and security updates.
2. **Configure your AWS Lightsail Instance:** Allocate appropriate resources based on your expected Moodle usage.
3. **SSH Certificate Installation:** If you're using SSH for remote access, install the SSH certificate on your local machine and configure it to connect to the server. This step ensures secure communication during the setup process.
4. **Connect to your Server:** Use SSH to connect to your server remotely.

**Server Setup:**

1. **Update and Upgrade:** Run `sudo apt update && sudo apt upgrade` to update the system.
2. **Install Essential Packages:** Run `sudo apt install git git-core git-doc curl htop` for version control and system monitoring.
3. **Install LAMP Stack:**
    - Webserver: Choose Apache (`sudo apt install apache2`) or Nginx (`sudo apt install nginx`).
    - PHP: Install PHP 7.4 or later (`sudo apt install php7.4 libapache2-mod-php7.4`) and required extensions (`sudo apt install php7.4-curl php7.4-xmlrpc php7.4-gd php7.4-intl php7.4-mysql`).
    - MySQL: Install MySQL server (`sudo apt install mysql-server`) and client (`sudo apt install mysql-client`).
4. **AppArmor Configuration:** Ubuntu Server uses AppArmor for mandatory access control. Familiarise yourself with AppArmor profiles and consider configuring them for enhanced security.

**Moodle Installation:**

1. **Create Document Root:** Choose a directory for Moodle files (e.g., `/var/www/html`) and grant web server ownership (`sudo chown -R www-data:www-data /var/www/html`).
2. **Clone Moodle Repository:** Navigate to the document root and clone the Moodle Git repository using `sudo git clone git://git.moodle.org/moodle.git`.
3. **Create Data Directory:** Choose a directory for Moodle data (e.g., `/var/moodledata`) and set appropriate permissions (`sudo mkdir /var/moodledata && sudo chown -R www-data:www-data /var/moodledata`).
4. **Set Permissions:** Ensure web server ownership of Moodle files and data directory (`sudo chown -R www-data:www-data /var/www/html /var/moodledata`).

**Database Setup:**

1. **Secure MySQL:** Run `sudo mysql_secure_installation` to set a strong root password and configure security options.
2. **Create Database:** Create a database and user for Moodle using `mysql` command-line tool or a graphical interface like phpMyAdmin. Remember the credentials.

**Moodle Web Configuration:**

1. **Apache:** Edit the Apache configuration file `/etc/apache2/sites-available/000-default.conf` to point the DocumentRoot to your chosen Moodle directory.
2. **Nginx:** Create a virtual host configuration file in `/etc/nginx/sites-available` directing requests to the Moodle directory. Enable the configuration.
3. **Restart Webserver:** Restart Apache (`sudo systemctl restart apache2`) or Nginx (`sudo systemctl restart nginx`).

**Moodle Installation Process:**

1. **Web Browser Access:** Access your server's IP address or domain name in a web browser.
2. **Follow Installation Wisard:** Enter the database credentials and other configuration details as prompted.
3. **Complete Installation:** Finish the installation process and access your Moodle site.

**Security and Firewall:**

1. **Moodle Configuration:** Within Moodle admin, review and adjust security settings under "Site administration > Server."
2. **Web Server Hardening:** Follow best practices for securing your chosen web server (Apache or Nginx).
3. **AppArmor:** Consider configuring AppArmor profiles to enhance security.
4. **UFW Firewall:** Use the UFW firewall (`sudo ufw enable`) to restrict access to necessary ports (e.g., HTTP, SSH) and block unnecessary ones.
5. **Regular Updates:** Keep your OS, PHP, Moodle, and MySQL updated with the latest security patches.

**Git Versioning:**

1. **Git Workflow:** Use Git commands to manage Moodle code versions, committing changes and pulling updates from the repository.
2. **Backup:** Regularly back up your Moodle data and codebase for disaster recovery.

**Additional Considerations:**

* **Performance Optimisation:** If needed, explore caching mechanisms and server optimisation techniques for better performance.
* **Load Balancing:** For high traffic scenarios, consider load balancing solutions to distribute requests across multiple instances.
* **Monitoring:** Implement monitoring tools to track server health, performance, and security events.

**Installing an SSL Certificate:**

1. **Choose a Certificate:** You can obtain a free certificate from Let's Encrypt or purchase one from a trusted Certificate Authority (CA). For production environments, consider paid options with stronger security and support.
2. **Certificate Installation:** The process varies depending on your chosen certificate provider and web server. Many vendors offer automated tools or instructions for specific web server configurations. Here are some resources:
    - **Let's Encrypt:** [https://letsencrypt.org/getting-started/](https://letsencrypt.org/getting-started/)
    - **Apache with Certbot:** [https://certbot.eff.org/instructions](https://certbot.eff.org/instructions)
    - **Nginx with Certbot:** [https://certbot.eff.org/instructions?ws=nginx&os=pip](https://certbot.eff.org/instructions?ws=nginx&os=pip)
3. **Web Server Configuration:** Modify your web server configuration files (e.g., Apache `.conf` or Nginx `.conf`) to enable HTTPS and point to your installed certificate files.
4. **Restart Webserver:** Restart your web server to apply the changes.

**Additional Considerations:**

* **Redirect HTTP to HTTPS:** Ensure all HTTP traffic is redirected to HTTPS to avoid mixed content warnings and improve security.
* **Test Your SSL Configuration:** Use online tools like SSL Labs ([https://www.ssllabs.com/ssltest/](https://www.ssllabs.com/ssltest/)) to check your certificate installation and configuration.
```

This revision includes the placement of SSH certificate installation earlier in the process, as well as the mention of AppArmor configuration in the server setup section.


**See also::** 

### Links to this note:
```query
"[[Ubuntu server setup for Moodle]]"
```

