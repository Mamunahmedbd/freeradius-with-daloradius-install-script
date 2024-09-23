**daloRADIUS** is an advanced RADIUS web management application for managing hotspots and general-purpose ISP deployments. It features user management, graphical reporting, accounting, a billing engine, and integrates with [OpenStreetMap](https://www.openstreetmap.org/copyright) for geolocation. The system is based on [FreeRADIUS](https://freeradius.org/) with which it shares access to the backend database.

**daloRADIUS** is written using the [PHP programming language](https://www.php.net/) and uses a [database abstraction layer](https://en.wikipedia.org/wiki/Database_abstraction_layer) (DAL) for database access. Although DAL allows the use of different [database management systems](https://en.wikipedia.org/wiki/Database#Database_management_system) (DBMSs) (e.g., MariaDB, MySQL, PostgreSQL, SQLite, MsSQL, etc.), **it is important to note that daloRADIUS has been fully tested only on the [MariaDB](https://mariadb.org/) DBMS**. Therefore, **the use of other DBMSs is not recommended**.

## Installation
### quick installation
To quickly install a basic standalone AAA infrastructure - based on daloRADIUS - on a [Debian](https://www.debian.org/download) environment, run the following command in a `root` terminal:
```bash
wget -qO - https://raw.githubusercontent.com/mamunahmedbd/freeradius-with-daloradius-install-script/main/install.sh | bash
```
At the end of this procedure, **the installation script will generate random credentials to be used for the operator's first login**.

### NAS Management

- **List NAS**: View a list of all Network Access Servers (NAS) registered in the system.
- **Create New NAS**: Add new NAS devices to manage network access.
- **Edit NAS**: Modify NAS details and settings.
- **Delete NAS**: Remove NAS devices from the system.

### Groups Management

- **List, Create New, Edit and Delete User-Groups Mapping**: Manage user-group mapping in the radius database.
- **List, Create New, Edit and Delete Group-Reply and Group-Check Settings**: Configure group-wide attributes in the radius database.

## Accounting

### Users Accounting By

- **Username**: View accounting information for specific users by their username.
- **IP Address**: Monitor accounting details based on the user's IP address.
- **NAS IP Address**: Track accounting data based on the NAS IP address.
- **Date (From/To)**: Get accounting records within a specified date range.
- **Display of All Accounting Records**: Access a comprehensive view of all accounting records in the radius database.
- **Display of Active Accounting Records**: Monitor active accounting sessions using Max-All-Session attribute or Expiration attribute.
- **Custom Accounting Query**: Perform custom accounting queries to extract specific data.

### HotSpots Accounting

- **Comparison of Accounting for different HotSpots**: Compare accounting data for different hotspots, providing information on hotspot's unique users, total hits, average time, and total time.

### GIS - Geographical Information System

daloRADIUS comes with integrated support for GIS provided by Leaflet and CARTO basemap, enabling the visual location of deployed HotSpots across a map. It allows you to see their status and monitor them visually.

- **View Map**: Monitor deployed HotSpots using the GIS map.
- **Edit Map**: Add or delete HotSpots directly on the map, without navigating to the HotSpots Management page.

## Reporting

### Basic Reporting

- **Online Users**: View online users currently connected to the system from all NAS devices at a current point in time.
- **Last Connection Attempts**: View last connection attempts and their status - whether they were rejected or successful.
- **Search Users**: Search for Users - similar to the functionality in User Management page.
- **Top Users**: View a report of the Top Users based on their Bandwidth consumption or Time usage.

### Logs Reporting

- **daloRADIUS Log**: Keep track of all actions performed within the daloRADIUS interface, such as page visits, form actions (e.g., deleting users, creating new hotspots), and queries submission for user accounting.
- **RADIUS Server Log**: Monitor the FreeRADIUS server logfile.
- **System Log**: Monitor the system log, which can include syslog or messages, depending on the configuration.
- **Boot Log**: Monitor the boot/kernel log (dmesg).

### Status Reporting

- **Server Status**: Provides detailed information on the server where daloRADIUS is deployed, including CPU utilization, uptime, memory, disk information, and more.
- **RADIUS Status**: Provides information on whether the FreeRADIUS server is running, along with the database server (e.g., MySQL, PostgreSQL, or others).

## Billing

- **POS (Point of Sales)**
- **Plans**
- **Rates**
- **PayPal Transactions**
- **Billing History**
- **Invoices**
- **Payments**

## Graphs

### Users Graphs

Provides visual graphs and statistical listing per user connection's attributes, including:

- **Logins/Hits**
- **Download**
- **Upload**

### Server-Wide Graphs

Provides visual graphs and statistical listing for the entire server, showing all-time information on:

- **Logins/Hits**
- **Traffic Comparison**

## Configuration

### Global Configuration

- **Database Settings**: Configure database connection information (storage: MySQL, PostgreSQL, and others), credentials (username and password), radius database table names (radcheck, radacct, etc.), and database password encryption type (none, md5, sha1).
- **Language Settings**: daloRADIUS is multi-lingual and currently supports English and Russian language packs.
- **Logging Settings and Debugging**: Enable logging of different actions, queries, and page visits. Also supports debugging of SQL queries executed.
- **Interface Settings**: Support for displaying password text in either clear-text or as asterisks to hide it. Table listing spanning across multiple pages is configurable on the number of rows per page and addition of number links for quick-access to different pages.

### Maintenance

- **Test User Connectivity**: Provides the ability to check if a user's credentials (username and password) are valid by executing a radius query to a radius server (configurable for radius port, shared secret, etc.).
- **Disconnect User**: Supply a username and send a PoD (Packet of Disconnect) or CoA (Change of Authority) packet to the NAS to disconnect the user.

### Operators

daloRADIUS supports Operators for complete management of the entire platform. Different Operators can be added with their contact information and ACLs settings to grant or revoke them permissions to access different pages.

- **List Operators**
- **Create New Operator**
- **Edit Operator**
- **Delete Operator**
