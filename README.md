# 🌾 AgriInsights 2026 (AgriPredict)

A comprehensive agricultural marketplace platform combining **AI-powered analytics** and **Blockchain transparency** to modernize the agricultural supply chain. Connect farmers, buyers, and logistics providers in a secure, transparent marketplace.

## ✨ Features

### 🤖 AI & Machine Learning
- **Price Prediction**: Get optimal selling prices for crops based on historical data, market location, season, and quality (~92% accuracy)
- **Demand Forecasting**: Predict market demand levels (Low/Medium/High) to help plan harvest and sales strategy (~92% accuracy)

### 🔐 Blockchain Integration
- **Secure Payments**: Direct ETH transfers from buyers to farmers using Ethereum blockchain
- **Transaction Verification**: Every transaction generates a transaction hash for immutable proof of purchase
- **Wallet Authentication**: All users authenticate via MetaMask or Hardhat test accounts
- **Smart Contracts**: Solidity contracts for marketplace operations (AgriMarketplace.sol)

### 👥 Role-Based Dashboards
- **Farmer Dashboard**: Price prediction, demand forecasting, and crop listing tools
- **Buyer Dashboard**: Browse marketplace, purchase crops, and verify transactions
- **Logistics Dashboard**: Track orders and update delivery status through the lifecycle

### 📱 Modern UI/UX
- **Responsive Design**: Works seamlessly on desktop, tablet, and mobile devices
- **Beautiful Interface**: Built with Tailwind CSS and shadcn/ui components
- **Smooth Animations**: Framer Motion for polished user experience

## 🛠️ Tech Stack

### Frontend
- **React 18** + **TypeScript** + **Vite** - Modern frontend framework
- **Tailwind CSS** + **shadcn/ui** - Beautiful, accessible UI components
- **Ethers.js v6** - Blockchain interactions and wallet management
- **Framer Motion** - Smooth animations and transitions
- **React Query** - Efficient data fetching and state management
- **React Router** - Client-side routing

### Backend
- **FastAPI** (Python) - High-performance API framework
- **Scikit-learn** - Machine learning models (Random Forest Regressors)
- **SQLAlchemy** - Database ORM
- **SQLite** - Lightweight database
- **Pandas** - Data manipulation for ML
- **Joblib** - Model serialization

### Blockchain
- **Hardhat** - Ethereum development environment
- **Solidity ^0.8.0** - Smart contract language
- **Ethers.js** - Web3 library for frontend
- **Local Hardhat Node** - Development blockchain

## 📋 Prerequisites

Before you begin, ensure you have the following installed:

