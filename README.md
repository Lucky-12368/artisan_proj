# Artisan Application

A full-stack web application with a React frontend and Node.js/Express backend.

## 📋 Prerequisites

- Node.js >= 16.0.0
- npm >= 8.0.0
- Git

## 📁 Project Structure

```
artisan_proj/
├── client/              # React frontend
│   ├── src/
│   ├── dist/           # Built output
│   ├── package.json
│   ├── vite.config.js
│   └── .env.example
├── server/             # Express backend
│   ├── server.js       # Entry point
│   ├── uploads/        # File uploads directory
│   ├── package.json
│   └── .env.example
├── README.md           # This file
├── .gitignore
└── .github/workflows/  # CI/CD pipelines
```

## 🚀 Getting Started

### Local Development

#### 1. Clone the Repository
```bash
git clone https://github.com/yourusername/artisan_proj.git
cd artisan_proj
```

#### 2. Setup Client

```bash
cd client

# Copy environment variables
cp .env.example .env

# Install dependencies
npm install

# Start development server (runs on http://localhost:3000)
npm run dev
```

#### 3. Setup Server (in a new terminal)

```bash
cd server

# Copy environment variables
cp .env.example .env

# Install dependencies
npm install

# Start server (runs on http://localhost:5000)
npm run dev
```

The client development server is configured to proxy API requests to the backend.

### Build for Production

#### Build Client
```bash
cd client
npm run build
```

This creates an optimized build in `client/dist/`

#### Build Server
The server is ready to use as-is. Just ensure dependencies are installed:
```bash
cd server
npm install
```

## 🌐 Deployment

### Option 1: Deploy to Heroku

#### 1. Create a Heroku App
```bash
heroku create your-app-name
```

#### 2. Set Environment Variables
```bash
heroku config:set NODE_ENV=production
```

#### 3. Deploy
```bash
git push heroku main
```

### Option 2: Deploy to Vercel (Frontend Only)

```bash
cd client
npm install -g vercel
vercel
```

### Option 3: Deploy to GitHub Pages (Frontend Only)

1. Go to repository Settings → Pages
2. Select "Deploy from a branch"
3. Choose `gh-pages` branch
4. The workflow will automatically deploy on every push to `main`

### Option 4: Deploy to Render

#### Create render.yaml

Add this file to the root directory:

```yaml
services:
  - type: web
    name: artisan-app
    env: node
    buildCommand: cd client && npm install && npm run build && cd ../server && npm install
    startCommand: cd server && npm start
    envVars:
      - key: NODE_ENV
        value: production
      - key: PORT
        value: 5000
```

Then push to Render:
```bash
git push
```

## 📝 Environment Variables

### Client (.env)
```
VITE_API_URL=https://your-api-url.com/api
```

### Server (.env)
```
PORT=5000
NODE_ENV=production
```

## 🔧 Available Scripts

### Client
- `npm run dev` - Start development server
- `npm run build` - Build for production
- `npm run preview` - Preview production build
- `npm run lint` - Run linter
- `npm run format` - Format code with Prettier

### Server
- `npm start` - Start server
- `npm run dev` - Start with nodemon (auto-reload)
- `npm test` - Run tests

## 📦 Dependencies

### Client
- React 18.2+
- Vite (build tool)
- Axios (HTTP client)

### Server
- Express 4.18+
- CORS
- Multer (file upload)
- Dotenv (environment variables)

## 🐛 Troubleshooting

### Port Already in Use
Change the port in the respective `.env` file or kill the process using the port.

### CORS Errors
Ensure the client's `VITE_API_URL` matches your server URL in the `.env` file.

### Build Fails
```bash
# Clear caches and reinstall
rm -rf node_modules package-lock.json
npm install
npm run build
```

## 📄 License

MIT License - feel free to use this project for personal or commercial purposes.

## 👤 Author

Your Name - [@yourtwitter](https://twitter.com/yourtwitter)

## 🤝 Contributing

Contributions are welcome! Please feel free to submit a Pull Request.

1. Fork the repository
2. Create your Feature Branch (`git checkout -b feature/AmazingFeature`)
3. Commit your changes (`git commit -m 'Add some AmazingFeature'`)
4. Push to the Branch (`git push origin feature/AmazingFeature`)
5. Open a Pull Request

## 📞 Support

For support, email support@example.com or open an issue on GitHub.
