📌 Netdata Monitoring with Docker — Real-time System & App Metrics <br>

📖 Overview
This project demonstrates installing and running Netdata, a free, open-source monitoring tool, using Docker.
With Netdata, you can visualize CPU, memory, disk, network usage, and monitor Docker containers in real time.
It also provides alerts, charts, and logs for troubleshooting and performance optimization.

🚀 Features

Real-time performance monitoring

Web-based dashboard (localhost:19999)

Container monitoring when run with Docker

Lightweight & easy to install

Customizable alerts and charts

🛠 Tools & Technologies

Netdata — Monitoring tool

Docker — Containerized deployment

Linux — Tested on Ubuntu (works on others)

📂 Project Structure <br>
netdata-monitoring/ <br>
│ <br>
├── docker-compose.yml      # Optional: Compose file for Netdata <br>
├── README.md               # Documentation <br>
├── screenshots/            # Proof of dashboard & metrics <br>
└── .gitignore              # Ignore unnecessary files <br>

📝 Steps to Run the Project
```
1️⃣ Install Prerequisites

Install Docker

2️⃣ Run Netdata Container

Using docker run:

docker run -d --name=netdata \
  -p 19999:19999 \
  --cap-add SYS_PTRACE \
  --security-opt apparmor=unconfined \
  -v netdataconfig:/etc/netdata \
  -v netdatalib:/var/lib/netdata \
  -v netdatacache:/var/cache/netdata \
  -v /etc/passwd:/host/etc/passwd:ro \
  -v /etc/group:/host/etc/group:ro \
  -v /proc:/host/proc:ro \
  -v /sys:/host/sys:ro \
  -v /etc/os-release:/host/etc/os-release:ro \
  netdata/netdata
```

Using docker-compose.yml:
```
version: '3'
services:
  netdata:
    image: netdata/netdata
    container_name: netdata
    ports:
      - 19999:19999
    cap_add:
      - SYS_PTRACE
    security_opt:
      - apparmor=unconfined
    volumes:
      - netdataconfig:/etc/netdata
      - netdatalib:/var/lib/netdata
      - netdatacache:/var/cache/netdata
      - /etc/passwd:/host/etc/passwd:ro
      - /etc/group:/host/etc/group:ro
      - /proc:/host/proc:ro
      - /sys:/host/sys:ro
      - /etc/os-release:/host/etc/os-release:ro
volumes:
  netdataconfig:
  netdatalib:
  netdatacache:


Run:

docker-compose up -d

3️⃣ Access Dashboard

Open browser and visit:
http://localhost:19999

4️⃣ Monitor Metrics

CPU usage, memory, disk I/O

Network activity

Docker container stats

Alerts panel

5️⃣ View Logs
docker logs netdata


Or access logs directly inside container:

docker exec -it netdata /bin/bash
cat /var/log/netdata/*
```

📌 Learning Outcomes <br>

✅ Deploy Netdata in Docker <br>
✅ Monitor system & container metrics <br>
✅ Navigate and interpret dashboard charts <br>
✅ Explore real-time alerts & logs
<br><br>
🔗 Repository Info <br>
Repo Name: netdata-monitoring-docker <br>
Description: "Real-time system and Docker container monitoring using Netdata in Docker." <br>

✅ Necessary Files for Your Repo

README.md → Documentation (above)

docker-compose.yml → Optional for easy deployment

.gitignore → To exclude unnecessary files

screenshots/ folder → With proof of dashboard
