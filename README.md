# medicore-frontend

React 18 SPA for the **MediCore** healthcare platform
([monorepo](https://github.com/Vamshikrishna720/medicore)) — **JavaScript ES6+,
HTML5, hand-written CSS3** (no UI framework), Vite dev server.

## Pages

- **Auth** — login (with one-click demo accounts), register (PATIENT/DOCTOR)
- **Patient** — dashboard, find doctors (filters + booking modal), my appointments (cancel), profile (+ self-deactivation), notifications
- **Doctor** — dashboard with on/off-duty toggle, appointments (confirm / complete / cancel), profile
- **Admin** — stats cards, users table with search + **activate/deactivate**

## Architecture notes

- `services/api.js` — axios instance with **JWT request interceptor** + 401 auto-logout
- `context/AuthContext.jsx` — Context API auth state; `ProtectedRoute` guards by role
- Dev proxy: `/api` → `http://localhost:8080` (the gateway); in Docker, Nginx proxies instead

## Run

```bash
npm install
npm run dev          # http://localhost:5173 (needs the backend stack running)
```

Docker: built stage → Nginx serves `dist/` and proxies `/api` to `api-gateway:8080` → port 3000.
