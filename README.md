# 🔐 Certificate Verifier

A blockchain-powered certificate verification system that enables universities to register certificates and employers to verify their authenticity.

## 🏗️ Architecture

```
Frontend (React) ↔ Backend (FastAPI) ↔ Blockchain (Smart Contract)
```

- **Frontend**: Modern React UI with drag-and-drop file upload
- **Backend**: FastAPI server with certificate validation
- **Blockchain**: Smart contract for immutable certificate registry

## 🚀 Features

### For Universities/Institutions
- **Register Certificates**: Upload and hash certificates on blockchain
- **Immutable Storage**: Permanent, tamper-proof certificate records
- **Batch Processing**: Register multiple certificates efficiently

### For Employers/Verifiers
- **Instant Verification**: Upload certificate to check authenticity
- **Blockchain Lookup**: Verify against decentralized registry
- **Detailed Results**: View issuer, timestamp, and verification status

## 📁 Project Structure

```
Pro-1-cert-verifier/
├── frontend/web/          # React frontend application
│   ├── src/
│   │   ├── components/    # UI components
│   │   │   ├── UploadForm.jsx     # Certificate verification
│   │   │   └── RegisterForm.jsx   # Certificate registration
│   │   └── App.jsx        # Main application
│   └── package.json
├── backend/               # FastAPI backend server
│   ├── app/
│   │   ├── main.py        # API endpoints
│   │   ├── contract_client.py     # Blockchain integration
│   │   └── verification_utils.py  # Validation logic
│   ├── working_main.py    # Simplified server
│   └── requirements.txt
├── blockchain/            # Smart contract & deployment
│   ├── contracts/
│   │   └── CertificateRegistry.sol
│   ├── scripts/deploy.js
│   └── package.json
└── README.md
```

## 🛠️ Installation & Setup

### Prerequisites
- Node.js (v16+)
- Python (3.8+)
- Git

### 1. Clone Repository
```bash
git clone <repository-url>
cd Pro-1-cert-verifier
```

### 2. Backend Setup
```bash
cd backend
pip install -r requirements.txt
python -m uvicorn working_main:app --reload --port 8000
```

### 3. Frontend Setup
```bash
cd frontend/web
npm install
npm run dev
```

### 4. Access Application
- **Frontend**: http://localhost:5176
- **Backend API**: http://localhost:8000
- **API Status**: http://localhost:8000/status

## 🔄 Usage Workflow

### Step 1: Register Certificate (Universities)
1. Go to "Register Certificate" tab
2. Upload certificate file (PDF/JPG/PNG)
3. System generates SHA256 hash
4. Certificate stored on blockchain registry

### Step 2: Verify Certificate (Employers)
1. Go to "Verify Certificate" tab  
2. Upload certificate file
3. System checks against blockchain
4. Results: ✅ Verified or ❌ Invalid

## 🔧 API Endpoints

| Method | Endpoint | Description |
|--------|----------|-------------|
| GET | `/` | API status |
| GET | `/status` | View registered certificates |
| POST | `/register` | Register new certificate |
| POST | `/verify` | Verify certificate authenticity |

## 🧪 Testing

### Test Registration Flow
```bash
# 1. Register a certificate
curl -X POST http://localhost:8000/register \
  -F "file=@certificate.pdf"

# 2. Check status
curl http://localhost:8000/status

# 3. Verify same certificate
curl -X POST http://localhost:8000/verify \
  -F "file=@certificate.pdf"
```

## 🔐 Security Features

- **SHA256 Hashing**: Unique fingerprint for each certificate
- **Content Validation**: File format and keyword verification
- **Blockchain Registry**: Immutable certificate records
- **CORS Protection**: Secure cross-origin requests

## 🌐 Blockchain Integration

### Smart Contract Functions
- `registerCertificate(hash)`: Store certificate hash
- `verifyCertificate(hash)`: Check certificate validity
- `revokeCertificate(hash)`: Invalidate certificate

### Current Implementation
- **Development**: Mock blockchain with in-memory storage
- **Production**: Deploy to Ethereum/Polygon networks

## 📊 Certificate Validation

### Content Checks
- File size limits (100 bytes - 10MB)
- PDF format validation (%PDF header)
- Certificate keywords detection
- Image format verification

### Blockchain Checks
- Hash existence in registry
- Certificate validity status
- Issuer information
- Registration timestamp

## 🚀 Deployment

### Frontend (Netlify/Vercel)
```bash
cd frontend/web
npm run build
# Deploy dist/ folder
```

### Backend (Heroku/AWS)
```bash
cd backend
# Add Procfile: web: uvicorn working_main:app --host=0.0.0.0 --port=${PORT:-5000}
git push heroku main
```

### Blockchain (Hardhat)
```bash
cd blockchain
npx hardhat compile
npx hardhat run scripts/deploy.js --network mainnet
```

## 🔮 Future Enhancements

- [ ] Real blockchain deployment (Ethereum/Polygon)
- [ ] User authentication system
- [ ] Persistent database integration
- [ ] Batch certificate processing
- [ ] Mobile application
- [ ] Certificate templates
- [ ] Analytics dashboard
- [ ] API rate limiting

## 🤝 Contributing

1. Fork the repository
2. Create feature branch (`git checkout -b feature/amazing-feature`)
3. Commit changes (`git commit -m 'Add amazing feature'`)
4. Push to branch (`git push origin feature/amazing-feature`)
5. Open Pull Request

## 📄 License

This project is licensed under the MIT License - see the [LICENSE](LICENSE) file for details.

## 🆘 Troubleshooting

### Common Issues

**Backend 404 Errors**
```bash
# Kill existing processes
taskkill /F /IM python.exe
# Restart server
python -m uvicorn working_main:app --reload --port 8000
```

**Frontend Build Errors**
```bash
# Clear cache and reinstall
rm -rf node_modules package-lock.json
npm install
```

**Port Already in Use**
```bash
# Check what's using port 8000
netstat -ano | findstr :8000
# Kill specific process
taskkill /F /PID <process_id>
```

## 📞 Support

For support and questions:
- Create an issue in the repository
- Check existing documentation
- Review troubleshooting section

---

**Built with ❤️ using React, FastAPI, and Blockchain Technology**
