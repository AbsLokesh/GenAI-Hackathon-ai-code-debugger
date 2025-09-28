# AI Code Debugger

AI Code Debugger is a full-stack web application designed to help developers debug their code efficiently using AI.  
By leveraging the **Llama API**, the platform provides intelligent suggestions, error explanations, and possible fixes to help users resolve bugs faster.  

The project features a **modern frontend (Next.js, React, Tailwind CSS)** and a **backend (Express.js)** for handling API requests and integration with Llama API.  
It also includes **Docker support** for easy development and deployment.

---

## Table of Contents
- [About the Project](#about-the-project)
- [Tech Stack](#tech-stack)
- [Features](#features)
- [Getting Started](#getting-started)
  - [Frontend Setup](#frontend-setup)
  - [Backend Setup](#backend-setup)
  - [Llama API Integration](#llama-api-integration)
- [Backend Details](#backend-details)
- [Docker Setup](#docker-setup)
- [Usage](#usage)
- [Contributing](#contributing)
- [License](#license)

---

## About the Project

AI Code Debugger is built to simplify the debugging process for developers by utilizing AI-powered insights.  
Users can paste code snippets, and the system analyzes, explains errors, and suggests possible fixes in real time.  

This project is ideal for:
- Students learning to code  
- Professionals debugging projects  
- Hackathon teams building AI-powered developer tools  

---

## Tech Stack

- **Frontend:**
  - [React](https://react.dev/)
  - [Next.js](https://nextjs.org/)
  - [Tailwind CSS](https://tailwindcss.com/)

- **Backend:**
  - [Express.js](https://expressjs.com/)

- **AI Integration:**
  - [Llama API](https://llama-api.com/) (for code analysis and suggestions)

- **DevOps:**
  - [Docker](https://www.docker.com/) for containerization

---

## Features
- Paste or upload code snippets for analysis  
- Receive AI-generated debugging tips and explanations  
- Get suggested fixes for detected errors  
- User-friendly, responsive UI  
- Fast and secure API communication  
- Fully containerized with Docker  

---

## Getting Started

### Frontend Setup
```bash
git clone https://github.com/your-username/ai-code-debugger.git
cd ai-code-debugger/frontend
npm install
npm run dev
```

### Backend Setup
```bash
cd ../backend
npm install
```

Create a `.env` file in `backend/`:
```
LLAMA_API_KEY=your_llama_api_key
PORT=5000
```

Run the backend:
```bash
npm start
```

---

## Llama API Integration
- Make sure you have a valid **Llama API key**.  
- The Express.js backend handles communication with Llama API.  
- The frontend communicates with backend via REST APIs.  

---

## Backend Details

The backend acts as a middleware between the frontend and the Llama API.  

### Structure
```
backend/
 ├── src/
 │    ├── index.js         # Entry point
 │    ├── routes/          # API routes
 │    ├── controllers/     # Request handlers
 │    └── services/        # External API integration
 ├── package.json
 └── .env
```

### Scripts
- Start server:
  ```bash
  npm start
  ```
- Development mode:
  ```bash
  npm run dev
  ```

---

## Docker Setup

This project comes with **Docker support** for both frontend and backend.

### Backend Dockerfile (`backend/Dockerfile`)
```dockerfile
FROM node:18-alpine

WORKDIR /app
COPY package*.json ./
RUN npm install --production
COPY . .

ENV PORT=5000
EXPOSE 5000

CMD ["npm", "start"]
```

### Frontend Dockerfile (`frontend/Dockerfile`)
```dockerfile
FROM node:18-alpine

WORKDIR /app
COPY package*.json ./
RUN npm install
COPY . .

RUN npm run build

ENV PORT=3000
EXPOSE 3000

CMD ["npm", "start"]
```

### Docker Compose (`docker-compose.yml`)
```yaml
version: "3.9"

services:
  backend:
    build: ./backend
    ports:
      - "5000:5000"
    env_file:
      - ./backend/.env

  frontend:
    build: ./frontend
    ports:
      - "3000:3000"
    environment:
      - NEXT_PUBLIC_API_URL=http://localhost:5000
    depends_on:
      - backend
```

---

## Running with Docker

1. **Build and run containers:**
   ```bash
   docker-compose up --build
   ```

2. **Access the app:**
   - Frontend → [http://localhost:3000](http://localhost:3000)  
   - Backend → [http://localhost:5000](http://localhost:5000)  

3. **Stop containers:**
   ```bash
   docker-compose down
   ```

---

## Usage
1. Open the web app in your browser.  
2. Paste your code snippet or upload a file.  
3. Click **Analyze** to receive AI-powered debugging feedback.  
4. Review suggestions and explanations; apply fixes as needed.  

---

## Contributing
Contributions, bug reports, and feature requests are welcome!  

1. Fork the repository  
2. Create your feature branch (`git checkout -b feature/your-feature`)  
3. Commit changes (`git commit -m 'Add new feature'`)  
4. Push to the branch (`git push origin feature/your-feature`)  
5. Open a pull request  

---

## License
Distributed under the MIT License. See `LICENSE` for details.  

---

**Happy Debugging! 🚀**
