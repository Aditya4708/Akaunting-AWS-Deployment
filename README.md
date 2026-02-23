# Akaunting-AWS-Deployment

# AWS EC2 & RDS Deployment: Akaunting Application (Assignment 1)

## Project Overview
This repository contains the configuration and connection details for deploying the Akaunting web application on an AWS EC2 instance, connected to a highly available Amazon RDS (MySQL) backend.

## EC2 / App URL
* **Live Application URL:** http://54.91.194.159

## Database Deployment Steps (Amazon RDS)
1. Navigated to the AWS RDS Console and created a new MySQL database.
2. Selected the "Free Tier" template and configured the master username (`admin`) and a secure password.
3. Set the DB instance class to `db.t3.micro` and allocated 20 GB of storage.
4. Ensured "Public Access" was set to **No**.
5. Created a new VPC Security Group dedicated to the RDS instance.

## Application Connection Steps
1. SSH into the EC2 instance hosting the Akaunting application.
2. During the Akaunting web installation (or via the `.env` file in `/var/www/akaunting`), input the following Database credentials:
   * **Database Type:** MySQL
   * **Hostname:** akaunting-db.ckr0iqasyh35.us-east-1.rds.amazonaws.com
   * **Database Port:** 3306
   * **Database Name:** akaunting
   * **Username:** admin
   * **Password:** [Master Password]
3. Completed the installation, allowing the application to build the necessary 46 tables in the RDS instance.
