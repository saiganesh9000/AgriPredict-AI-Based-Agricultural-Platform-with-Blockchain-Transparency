# 📦 Guide: Splitting into Separate Repositories

This guide will help you split the monorepo into two separate repositories:
1. **Backend Repository** (Python FastAPI)
2. **Frontend Repository** (React + Hardhat)

## 🎯 Overview

- **Backend Repo**: Contains Python FastAPI backend, ML models, and database
- **Frontend Repo**: Contains React frontend, Hardhat contracts, and blockchain code

## 📋 Step-by-Step Instructions

### Option 1: Create New Repositories (Recommended)

#### For Backend Repository:

1. **Create a new repository** (e.g., `agri-insights-backend`)

2. **Copy backend files to new location:**
   ```bash
   # Create new directory
   mkdir ../agri-insights-backend
   cd ../agri-insights-backend
   
   # Initialize git
   git init
   
   # Copy backend files
   cp -r ../agri-insights-2026/backend/* .
   
   # Copy backend .gitignore
   cp ../agri-insights-2026/backend/.gitignore .
   ```

3. **Create backend README** (already exists in backend/README.md)

4. **Commit and push:**
   ```bash
   git add .
   git commit -m "Initial commit: Backend API"
   git remote add origin <your-backend-repo-url>
   git push -u origin main
   ```

#### For Frontend Repository:

1. **Create a new repository** (e.g., `agri-insights-frontend`)

2. **Copy frontend files to new location:**
   ```bash
   # Create new directory
   mkdir ../agri-insights-frontend
   cd ../agri-insights-frontend
   
   # Initialize git
   git init
   
   # Copy frontend files
   cp -r ../agri-insights-2026/src .
   cp -r ../agri-insights-2026/public .
   cp -r ../agri-insights-2026/contracts .
   cp -r ../agri-insights-2026/scripts .
   cp -r ../agri-insights-2026/test .
   cp -r ../agri-insights-2026/ignition .
   cp ../agri-insights-2026/package.json .
   cp ../agri-insights-2026/package-lock.json .
   cp ../agri-insights-2026/vite.config.ts .
   cp ../agri-insights-2026/tsconfig*.json .
   cp ../agri-insights-2026/tailwind.config.ts .
   cp ../agri-insights-2026/postcss.config.js .
   cp ../agri-insights-2026/components.json .
   cp ../agri-insights-2026/eslint.config.js .
   cp ../agri-insights-2026/hardhat.config.cjs .
   cp ../agri-insights-2026/index.html .
   cp ../agri-insights-2026/.gitignore.frontend .gitignore
   ```

3. **Update frontend README** (create a frontend-specific one)

4. **Commit and push:**
   ```bash
   git add .
   git commit -m "Initial commit: Frontend + Blockchain"
   git remote add origin <your-frontend-repo-url>
   git push -u origin main
   ```

### Option 2: Use Git Subtree (Advanced)

If you want to keep them in the same repo but manage separately:

```bash
# For backend
git subtree push --prefix=backend origin backend-main

# For frontend
git subtree push --prefix=. origin frontend-main
```

## 📁 File Organization

### Backend Repository Should Include:
```
backend/
├── main.py
├── database.py
├── models.py
├── train_models.py
├── app.py (Streamlit - optional)
├── requirements.txt
├── README.md
├── .gitignore
├── models/
│   ├── *.pkl
│   └── accuracy.txt
├── *.csv (datasets)
└── agri_insights.db (should be in .gitignore)
```

### Frontend Repository Should Include:
```
frontend/
├── src/
├── public/
├── contracts/
├── scripts/
├── test/
├── ignition/
├── package.json
├── package-lock.json
├── vite.config.ts
├── hardhat.config.cjs
├── tsconfig*.json
├── tailwind.config.ts
├── postcss.config.js
├── components.json
├── eslint.config.js
├── index.html
├── README.md
└── .gitignore
```

## ⚙️ Configuration Updates Needed

### Backend:
- Update CORS in `main.py` to allow frontend URL
- Update API documentation with frontend URL

### Frontend:
- Update `src/services/api.ts` if backend URL changes
- Update README with backend API URL

## 🔗 Linking the Repositories

After splitting, you can:

1. **Add backend repo as submodule** (if needed):
   ```bash
   git submodule add <backend-repo-url> backend
   ```

2. **Or use separate repos** and document the connection in README files

## 📝 Notes

- The blockchain contracts (`contracts/`, `hardhat.config.cjs`) go with the frontend since they're used there
- Database file (`agri_insights.db`) should be in `.gitignore` for backend
- Model files (`.pkl`) can be committed or ignored based on your preference
- Update README files in each repo to reference the other
