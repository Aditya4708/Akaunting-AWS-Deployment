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
   * **Password:** Adityanambiar47
3. Completed the installation, allowing the application to build the necessary 46 tables in the RDS instance.

## Assignment 2: DynamoDB (NoSQL) Integration

### Database Deployment & Schema
* **Database Engine:** Amazon DynamoDB
* **Table Name:** `Lab5AkauntingLog`
* **Partition Key:** `LogID` (Type: String)
* **Schema Design:** As a NoSQL database, the table is schema-less beyond the Partition Key. It is designed to store application logs and audit records utilizing nested data structures.

### Security Configuration (Zero-Trust)
* **Authentication Method:** AWS IAM Role
* **Implementation:** Access to DynamoDB is granted exclusively via an IAM Role (`AmazonDynamoDBFullAccess`) attached directly to the EC2 instance. No API keys or long-term AWS credentials are hardcoded into the application or server, adhering to AWS security best practices.

### 5 Mandatory Datatypes Proof (Sample JSON)
The database utilizes the following 5 attribute types: String (S), Number (N), Boolean (BOOL), List (L), and Map (M).

```json
{
    "LogID": {"S": "A001"},
    "EventCode": {"N": "200"},
    "IsActive": {"BOOL": true},
    "Permissions": {"L": [{"S": "Admin"}, {"S": "Write"}]},
    "Audit": {"M": {
        "Student": {"S": "Aditya"}, 
        "Status": {"S": "Active"}
    }}
}
