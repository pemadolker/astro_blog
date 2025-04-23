---
title: MSSQL
publishDate: "2025-04-16T13:20:00Z"
updateDate: "2025-04-17T14:32:00Z"
---

---
title: "Footprinting - MSSQL"
publishedAt: 2025-04-20
summary: ""
tags: "Footprinting"
---

# Notes on MSSQL (Microsoft SQL Server)

## Overview of MSSQL

- **Definition**: Microsoft SQL (MSSQL) is a SQL-based relational database management system developed by Microsoft. It is primarily designed for Windows operating systems but has versions for Linux and macOS.
- **Popularity**: MSSQL is favored by database administrators and developers, especially for applications built on the .NET framework due to its strong integration.

## MSSQL Clients

- **SQL Server Management Studio (SSMS)**: 
  - A feature included with the MSSQL installation package, used for database management and configuration.
  - Can be installed on any system, not just the server hosting the database.

- **Other Clients**:
  - `mssql-cli`
  - SQL Server PowerShell
  - HeidiSQL
  - SQLPro
  - Impacket's `mssqlclient.py`: Useful for penetration testing.

## MSSQL Databases

- **Default System Databases**:
  - **master**: Tracks all system information for an SQL server instance.
  - **model**: Template database for new databases.
  - **msdb**: Used by SQL Server Agent for scheduling jobs and alerts.
  - **tempdb**: Stores temporary objects.
  - **resource**: Read-only database containing system objects.

## Default Configuration

- **Service Account**: MSSQL typically runs as `NT SERVICE\MSSQLSERVER`.
- **Authentication**: By default, Windows Authentication is used, and encryption is not enforced.

## Dangerous Settings

- **Common Misconfigurations**:
  - MSSQL clients not using encryption for connections.
  - Use of self-signed certificates, which can be spoofed.
  - Weak or default credentials for the `sa` account.

## Footprinting the Service

- **Port Scanning**: MSSQL usually listens on TCP port 1433. Use Nmap to gather information about the MSSQL service.
  ```bash
  sudo nmap --script ms-sql-info,ms-sql-empty-password,ms-sql-xp-cmdshell -p 1433 10.129.201.248


## Conclusion
MSSQL is a powerful relational database management system that requires careful configuration and management to ensure security. Understanding its architecture, potential vulnerabilities, and best practices for securing MSSQL is essential for database administrators and security professionals. Setting up a local MSSQL instance for experimentation can provide valuable insights into its functionality and configuration options.