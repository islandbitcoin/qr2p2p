# QRBridge

A decentralized QR paycode marketplace connecting global payment systems through crypto settlements.

## Overview

QRBridge enables seamless cross-border payments by allowing users to upload QR codes from local fiat payment systems (PromptPay, QRIS, UPI, etc.) and have them paid by "Earners" who are compensated in cryptocurrency. This creates a bridge between traditional payment rails and the crypto economy.

## Key Features

- **QR Code Marketplace**: Upload and browse payment QR codes from various fiat systems
- **Decentralized Matching**: Connect payment requesters with local earners
- **Crypto Settlements**: Earners receive Bitcoin Lightning or USDT compensation
- **Multi-Region Support**: Support for PromptPay (Thailand), QRIS (Indonesia), UPI (India), and more
- **Real-time Matching**: Instant pairing of payment requests with available earners
- **Escrow Protection**: Secure settlement mechanism protecting both parties

## Use Cases

1. **Cross-border Remittances**: Send money to family abroad without traditional banking
2. **Travel Payments**: Pay local merchants while traveling using your crypto holdings
3. **Freelancer Payments**: Receive payments in crypto while clients pay with local methods
4. **Merchant Services**: Accept global payments while receiving local fiat
5. **Crypto Earning**: Monetize your local payment access by serving international users

## Architecture Overview

```
┌─────────────────┐    ┌──────────────────┐    ┌─────────────────┐
│   Requester     │    │    QRBridge      │    │     Earner      │
│                 │    │    Platform      │    │                 │
│ 1. Upload QR    │───▶│                  │◀───│ 3. Browse Jobs  │
│ 2. Lock Crypto  │    │  Job Matching    │    │ 4. Accept Job   │
│                 │    │  Escrow System   │    │ 5. Pay QR Code  │
│ 6. Release Fund │◀───│  Settlement      │───▶│ 6. Get Crypto   │
└─────────────────┘    └──────────────────┘    └─────────────────┘

Components:
- Frontend: React/Next.js dashboard for job posting and browsing
- Backend: Express/Fastify API for job management and matching
- Core: Shared QR parsing, validation, and settlement logic
- Settlement: Lightning Network and USDT payment processing
```

## Technologies Used

### Frontend
- **React/Next.js**: Modern web framework for responsive UI
- **TypeScript**: Type-safe development
- **TailwindCSS**: Utility-first styling
- **React Query**: Efficient data fetching and caching

### Backend
- **Node.js**: JavaScript runtime
- **Express/Fastify**: Web application framework
- **TypeScript**: Type-safe server development
- **PostgreSQL**: Relational database for job storage
- **Redis**: Caching and real-time matching

### Core Systems
- **QR Code Parsing**: Multi-format QR code interpretation
- **Lightning Network**: Bitcoin micropayments via LND/CLN
- **USDT Integration**: Stablecoin settlements on multiple chains
- **WebSocket**: Real-time job updates and notifications

### Infrastructure
- **Docker**: Containerized deployment
- **NGINX**: Reverse proxy and load balancing
- **PM2**: Process management

## Installation & Setup

### Prerequisites
- Node.js 18+ and npm/yarn/pnpm
- PostgreSQL 14+
- Redis 6+
- Docker (optional)

### Quick Start

```bash
# Clone the repository
git clone https://github.com/your-org/qrbridge.git
cd qrbridge

# Install dependencies
npm install

# Copy environment configuration
cp .env.example .env

# Configure your environment variables
# - Database connection strings
# - Lightning node credentials
# - API keys for supported payment systems

# Run database migrations
npm run db:migrate

# Start development servers
npm run dev

# Backend will run on http://localhost:3001
# Frontend will run on http://localhost:3000
```

### Production Deployment

```bash
# Build the application
npm run build

# Start with PM2
npm run start:prod

# Or use Docker
docker-compose up -d
```

## Environment Variables

Create a `.env` file based on `.env.example`:

