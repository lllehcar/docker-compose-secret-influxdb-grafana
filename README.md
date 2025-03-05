<img width="280" alt="Screenshot 2025-03-05 at 11 39 28 PM" src="https://github.com/user-attachments/assets/0bbbe423-fe4f-455f-8a6b-95859042e847" />
<img width="280" alt="Screenshot 2025-03-05 at 11 39 52 PM" src="https://github.com/user-attachments/assets/fdd37bc0-02b9-4f99-873d-934b74c922cf" />
<img width="230" alt="Screenshot 2025-03-05 at 11 40 10 PM" src="https://github.com/user-attachments/assets/b768e0d0-cce1-48b9-9ca0-c45a6b61d81f" />
<img width="120" alt="Screenshot 2025-03-05 at 11 40 25 PM" src="https://github.com/user-attachments/assets/a157c8f2-8b28-4828-acde-02276a25bb65" />

# InfluxDB and Grafana Deployment using Docker Compose & Docker Secret

This project provides a simple setup for deploying **InfluxDB 2.x** and **Grafana** using **Docker Compose**. It uses Docker **secrets** to securely handle sensitive information like the InfluxDB admin username, password, and token.

## Prerequisites

Before deploying this project, ensure that you have the following installed:

- [Docker](https://docs.docker.com/get-docker/)
- [Docker Compose](https://docs.docker.com/compose/install/)

Additionally, you will need to create a GitHub repository to store your secret credentials (i.e., **InfluxDB2 admin username, password, and token**).

## Folder Structure

influxDB_grafana/ <br/>
    ├── compose.yaml # Docker Compose file <br/>
    ├── influxdb2-admin-username.txt # File containing InfluxDB username <br/>
    ├── influxdb2-admin-password.txt # File containing InfluxDB password <br/>
    ├── influxdb2-admin-token.txt # File containing InfluxDB token<br/>


## Setup and Deployment

### 1. Clone the Repository

Clone this repository to your local machine:

```bash
git clone https://github.com/lllehcar/docker-compose-secret-influxdb-grafana.git
cd docker-compose-secret-influxdb-grafana/influxDB_grafana
```


### 2. Configure the Secrets
Before deploying, ensure you have the following secret files in your influxDB_grafana folder: <br/>

`influxdb2-admin-username.txt`: InfluxDB admin username. <br/>
`influxdb2-admin-password.txt`: InfluxDB admin password. <br/>
`influxdb2-admin-token.txt`: InfluxDB admin token. <br/>
If you don't have these credentials, you can create them by following the InfluxDB documentation for creating an admin user and token.

### 3. Launch the Services

To launch InfluxDB 2.x and Grafana services, run the following command:

```bash
docker compose up
```

This command will:

Start InfluxDB 2.x on port `8086`. <br/>
Start Grafana on port `3000`.<br/>
Set up Docker secrets for secure handling of credentials.

### 4. Access Grafana and InfluxDB
Once the services are up and running, you can access Grafana at `http://localhost:3000`.<br/>
InfluxDB at `http://localhost:8086`<br/>
Credentials to login to InfluxDB would be the ones set in txt files.
<img width="1440" alt="Screenshot 2025-03-05 at 11 31 02 PM" src="https://github.com/user-attachments/assets/e7d19ded-9031-44a3-9c66-cf0d88f4eb99" />

Default Grafana login credentials:<br>
Username: admin<br>
Password: admin<br>

<img width="1440" alt="Screenshot 2025-03-05 at 11 37 33 PM" src="https://github.com/user-attachments/assets/d14460a8-6365-4670-b91b-73560167b05d" />

After logging in, you can configure Grafana to connect to InfluxDB as a data source. For example:<br>
URL: http://influxdb2:8086<br>
Database: home<br>
Token: Use the admin token from the influxdb2-admin-token.txt file.<br>

