# KeyCraft Picker - Project Walkthrough

## How to Run the Application
You need to run both the Client (Frontend) and Server (Backend) simultaneously.

### 1. Start the Backend (Server)
1. Open a terminal.
2. Navigate to `server` folder: `cd server`
3. Install dependencies (if not done): `npm install`
4. Create `.env.local` with your MongoDB URI:
   ```env
   MONGODB_URI=mongodb+srv://<username>:<password>@cluster.mongodb.net/keycraft
   ```
5. Seed the database (Optional but recommended): `node scripts/seed.js`
6. Run the server: `npm run dev` (Runs on http://localhost:3000)

### 2. Start the Frontend (Client)
1. Open a **new** terminal.
2. Navigate to `client` folder: `cd client`
3. Install dependencies: `npm install`
4. Run the client: `npm run dev` (Runs on http://localhost:5173)

---

## Features Tour

### Authentication
- Register/Login to access features.

### Admin Dashboard (New Data Models)
- **Add Parts:** The form now adapts to the selected part type.
    - **Cases:** Enter Layout, Mounting Type.
    - **PCBs:** Enter Switch Support (3-pin/5-pin).
    - **Switches:** Enter Brand, Type (Linear/Tactile).
    - **Keycaps:** Enter Material.

### Part Catalog
- Browse parts with specific details (Brand, Material, etc.) now visible.

### Keyboard Builder
- **Real-time Compatibility:** Checks if your selected specific parts work together.
- **Save Build:** Save custom configurations.