```env
# Database
DATABASE_URL=postgresql://user:password@localhost:5432/qrbridge
REDIS_URL=redis://localhost:6379

# Lightning Network
LND_HOST=localhost:10009
LND_MACAROON_PATH=/path/to/admin.macaroon
LND_TLS_CERT_PATH=/path/to/tls.cert

# API Configuration
PORT=3001
JWT_SECRET=your-jwt-secret
CORS_ORIGIN=http://localhost:3000

# Payment System APIs (optional)
PROMPTPAY_API_KEY=your-promptpay-key
QRIS_API_KEY=your-qris-key
UPI_API_KEY=your-upi-key
```

## API Documentation

Once running, visit `/api/docs` for interactive API documentation.

Key endpoints:
- `POST /api/jobs` - Create new payment job
- `GET /api/jobs` - Browse available jobs
- `POST /api/jobs/:id/accept` - Accept a payment job
- `POST /api/settlements/:id/confirm` - Confirm payment completion

## Contributing

We welcome contributions! Please follow these guidelines:

### Development Process
1. Fork the repository
2. Create a feature branch: `git checkout -b feature/amazing-feature`
3. Make your changes and add tests
4. Ensure all tests pass: `npm test`
5. Commit with conventional commits: `git commit -m "feat: add amazing feature"`
6. Push to your fork: `git push origin feature/amazing-feature`
7. Open a pull request

### Code Standards
- Use TypeScript for all new code
- Follow ESLint and Prettier configurations
- Write tests for new features
- Update documentation as needed
- Ensure compatibility with supported payment systems

### Testing
```bash
# Run all tests
npm test

# Run with coverage
npm run test:coverage

# Run e2e tests
npm run test:e2e
```

## Security Considerations

- Always validate QR code authenticity before processing
- Implement proper rate limiting on all endpoints
- Use secure escrow mechanisms for crypto holdings
- Regularly audit smart contracts and settlement logic
- Implement proper KYC/AML procedures where required

## License

This project is licensed under the MIT License - see the [LICENSE](LICENSE) file for details.

## Legal Disclaimers

⚠️ **Important Legal Notice**

### Regulatory Compliance
- QRBridge operates in a complex regulatory environment involving cryptocurrency, cross-border payments, and financial services
- Users are responsible for compliance with local laws and regulations in their jurisdiction
- Some jurisdictions may prohibit or restrict cryptocurrency trading, money transmission, or cross-border payments
- Consult with legal professionals before using this system commercially

### Payment System Risks
- Integration with third-party payment systems (PromptPay, QRIS, UPI) carries inherent risks
- Payment reversals, fraud, or system outages may impact settlements
- QRBridge is not responsible for failures or limitations of underlying payment rails
- Users should understand the terms and risks of each payment system they interact with

### Financial Risks
- Cryptocurrency values are volatile and may result in financial loss
- Settlement times and fees may vary based on network conditions
- Users are responsible for their own funds and private key security
- No guarantee of payment completion or cryptocurrency delivery

### Service Availability
- QRBridge is provided "as is" without warranties of any kind
- Service availability, accuracy, and performance are not guaranteed
- The platform may be discontinued or modified at any time
- Users should not rely on QRBridge for critical or time-sensitive payments

### Data and Privacy
- QR codes may contain sensitive payment information
- Users are responsible for protecting their personal and financial data
- Payment information may be shared with settlement counterparties
- Review our Privacy Policy for detailed data handling practices

By using QRBridge, you acknowledge that you have read, understood, and agree to these disclaimers and assume all associated risks.

## Support

- Documentation: [docs/](docs/)
- Issues: [GitHub Issues](https://github.com/your-org/qrbridge/issues)
- Community: [Discord Server](https://discord.gg/qrbridge)
- Email: support@qrbridge.io

## Roadmap

- [ ] MVP: Basic QR job posting and matching
- [ ] Lightning Network integration
- [ ] USDT settlement support
- [ ] Mobile applications (iOS/Android)
- [ ] Advanced matching algorithms
- [ ] Multi-chain cryptocurrency support
- [ ] Merchant dashboard and APIs
- [ ] Automated compliance tools
- [ ] Decentralized governance token

---

*QRBridge: Bridging the gap between traditional finance and the crypto economy, one QR code at a time.*