# FlexiVault - Advanced DeFi Lending Protocol

[![Stacks](https://img.shields.io/badge/Stacks-Blockchain-orange)](https://stacks.co)
[![Clarity](https://img.shields.io/badge/Language-Clarity-blue)](https://clarity-lang.org)
[![License](https://img.shields.io/badge/License-MIT-green)](LICENSE)

## Overview

FlexiVault revolutionizes decentralized lending by creating a sophisticated marketplace where crypto holders can unlock instant liquidity from their digital assets without losing ownership. Built for the next generation of DeFi, combining security with innovation.

### 🌟 Key Features

- **Dynamic Risk-Adjusted Collateral Management**: Advanced algorithms for optimal collateral utilization
- **Real-time Automated Liquidation Prevention**: Proactive position monitoring and protection
- **Flexible Interest Rate Models**: Market-responsive rates adapting to volatility
- **Multi-Asset Collateral Framework**: Support for BTC and STX with cross-chain compatibility
- **Decentralized Governance**: Community-driven protocol management
- **Enterprise-Grade Security**: Audited smart contracts with transparent operations

## Architecture

FlexiVault utilizes a sophisticated lending protocol that transforms illiquid crypto holdings into active financial instruments through:

- Advanced risk management algorithms
- Real-time market data integration
- Automated liquidation protection mechanisms
- Dynamic interest rate calculations
- Comprehensive collateral ratio management

## Smart Contract Features

### Core Capabilities

| Feature | Description |
|---------|-------------|
| **Collateral Management** | Secure deposit and withdrawal of digital assets |
| **Loan Origination** | Automated loan processing with risk assessment |
| **Interest Calculation** | Block-based compound interest with dynamic rates |
| **Liquidation Protection** | Real-time monitoring and automated position management |
| **Oracle Integration** | Multi-asset price feed management |
| **Governance Controls** | Administrative functions for protocol parameters |

### Supported Assets

- **BTC** - Bitcoin collateral support
- **STX** - Stacks token integration

## Getting Started

### Prerequisites

- [Clarinet](https://github.com/hirosystems/clarinet) - Stacks development environment
- [Node.js](https://nodejs.org/) (v16 or higher)
- [Git](https://git-scm.com/)

### Installation

1. **Clone the repository**

   ```bash
   git clone https://github.com/boluwatife-4/FlexiVault.git
   cd FlexiVault
   ```

2. **Install dependencies**

   ```bash
   npm install
   ```

3. **Verify contract integrity**

   ```bash
   clarinet check
   ```

4. **Run tests**

   ```bash
   npm test
   ```

### Project Structure

```text
FlexiVault/
├── contracts/
│   └── flexi-vault.clar       # Main lending protocol contract
├── tests/
│   └── flexi-vault.test.ts    # Comprehensive test suite
├── settings/
│   ├── Devnet.toml           # Development network configuration
│   ├── Testnet.toml          # Testnet configuration
│   └── Mainnet.toml          # Mainnet configuration
├── Clarinet.toml             # Project configuration
├── package.json              # Node.js dependencies
└── README.md                 # Project documentation
```

## Protocol Usage

### For Borrowers

#### 1. Initialize Platform (Admin Only)

```clarity
(contract-call? .flexi-vault initialize-platform)
```

#### 2. Deposit Collateral

```clarity
(contract-call? .flexi-vault deposit-collateral u1000000) ;; Amount in satoshis
```

#### 3. Request Loan

```clarity
(contract-call? .flexi-vault request-loan 
  u1000000    ;; Collateral amount
  u500000     ;; Loan amount requested
)
```

#### 4. Repay Loan

```clarity
(contract-call? .flexi-vault repay-loan 
  u1          ;; Loan ID
  u525000     ;; Repayment amount (principal + interest)
)
```

### For Administrators

#### Update Risk Parameters

```clarity
;; Update minimum collateral ratio
(contract-call? .flexi-vault update-collateral-ratio u175) ;; 175%

;; Update liquidation threshold
(contract-call? .flexi-vault update-liquidation-threshold u130) ;; 130%
```

#### Manage Price Feeds

```clarity
;; Update BTC price (price in USD cents)
(contract-call? .flexi-vault update-price-feed "BTC" u4500000) ;; $45,000
```

## Risk Parameters

| Parameter | Default Value | Description |
|-----------|---------------|-------------|
| **Minimum Collateral Ratio** | 150% | Required overcollateralization |
| **Liquidation Threshold** | 120% | Automatic liquidation trigger |
| **Platform Fee Rate** | 1% | Protocol service fee |
| **Base Interest Rate** | 5% | Annual interest rate |

## Query Functions

### Loan Information

```clarity
;; Get loan details
(contract-call? .flexi-vault get-loan-details u1)

;; Get user's active loans
(contract-call? .flexi-vault get-user-loans 'SP1234...)

;; Get platform statistics
(contract-call? .flexi-vault get-platform-stats)

;; Get supported assets
(contract-call? .flexi-vault get-valid-assets)
```

## Testing

The protocol includes comprehensive tests covering:

- **Unit Tests**: Individual function validation
- **Integration Tests**: End-to-end workflow testing
- **Edge Cases**: Boundary condition handling
- **Security Tests**: Attack vector prevention

```bash
# Run all tests
npm test

# Run with coverage
npm run test:coverage

# Run specific test file
npm test flexi-vault.test.ts
```

## Security Considerations

### Built-in Protections

- **Access Control**: Role-based permissions for administrative functions
- **Input Validation**: Comprehensive parameter checking
- **Overflow Protection**: Safe arithmetic operations
- **Reentrancy Guards**: State consistency maintenance
- **Oracle Validation**: Price feed integrity verification

### Risk Mitigation

1. **Overcollateralization**: Minimum 150% collateral ratio requirement
2. **Automated Liquidation**: Real-time position monitoring
3. **Price Validation**: Oracle price bounds checking
4. **Asset Whitelisting**: Controlled collateral asset support

## Development

### Running Tests

```bash
# Check contract syntax
clarinet check

# Run unit tests
clarinet test

# Format code
clarinet fmt

# Deploy to devnet
clarinet integrate
```

### Contributing

1. Fork the repository
2. Create a feature branch (`git checkout -b feature/amazing-feature`)
3. Commit your changes (`git commit -m 'Add amazing feature'`)
4. Push to the branch (`git push origin feature/amazing-feature`)
5. Open a Pull Request

## Error Codes

| Code | Description |
|------|-------------|
| `u100` | Not authorized |
| `u101` | Insufficient collateral |
| `u102` | Below minimum requirement |
| `u103` | Invalid amount |
| `u104` | Already initialized |
| `u105` | Not initialized |
| `u106` | Invalid liquidation |
| `u107` | Loan not found |
| `u108` | Loan not active |
| `u109` | Invalid loan ID |
| `u110` | Invalid price |
| `u111` | Invalid asset |

## Roadmap

- [ ] **V2.0**: Multi-collateral support expansion
- [ ] **V2.1**: Cross-chain asset integration
- [ ] **V2.2**: Advanced yield farming features
- [ ] **V2.3**: DAO governance implementation
- [ ] **V2.4**: Insurance protocol integration

## License

This project is licensed under the MIT License - see the [LICENSE](LICENSE) file for details.
