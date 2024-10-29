
## INSTALL MYSQL 8 COMMUNITY EDITION (CentOS/RHEL)

### INSTALLATION STEPS

**STEP 1. DOWNLOAD MYSQL 8 REPOSITORY PACKAGE**
```sh
wget https://repo.mysql.com/mysql80-community-release-el7-3.noarch.rpm
```

**STEP 2. INSTALL MYSQL REPO LOCALLY**

Installing the MySQL repository locally configures YUM to recognize the MySQL software repository, which provides access to the latest MySQL versions and updates. This repository ensures:
- **Automatic Access to Updates**: You’ll receive MySQL updates directly through YUM, making it easy to keep MySQL secure and up-to-date.
- **Simplified Dependency Management**: All necessary dependencies for MySQL are available through this repository, simplifying installation.

Run the command below to set up the repository:

```sh
sudo yum localinstall mysql80-community-release-el7-3.noarch.rpm
```

**STEP 3. IMPORT PUBLIC KEY FOR MYSQL 8**
```sh
sudo rpm --import https://repo.mysql.com/RPM-GPG-KEY-mysql-2022
```

**STEP 4. INSTALL MYSQL SERVER**
```sh
sudo yum install mysql-community-server
```

**STEP 5. ENABLE MYSQL SERVICE TO AUTO-START ON REBOOT**
```sh
sudo systemctl enable mysqld.service
```

**STEP 6. START MYSQL SERVICE**
```sh
sudo systemctl start mysqld.service
```

**STEP 7. CHECK STATUS OF MYSQL SERVICE**
```sh
sudo systemctl status mysqld
```

### VERIFICATION

To ensure MySQL is properly installed and running, you can run the following commands:

1. **Check if MySQL is running**: 
   ```sh
   pidof mysqld
   ```

2. **Verify MySQL is listening on the default port 3306**:
   - If you don't have `netstat` installed, first run:
     ```sh
     sudo yum install net-tools
     ```
   - Then check for MySQL on port 3306:
     ```sh
     netstat -ntlp | grep 3306
     ```

3. **List open files by the MySQL user**:
   ```sh
   sudo lsof -u mysql
   ```

### OPTIONAL: ALLOW MYSQL THROUGH FIREWALL
If your firewall blocks MySQL connections, you may need to allow MySQL through the firewall:

```sh
sudo firewall-cmd --add-service=mysql --permanent
sudo firewall-cmd --reload
```
