# Power Apps Template - Starter App "Hello World"

## 📋 Step-by-Step Setup Guide
https://learn.microsoft.com/en-us/power-apps/developer/code-apps/how-to/create-an-app-from-scratch
### Step 1: Create Vite Project
```bash
1 mkdir C:\CodeApps -Force
2 cd C:\CodeApps
3 npm create vite@latest AppFromScratch -- --template react-ts
cd C:\CodeApps\AppFromScratch
4 npm install
5 npm i --save-dev @types/node

6 **Open the vite.config.ts, and update to be:**
TypeScript
import { defineConfig } from 'vite'
import react from '@vitejs/plugin-react'
import * as path from 'path'

// https://vite.dev/config/
export default defineConfig({
  base: "./",
  server: {
    host: "::",
    port: 3000,
  },
  plugins: [react()],
  resolve: {
    alias: {
      "@": path.resolve(__dirname, "./src"),
    },
  },
});
---------------------------------------------------------------------
8 npm run dev
9 Initialize your code app
10 pac auth create
11 pac env select -env <URL of your environment>
12 pac code init --displayName "App From Scratch"
13 npm install --save "@microsoft/power-apps"
14 Open the package.json, and update the existing line:
15 "dev": "vite" ----> change to "dev": "start pac code run && vite",

16 Add a new file under the src folder named PowerProvider.tsx and grab the code from
https://github.com/microsoft/PowerAppsCodeApps/blob/main/docs/assets/PowerProvider.tsx
 open main.tsx and add 
 import PowerProvider from './PowerProvider.tsx'
<StrictMode>
  <PowerProvider>
    <App />
  </PowerProvider>
</StrictMode>,
17 npm run dev
npm run build | pac code push