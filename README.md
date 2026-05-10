# Integrated External Honeypot & Insider Threat Detection System (IEH-ITDS)
## Module: Network Device Scanner

This is a complete, working module for active network ARP scanning, database tracking, and email alerts via Next.js + Flask.

## Backend Setup (Python / Flask)

1. **Install Dependencies**
   ```bash
   cd backend
   pip install flask flask-cors python-dotenv pymysql scapy
   ```

2. **Database Setup**
   Ensure MySQL is running. Run the schema creation file:
   ```bash
   mysql -u root -p < schema.sql
   ```

3. **Configure Environment Variables**
   Copy the example config and add your credentials:
   ```bash
   cp .env.example .env
   # Edit .env and put in real MySQL and Email credentials
   ```

4. **Run the Backend**
   Scapy requires root/sudo privileges to capture packets natively.
   ```bash
   sudo -E python app.py
   # Runs on http://localhost:5000
   ```

## Frontend Setup (Next.js 14 App Router)

1. **Install Dependencies**
   Note: Assuming you have a basic Next.js app setup in `frontend/`. If not, run `npx create-next-app@latest frontend` first, then overwrite the `app` files.
   ```bash
   cd frontend
   npm install
   ```

2. **Run the Next.js App**
   ```bash
   npm run dev
   # Runs on http://localhost:3000
   ```

3. **Access the Dashboard**
   Navigate your browser to `http://localhost:3000/dashboard/network` to view the scanner dashboard and run scans.

## Features
- **Scapy ARP Sweeping:** Efficient local layer 2 discovery
- **Automated Emailing:** Connects to Gmail SMTP for HTML critical alerts on unknown MAC addresses
- **Auto-Refresh:** Frontend pings DB every 5 minutes
- **Glassmorphic UI:** Modern Tailwind components with responsive layouts.
