# 🏭 MES OEE Dashboard — Node-RED

A **Manufacturing Execution System (MES)** built with Node-RED, featuring real-time OEE (Overall Equipment Effectiveness) monitoring, machine data management, and material handling tracking.

> Developed for PT Astra — "Shacio OEE" system

---

## ✨ Features

- 🔐 **Login Page** — User authentication flow
- 📊 **OEE Dashboard** — Real-time visualization of Availability, Performance, and Quality metrics
- 🖊️ **Machine Data Input** — Form to input/update machine parameters (planned time, runtime, cycle time, counts)
- 🚗 **Material Handling** — AGV System & Conveyor System monitoring
- 🗄️ **MySQL Integration** — Persistent storage for machine and OEE data
- 📥 **CSV Export** — OEE report downloadable as CSV (`Laporan_OEE_Mesin1.csv`)

---

## 🧮 OEE Formula

| Metric | Formula |
|---|---|
| **Availability** | Runtime / Planned Time × 100 |
| **Performance** | Ideal Cycle Time × Total Count / Runtime × 100 |
| **Quality** | Good Count / Total Count × 100 |
| **OEE** | Availability × Performance × Quality |

---

## 🛠️ Tech Stack

| Layer | Technology |
|---|---|
| Flow Engine | [Node-RED](https://nodered.org/) |
| UI Dashboard | node-red-dashboard |
| Database | MySQL (`node-red-node-mysql`) |
| Frontend | Custom HTML/CSS/JS (injected via Template nodes) |

---

## 📋 Prerequisites

- Node.js (v18+ recommended)
- Node-RED
- MySQL Server
- Node-RED Nodes:
```bash
  npm install node-red-dashboard
  npm install node-red-node-mysql
```

---

## 🚀 Getting Started

1. **Clone this repository**
```bash
   git clone https://github.com/YOUR_USERNAME/node-red-mes-oee.git
   cd node-red-mes-oee
```

2. **Set up the MySQL database**
   - Create a database (e.g., `mes_oee`)
   - Create the required tables:
```sql
     CREATE TABLE machine (
       id INT AUTO_INCREMENT PRIMARY KEY,
       machine_code VARCHAR(50),
       machine_name VARCHAR(100),
       location VARCHAR(100),
       status VARCHAR(50),
       shift VARCHAR(10),
       planned_time FLOAT,
       runtime FLOAT,
       ideal_cycle_time FLOAT,
       total_count INT,
       good_count INT
     );
```

3. **Import the flow**
   - Open Node-RED (`http://localhost:1880`)
   - Go to **Menu → Import → Select File**
   - Import `flows (2).json`

4. **Configure MySQL credentials**
   - In Node-RED, find the MySQL config node
   - Update host, port, database name, username, and password

5. **Deploy and access**
   - Click **Deploy** in Node-RED
   - Open the dashboard: `http://localhost:1880/ui`
   - Open the OEE input form: `http://localhost:1880/oee`

---

## 📁 Project Structure

```
node-red-mes-oee/
├── flows (2).json          # Main Node-RED flow (import this)
├── Laporan_OEE_Mesin1.csv  # Sample OEE report output
└── README.md
```

---

## 📸 Flow Overview

| Tab | Description | Preview |
|---|---|---|
| `Login` | User authentication flow | ![Login](https://github.com/user-attachments/assets/a21f5ca6-1920-4a65-8084-a5736d379508) |
| `Dashboard OEE PT Astra` | Main OEE monitoring dashboard | ![Dashboard](https://github.com/user-attachments/assets/8e5f7f77-b0ee-48a7-8e5f-11f3bf7bef07) |
| `Input` | Machine data entry form with MySQL upsert logic | ![Input](https://github.com/user-attachments/assets/789d4236-19f6-4541-9f74-83e49bc02a9c) |
| `Dataset Dashboard` | Tabular view of OEE records | ![Dataset](https://github.com/user-attachments/assets/6c775a84-c323-452d-b91c-0c5896ef3f9e) |
---

## 📄 License

MIT License — feel free to use and adapt for your own MES projects.

---

## 🤝 Contributing

Pull requests are welcome! For major changes, please open an issue first.
