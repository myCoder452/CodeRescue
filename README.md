# CodeRescue
The signals that save

Access Files: https://mega.nz/folder/6kBgACzZ#QVWn8w5ZOM4KChyIA80cUw

# CodeRescue Platform

CodeRescue is a decentralized disaster response coordination platform designed to bridge the gap between chaotic disaster zones and global technological resources. It enables rapid, autonomous coordination of aid through a resilient network of developers, responders, and community members.

This repository contains the full source code for the **CodeRescue** ecosystem, which consists of:
1.  **Public Website**: The landing, about, and informational pages.
2.  **Web Application**: The secure dashboard (Operative Directory) for registered users to manage reports, messaging, and wallets.
3.  **Backend API**: A Node.js/Express server managing authentication, messaging, and geo-spatial data.

---

## 🏗️ Architecture & Tech Stack

The project is structured as a **monorepo** managing multiple services concurrently.

### 1. Frontend (Public Website & Web App)
-   **Framework**: [React 18+](https://react.dev/)
-   **Build Tool**: [Vite](https://vitejs.dev/)
-   **Routing**: React Router DOM (v6+)
-   **Styling**: Pure CSS with Glassmorphism design system (responsive)
-   **Maps**: [Leaflet](https://leafletjs.com/) & React-Leaflet
-   **Icons**: [Lucide React](https://lucide.dev/)

### 2. Backend (API Server)
-   **Runtime**: Node.js
-   **Framework**: [Express.js](https://expressjs.com/)
-   **Database**: SQLite (Zero-config, localized database for easy deployment)
-   **Authentication**: JWT (JSON Web Tokens)
-   **Real-time**: Socket.io (for messaging and alerts)

### 3. Key Libraries
-   **Blockchain Integration**: `ethers.js`, `@solana/web3.js` (for wallet simulation)
-   **Cryptography**: `crypto-js` (for data security)
-   **Concurrency**: `concurrently` (to run all services with one command)

---

## 🚀 Getting Started

Follow these instructions to set up the project locally on your machine.

### Prerequisites
-   **Node.js**: Version 18.0.0 or higher
-   **npm**: Included with Node.js

### Installation

1.  **Clone the Repository**
    ```bash
    git clone https://github.com/your-username/code-rescue.git
    cd code-rescue
    ```

2.  **Install Dependencies**
    Since this is a monorepo-style setup, dependencies are managed at the root and within the `web-app` directory. Run the install command in the root directory, which will handle the dependencies defined in `package.json`.
    ```bash
    npm install
    ```
    *Note: If you encounter issues, verify that `web-app` dependencies are also installed by running `cd web-app && npm install && cd ..` manually, although the root install typically suffices for this workspace config.*

3.  **Environment Setup**
    The project is pre-configured with sensitive defaults for development (e.g., SQLite file path, Dev Ports). No `.env` file is strictly required to start the simplified dev mode, but check `web-app/server` for specific configurations if deploying.

### Running the Application

To start the entire ecosystem (Website, Web App, and Backend) simultaneously, run:

```bash
npm run dev
```

This command uses `concurrently` to spawn three processes:
1.  **Public Website**: [http://localhost:5173](http://localhost:5173) - The landing page and public info.
2.  **Web App Dashboard**: [http://localhost:5174](http://localhost:5174) - The secure login and dashboard area.
3.  **Backend API**: [http://localhost:3000](http://localhost:3000) - The REST API and Socket server.

> **Tip**: Keep your terminal open to see logs from all three services.

---

## 📂 Project Structure

```text
code-rescue/
├── src/                    # Source for Public Website (Port 5173)
│   ├── pages/              # LandingPage, AboutPage, HowItWorksPage
│   ├── assets/             # Images and global styles
│   └── main.jsx            # Entry point for Website
├── web-app/                # Source for Web Application (Port 5174)
│   ├── src/
│   │   ├── pages/          # Dashboard, Messaging, Profile, Wallet
│   │   ├── components/     # Reusable UI components (Sidebar, ChatWindow)
│   │   ├── services/       # API integration (UserService, MessageService)
│   │   └── context/        # AuthContext and global state
│   └── server/             # Node.js Backend (Port 3000)
│       ├── routes/         # API endpoints (auth, messages, reports)
│       ├── db.js           # SQLite connection & Seeding logic
│       └── app.js          # Express server entry point
├── package.json            # Root dependencies & scripts
└── vite.config.js          # Vite configuration
```

---

## ✨ Key Features

### 1. Operations Dashboard
-   **Global Heatmap**: Visualizes crisis reports in real-time using interactive Leaflet maps.
-   **Crisis Reporting**: Users can submit reports with geolocation, severity, and images.

### 2. Secure Messaging
-   **Real-time Chat**: Instant P2P communication logic.
-   **Features**:
    -   Persistence in SQLite database.
    -   Emoji & Attachment support (UI).
    -   **Edit & Delete**: Full control over message history with soft-delete support.
    -   Sender verification (Current User vs Other).

### 3. Identity & Verification
-   **Role-Based Access**: Specialized views for Developers vs. Reporters.
-   **Profile Management**: Manage skills, languages, and verification status (Mock KYC).

### 4. Financial Rails (Simulated)
-   **Multi-Chain Wallet**: View balances for Ethereum and Solana.
-   **Gasless UX**: UI designed to abstract blockchain complexity.

---

## 🔧 Troubleshooting

**Result: "Address in use" error?**
-   Ensure ports `3000`, `5173`, and `5174` are free.
-   Kill any runaway Node processes: `pkill -f node` (on Linux/Mac) or Task Manager (Windows).

**Result: "Database not initialized"?**
-   The backend automatically creates `database.sqlite` in `web-app/server` on first run. If you see errors, try deleting the `database.sqlite` file and restarting `npm run dev` to re-seed it.

**Result: Images not loading?**
-   Ensure assets are placed in the `public` folder of the respective root. Website images go in `/public`, Web App images go in `web-app/public`.

---

## 🤝 Contribution

CodeRescue is built by a distributed team.
-   **Frontend**: Modify `src/pages` for website changes or `web-app/src` for dashboard features.
-   **Backend**: Edit `web-app/server` files. The server auto-restarts on changes (if nodemon is configured, otherwise restart manually).

**License**: MIT