- **Node.js** (v18 or higher) - [Download](https://nodejs.org/)
- **Python** (3.8 or higher) - [Download](https://www.python.org/downloads/)
- **npm** or **yarn** (comes with Node.js)
- **Git** - [Download](https://git-scm.com/downloads)

## 🚀 Installation & Setup

### 1. Clone the Repository

```bash
git clone <your-repo-url>
cd agri-insights-2026
```

### 2. Install Frontend Dependencies

```bash
npm install
```

This will install all React, TypeScript, Hardhat, and other frontend dependencies.

### 3. Install Backend Dependencies

```bash
cd backend
pip install -r requirements.txt
cd ..
```

**Recommended**: Use a virtual environment:

```bash
cd backend
python -m venv venv
source venv/bin/activate  # On Windows: venv\Scripts\activate
pip install -r requirements.txt
cd ..
```

### 4. Train ML Models (First Time Setup)

The project includes pre-trained models in `backend/models/`, but if you want to retrain them:

```bash
cd backend
python train_models.py
cd ..
```

This will generate:
- `price_model.pkl` - Price prediction model
- `price_encoders.pkl` - Feature encoders for price prediction
- `demand_model.pkl` - Demand forecasting model
- `demand_encoders.pkl` - Feature encoders for demand forecasting

## 🏃 Running the Application

You need to run **three services** simultaneously:

### Terminal 1: Start Hardhat Local Blockchain

```bash
npx hardhat node
```

This will:
- Start a local Ethereum node on `http://localhost:8545`
- Create 20 test accounts, each with 10,000 ETH
- Display account addresses and private keys

**Keep this terminal running** - you'll need it for all blockchain transactions.

### Terminal 2: Start Backend API Server

```bash
cd backend
python main.py
```

Or if using a virtual environment:

```bash
cd backend
source venv/bin/activate  # On Windows: venv\Scripts\activate
python main.py
```

The API will be available at:
- **API Base URL**: `http://localhost:8000`
- **API Documentation**: `http://localhost:8000/docs` (Swagger UI)
- **Alternative Docs**: `http://localhost:8000/redoc`

### Terminal 3: Start Frontend Development Server

```bash
npm run dev 
```

The application will be available at:
- **Frontend URL**: `http://localhost:8080`

## 🎯 Project Structure

```
agri-insights-2026/
├── backend/                    # Python FastAPI Backend
│   ├── main.py                # FastAPI application entry point
│   ├── database.py            # SQLAlchemy database configuration
│   ├── models.py              # Database models (User, Product, Order)
│   ├── train_models.py        # ML model training script
│   ├── app.py                 # Streamlit app (optional/legacy)
│   ├── requirements.txt       # Python dependencies
│   ├── README.md              # Backend-specific documentation
│   ├── models/                # Trained ML models
│   │   ├── price_model.pkl
│   │   ├── price_encoders.pkl
│   │   ├── demand_model.pkl
│   │   ├── demand_encoders.pkl
│   │   └── accuracy.txt
│   ├── *.csv                  # Training datasets
│   └── agri_insights.db       # SQLite database (auto-created)
│
├── contracts/                 # Solidity Smart Contracts
│   └── AgriMarketplace.sol    # Main marketplace contract
│
├── src/                       # React Frontend Source
│   ├── components/            # React components
│   │   ├── auth/             # Authentication modals
│   │   │   ├── SignInModal.tsx
│   │   │   └── SignUpModal.tsx
│   │   ├── dashboard/        # Role-specific dashboards
│   │   │   ├── FarmerDashboard.tsx
│   │   │   ├── BuyerDashboard.tsx
│   │   │   ├── LogisticsDashboard.tsx
│   │   │   ├── PricePredictionForm.tsx
│   │   │   └── DemandForecastingForm.tsx
│   │   └── ui/               # shadcn/ui components
│   ├── contexts/             # React contexts
│   │   └── WalletContext.tsx # Wallet state management
│   ├── pages/                # Page components
│   │   ├── Index.tsx         # Landing page
│   │   ├── Dashboard.tsx     # Main dashboard
│   │   └── NotFound.tsx      # 404 page
│   ├── services/             # API service functions
│   │   └── api.ts            # Backend API client
│   ├── utils/                # Utility functions
│   │   └── currency.ts       # Currency formatting
│   └── main.tsx              # React entry point
│
├── public/                    # Static assets
├── scripts/                   # Hardhat scripts
├── test/                      # Tests
├── ignition/                  # Hardhat Ignition modules
├── hardhat.config.cjs        # Hardhat configuration
├── vite.config.ts            # Vite configuration
├── package.json              # Frontend dependencies
└── README.md                 # This file
```

## 👤 User Guide

### Getting Started

1. **Start all three services** (Hardhat node, Backend API, Frontend dev server)
2. **Open** `http://localhost:8080` in your browser
3. **Sign Up** or **Sign In** using one of the test accounts

### Sign Up / Sign In

#### Sign Up (New Users)
1. Click **"Sign Up"** in the navbar
2. Select a wallet account from the list:
   - **Account #0** - Pre-configured as Farmer
   - **Account #1** - Pre-configured as Buyer
   - **Account #2** - Pre-configured as Logistics
3. Choose your role (Farmer, Buyer, or Logistics)
4. Click **"Create Account"**

#### Sign In (Existing Users)
1. Click **"Sign In"** in the navbar
2. Select your wallet account
3. You'll be automatically authenticated and redirected to your dashboard

### 👨‍🌾 Farmer Dashboard

**Features:**
- **Price Prediction**: Get AI-powered price suggestions
- **Demand Forecasting**: Check market demand levels
- **List Products**: Create marketplace listings

**How to Use:**
1. Sign in as a Farmer (Account #0)
2. Navigate to Dashboard
3. **Price Suggestion Tab**:
   - Fill in crop details (type, location, quantity, quality, etc.)
   - Click **"Get Price Suggestion"**
   - Review the AI-suggested price
4. **List for Sale**:
   - After getting a price suggestion, click **"List for Sale"**
   - Review and adjust the final selling price if needed
   - Submit to create a marketplace listing

### 🛒 Buyer Dashboard

**Features:**
- **Browse Marketplace**: View all available crop listings
- **Purchase Crops**: Buy directly from farmers using blockchain
- **Transaction Verification**: View transaction hashes

**How to Use:**
1. Sign in as a Buyer (Account #1)
2. Navigate to Dashboard
3. Browse available products in the marketplace
4. Click **"Buy Now"** on a product
5. Fill in shipping details (address and phone number)
6. Click **"Confirm & Pay"**
7. Transaction is processed on the blockchain
8. Receive transaction hash for verification
9. Order is created and sent to Logistics

### 🚚 Logistics Dashboard

**Features:**
- **View Orders**: See all orders that need fulfillment
- **Update Status**: Track orders through lifecycle
- **Transaction Verification**: Verify payments via transaction hashes

**How to Use:**
1. Sign in as Logistics (Account #2)
2. Navigate to Dashboard
3. View all pending orders with details:
   - Product information
   - Buyer and farmer locations
   - Transaction hash
   - Current status
4. Click on an order to update its status:
   - **Pending** → **Picked Up** → **In Transit** → **Delivered**
5. Status updates are reflected in real-time

## 🔌 API Endpoints

### Authentication
- `POST /auth/login` - Sign up or sign in a user
  ```json
  {
    "wallet_address": "0x...",
    "role": "farmer" | "buyer" | "logistics"
  }
  ```

### ML Predictions
- `POST /predict_price` - Get price prediction for crops
  ```json
  {
    "date": "2026/01/18",
    "commodity_group": "Millet",
    "crop_type": "Jowar (Sorghum)",
    "state_name": "Andhra Pradesh",
    "market_location": "Adoni",
    "quantity_kg": 100.0,
    "quality_grade": 3,
    "season": "Kharif",
    "transport_cost": 20.0,
    "demand_index": 1.0
  }
  ```

- `POST /forecast_demand` - Get demand forecast
  ```json
  {
    "date": "2026/01/18",
    "commodity_group": "Millet",
    "crop_type": "Jowar (Sorghum)",
    "state_name": "Andhra Pradesh",
    "market_location": "Adoni",
    "season": "Kharif",
    "total_quantity_sold": 1000.0,
    "avg_price_per_kg": 50.0,
    "historical_demand_7d": 500.0,
    "price_trend_7d": 50.0,
    "estimated_production_kg": 10000.0,
    "policy_support_score": 0.8,
    "festival_flag": 0,
    "weather_index": 0.7
  }
  ```

### Products
- `GET /products` - Get all available products (unsold)
- `POST /products` - Create a new product listing

### Orders
- `GET /orders` - Get all orders
- `GET /orders/{wallet_address}` - Get orders for a specific user
- `POST /orders` - Create a new order
- `PATCH /orders/{order_id}/status` - Update order status

### Users
- `GET /users/{wallet_address}` - Get user role by wallet address

**Full API Documentation**: Visit `http://localhost:8000/docs` when the backend is running.

## 🔐 Hardhat Test Accounts

When you run `npx hardhat node`, you get 20 test accounts. The first 3 are pre-configured:

| Account | Address | Role | Balance |
|---------|---------|------|---------|
| #0 | `0xf39Fd6e51aad88F6F4ce6aB8827279cffFb92266` | Farmer | 10,000 ETH |
| #1 | `0x70997970C51812dc3A010C7d01b50e0d17dc79C8` | Buyer | 10,000 ETH |
| #2 | `0x3C44CdDdB6a900fa2b585dd299e03d12FA4293BC` | Logistics | 10,000 ETH |

Each account starts with 10,000 ETH for testing transactions.

## 🧪 Development

### Running Tests

```bash
# Run all Hardhat tests
npx hardhat test

# Run Solidity tests only
npx hardhat test solidity

# Run TypeScript/Mocha tests only
npx hardhat test mocha
```

### Building for Production

```bash
# Build frontend
npm run build

# Preview production build
npm run preview
```

### Database Management

The SQLite database (`backend/agri_insights.db`) is automatically created when you first run the backend. 

**To reset the database:**
```bash
cd backend
rm agri_insights.db  # On Windows: del agri_insights.db
python main.py       # Database will be recreated
```

### Smart Contract Deployment

To deploy the AgriMarketplace contract to the local Hardhat node:

```bash
# Deploy to local network
npx hardhat ignition deploy ignition/modules/AgriMarketplace.ts --network localhost
```

**Note**: You'll need to create an Ignition module for AgriMarketplace first, or deploy manually using Hardhat scripts.

## 🐛 Troubleshooting

### Backend Issues

**Problem**: Backend won't start
- ✅ Ensure Python 3.8+ is installed: `python --version`
- ✅ Check if port 8000 is available
- ✅ Verify dependencies: `pip install -r backend/requirements.txt`
- ✅ Check if models exist: `ls backend/models/*.pkl`

**Problem**: ML models not loading
- ✅ Ensure models are trained: `cd backend && python train_models.py`
- ✅ Check that `backend/models/` contains `.pkl` files

**Problem**: Database errors
- ✅ Delete and recreate: `rm backend/agri_insights.db && python backend/main.py`

### Frontend Issues

**Problem**: Frontend won't start
- ✅ Ensure Node.js 18+ is installed: `node --version`
- ✅ Clear and reinstall: `rm -rf node_modules && npm install`
- ✅ Check if port 8080 is available

**Problem**: Cannot connect to backend
- ✅ Verify backend is running on `http://localhost:8000`
- ✅ Check CORS settings in `backend/main.py`
- ✅ Verify API URL in `src/services/api.ts`

### Blockchain Issues

**Problem**: Hardhat node won't start
- ✅ Ensure Hardhat is installed: `npm install`
- ✅ Check if port 8545 is available
- ✅ Verify `hardhat.config.cjs` exists

**Problem**: Transactions not working
- ✅ Ensure Hardhat node is running: `npx hardhat node`
- ✅ Verify you're using correct wallet address
- ✅ Check account has sufficient balance
- ✅ Verify transaction is being sent to correct address

**Problem**: Wallet connection issues
- ✅ Check browser console for errors
- ✅ Verify Hardhat node is accessible at `http://localhost:8545`
- ✅ Try refreshing the page and reconnecting

## 📝 Environment Variables

Currently, the project uses default configurations. For production, you may want to set:

### Frontend (`.env`)
```env
VITE_API_BASE_URL=http://localhost:8000
VITE_HARDHAT_NODE_URL=http://localhost:8545
```

### Backend (`.env`)
```env
DATABASE_URL=sqlite:///./agri_insights.db
CORS_ORIGINS=http://localhost:8080
API_PORT=8000
```

## 🔒 Security Notes

- **Development Only**: This setup is for development. For production:
  - Use proper authentication (signature verification)
  - Set up proper CORS origins
  - Use environment variables for sensitive data
  - Deploy smart contracts to a testnet/mainnet
  - Use HTTPS for all connections
  - Implement rate limiting on API endpoints

## 🤝 Contributing

1. Fork the repository
2. Create a feature branch (`git checkout -b feature/amazing-feature`)
3. Commit your changes (`git commit -m 'Add some amazing feature'`)
4. Push to the branch (`git push origin feature/amazing-feature`)
5. Open a Pull Request

## 📄 License

This project is licensed under the MIT License.

## 🙏 Acknowledgments

- Built with React, FastAPI, and Hardhat
- UI components from [shadcn/ui](https://ui.shadcn.com/)
- ML models trained with Scikit-learn
- Blockchain development with Hardhat

## 📞 Support

For issues, questions, or contributions:
- Open an issue on the repository
- Check the API documentation at `http://localhost:8000/docs`
- Review the backend README at `backend/README.md`

---

**Happy Farming! 🌾**
