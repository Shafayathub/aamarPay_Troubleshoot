# aamarPay_Troubleshoot

## **Troubleshooting Payment Success URL Issues on Vercel**

**If your payment success URL is not functioning correctly on Vercel, follow these steps to resolve the issue:**

### 1. Project Structure

Ensure your project is organized as follows:

```
/project-root
├── public (directory for HTML, CSS, and JS files)
├── src
│   ├── index.ts (or app.ts, server.ts, etc.)
│   ├── app
├── dist (compiled JavaScript files)
├── node_modules
├── package.json
├── tsconfig.json
└── vercel.json
```

### 2. Configure Static File Serving in Express

In your Express app (app.ts), configure it to serve static files from the `public` directory:

```typescript
import express from 'express';
import path from 'path';

const app = express();

// Serve static files from the "public" directory
app.use(express.static(path.join(__dirname, 'public')));
```

### 3. Correct File Paths for Template Rendering

Make sure file paths for your HTML templates are accurate. For example:

```typescript
import { readFileSync } from 'fs';
import { join } from 'path';

const filePath = join(__dirname, '../../../../public/confirmation.html'); // update your html file path
let template = readFileSync(filePath, 'utf-8');

template = template.replace('{{message}}', message);
```

### 4. Deploy to Vercel

Deploy your application with the Vercel CLI:

```bash
npm run build
vercel
vercel --prod
```

*By following these steps, you should be able to resolve issues related to the payment success URL on Vercel.*
