# Linvest21 Private Public Service API - Comprehensive Documentation

## Table of Contents
1. [API Overview](#api-overview)
2. [Authentication & Base Information](#authentication--base-information)
3. [HTTP Methods & Response Codes](#http-methods--response-codes)
4. [API Categories](#api-categories)
5. [Detailed Endpoint Documentation](#detailed-endpoint-documentation)
6. [Common Schema Patterns](#common-schema-patterns)
7. [Best Practices](#best-practices)

## API Overview

- **API Title**: Private Public Service API for Linvest21
- **Version**: 1.0.0
- **OpenAPI Specification**: 3.1.0
- **Base URL**: `/`
- **Total Endpoints**: 304 endpoints
- **Primary Purpose**: Institutional investment management platform

### Key Features
- ✅ Portfolio optimization and management
- ✅ Advanced analytics and research tools
- ✅ Fixed income specialized analytics
- ✅ Multi-custodian data integration
- ✅ Private and public security management
- ✅ Real-time market data processing
- ✅ Bulk operations and template processing
- ✅ Performance analysis and reporting

## Authentication & Base Information

**Server Configuration**:
```yaml
servers:
  - url: "/"
    description: "Default Server URL"
```

**Primary Tags**:
- `Fixed Income Analytics` - APIs for Fixed Income portfolio analytics and metrics
- `Private Security Management` - APIs for managing private securities in accounts

## HTTP Methods & Response Codes

### Method Distribution
| Method | Count | Usage |
|--------|-------|--------|
| GET    | 202 (66.4%) | Data retrieval, analytics, reports |
| POST   | 81 (26.6%)  | Create operations, bulk processing |
| PUT    | 31 (10.2%)  | Updates, validations |
| DELETE | 20 (6.6%)   | Resource deletion |

### Standard Response Codes
- **200 OK** - Successful operation
- **400 Bad Request** - Invalid request parameters or malformed request
- **402 Payment Required** - Payment/subscription required for operation
- **404 Not Found** - Resource not found or doesn't exist

## API Categories

### 1. Portfolio Optimization & Management (37 endpoints)

Core portfolio optimization functionality including weight validation, metrics calculation, and optimization event management.

**Key Endpoints**:
- `PUT /api/v3/fundamental/bulk/validatealloc` - Validate bulk post optimisation weight (simple)
- `PUT /api/v2/fundamental/bulk/validatealloc` - Validate bulk post optimisation weight (new)
- `PUT /api/v2/fundamental/bulk/calcpostoptmetrics` - Calculate post optimisation metrics only
- `POST /api/optevent/new` - Create new optimization event
- `POST /api/optimisationdefinition/new` - Create new optimization definition

### 2. Fixed Income Analytics (17 endpoints)

Specialized analytics suite for fixed income portfolios.

**Analytics Available**:
- Yield to maturity comparison
- Yield curve analysis
- Duration and convexity risk
- Credit quality assessment
- Sector allocation analysis
- Liquidity metrics
- Return attribution

**Key Endpoints**:
- `GET /api/analytics/fi/charts/ytm-comparison/{accountId}` - YTM comparison charts
- `GET /api/analytics/fi/charts/yield-curve/{accountId}` - Yield curve analysis
- `GET /api/analytics/fi/charts/duration-risk/{accountId}` - Duration risk metrics
- `GET /api/analytics/fi/charts/credit-quality/{accountId}` - Credit quality breakdown

### 3. Research & Analytics (18 endpoints)

Comprehensive research and analytical capabilities for portfolio analysis.

**Research Tools**:
- Stress scenario analysis
- Value at Risk (VaR) calculations
- Holdings analysis (top/bottom performers)
- Alpha/Beta calculations
- Economic indicators
- Sector performance tracking

**Key Endpoints**:
- `GET /api/research/portfolio/var/{portfolioId}/{fromDate}/{toDate}` - Portfolio VaR
- `GET /api/research/stressscenario/{portfolio_id}/{scenario_id}/{from_date}/{to_date}` - Stress testing
- `GET /api/research/alphabeta/{portfolioId}/{from_date}/{to_date}` - Alpha/Beta metrics
- `GET /api/research/portfolio/toptenholdings/{portfolio_id}/{duration}` - Top holdings

### 4. ACIO (Adaptive Core Investment Optimization) (13 endpoints)

Advanced adaptive investment optimization system.

**Capabilities**:
- ACIO definition management
- Strategy mapping
- Account mapping  
- Style rotation models
- Sector rotation models
- Asset class rotation models

**Key Endpoints**:
- `GET/POST /api/acio/definition` - Manage ACIO definitions
- `PUT /api/acio/strategy/definition` - Map strategy to ACIO
- `GET /api/acio/stylerotationmodel/{model_id}/{universe_id}` - Style rotation data

### 5. Account Management & Holdings (24 endpoints)

Complete account lifecycle management and holdings tracking.

**Account Operations**:
- Account creation and updates
- Holdings management and trends
- Performance tracking
- Factor exposure analysis
- Cash flow analysis
- Sleeve management

**Key Endpoints**:
- `POST /api/account/create` - Create new account
- `PUT /api/account/update` - Update account information
- `GET /api/v4/account/sector/holding/{accountId}` - Account sector holdings
- `GET /api/account/holding/trend/{account_Id}/{fromDate}/{toDate}/{isRelative}` - Holding trends

### 6. Security & Market Data (18 endpoints)

Security information, pricing, and market data management.

**Data Types**:
- Security attributes and characteristics
- Price and return data
- Financial statements (income, balance sheet, cash flow)
- Financial ratios and valuations
- Company profiles
- ETF/MF constituents

**Key Endpoints**:
- `GET /api/security/returns/{securityId}/{fromDate}/{toDate}` - Security returns
- `GET /api/security/prices` - Current security prices
- `GET /api/security/financials/{securityId}` - Financial data
- `GET /api/public-shared/companyProfile/{securityId}` - Company information

### 7. Private Security Management (7 endpoints)

Specialized management for private securities and transactions.

**Features**:
- Private security CRUD operations
- Transaction processing
- Transaction history tracking
- Account-specific private holdings

**Key Endpoints**:
- `PUT/POST/DELETE /api/v1/private/security-management/securities` - Manage private securities  
- `POST /api/v1/private/security-management/transactions` - Process transactions
- `GET /api/v1/private/security-management/transactions/history/{accountId}/{securityId}` - Transaction history

### 8. Custodian Data Integration (10 endpoints)

Multi-custodian data integration and processing.

**Data Processing**:
- PDF data validation
- Transaction data import
- Position data import
- Tax lot management
- Realized gain/loss tracking

**Key Endpoints**:
- `POST /api/custodian-data/validate-pdf-data` - Validate PDF imports
- `POST /api/custodian-data/save-transactions` - Import transaction data
- `POST /api/custodian-data/save-positions` - Import position data

### 9. ByAllAccounts Integration (18 endpoints)

External account aggregation service integration.

**Integration Features**:
- Transaction retrieval and storage
- Position data synchronization
- Account summary aggregation
- Data loading status tracking
- Person and advisor management

**Key Endpoints**:
- `GET /api/v1/byallaccounts/transactions` - External transactions
- `GET /api/v1/byallaccounts/positions` - External positions
- `POST /api/by-all-accounts-data/retrieveAndSaveTransaction/{linvestAccountId}` - Sync transactions

### 10. Reference Data & Utilities (15+ endpoints)

System reference data and utility functions.

**Reference Data**:
- Security types and product types
- Geographic data (states, cities, countries)
- Currencies and market calendars
- Classification models
- Benchmark data

**Key Endpoints**:
- `GET /api/securitytypes/all` - All security types
- `GET /api/currencies` - Available currencies  
- `GET /api/calendar/next-business-day/{date}` - Business day calculations
- `GET /api/benchmark/all/{asOfDate}` - Benchmark data

## Detailed Endpoint Documentation

### Portfolio Optimization Endpoints

#### Validate Bulk Post Optimization Weight (Simple)
```
PUT /api/v3/fundamental/bulk/validatealloc
```
**Purpose**: Simplified validation of multiple accounts' holdings weights after optimization

**Request Body**: Array of `AccountHoldingValidationRequest`
```json
{
  "type": "array",
  "items": {
    "$ref": "#/components/schemas/AccountHoldingValidationRequest"
  }
}
```

**Response**: `BaseResponseListValidationResponseView`

#### Calculate Post Optimization Metrics
```
PUT /api/v2/fundamental/bulk/calcpostoptmetrics
```
**Purpose**: Calculate comprehensive metrics after portfolio optimization

**Tags**: `data-controller-opt-event`

### Fixed Income Analytics Endpoints

#### Yield to Maturity Comparison
```
GET /api/analytics/fi/charts/ytm-comparison/{accountId}
```
**Purpose**: Generate YTM comparison charts for fixed income portfolio

**Parameters**:
- `accountId` (path): Account identifier

#### Duration Risk Analysis
```
GET /api/analytics/fi/charts/duration-risk/{accountId}
```
**Purpose**: Analyze duration risk exposure in fixed income holdings

**Parameters**:
- `accountId` (path): Account identifier

### Account Management Endpoints

#### Create Account
```
POST /api/account/create
```
**Purpose**: Create a new investment account

**Request Body**: Account creation parameters
**Response**: Created account details

#### Get Account Holdings Trend
```
GET /api/account/holding/trend/{account_Id}/{fromDate}/{toDate}/{isRelative}
```
**Purpose**: Retrieve holding trends over specified time period

**Parameters**:
- `account_Id` (path): Account identifier
- `fromDate` (path): Start date for analysis
- `toDate` (path): End date for analysis  
- `isRelative` (path): Boolean for relative vs absolute values

### Security Data Endpoints

#### Get Security Returns
```
GET /api/security/returns/{securityId}/{fromDate}/{toDate}
```
**Purpose**: Retrieve historical returns for a specific security

**Parameters**:
- `securityId` (path): Security identifier
- `fromDate` (path): Start date for returns
- `toDate` (path): End date for returns

#### Get Security Financial Data
```
GET /api/security/financials/{securityId}
```
**Purpose**: Retrieve comprehensive financial data for a security

**Parameters**:
- `securityId` (path): Security identifier

## Common Schema Patterns

### Base Response Pattern
Most endpoints return responses following this structure:
```json
{
  "$ref": "#/components/schemas/BaseResponse[DataType]"
}
```

### Common Parameter Types
- **accountId**: Integer - Account identifier
- **securityId**: String - Security identifier  
- **asOfDate**: String - Date in ISO format
- **fromDate/toDate**: String - Date range parameters
- **userId**: Integer - User identifier
- **orgId**: Integer - Organization identifier

### Request Body Patterns
- **Bulk Operations**: Array of request objects
- **Update Operations**: Single object with updated fields
- **Template Operations**: Structured template data

## Best Practices

### API Usage Guidelines

1. **Date Handling**
   - Use ISO date format (YYYY-MM-DD)
   - Consider business day calculations for market data
   - Use appropriate date ranges for performance queries

2. **Bulk Operations**
   - Prefer bulk endpoints for multiple account operations
   - Use template-based uploads for large data sets
   - Validate data before bulk processing

3. **Error Handling**
   - Check for 402 Payment Required responses
   - Handle 404 responses for missing resources
   - Validate request parameters to avoid 400 errors

4. **Performance Optimization**
   - Use specific date ranges rather than open-ended queries
   - Leverage caching for reference data
   - Consider pagination for large result sets

5. **Security Considerations**
   - Validate account access permissions
   - Use appropriate authentication for sensitive operations
   - Audit trail for portfolio modifications

### Integration Patterns

1. **Portfolio Management Workflow**:
   ```
   Create Account → Upload Holdings → Define Optimization → Run Optimization → Validate Results → Accept/Reject
   ```

2. **Research Analysis Workflow**:
   ```
   Select Portfolio → Choose Analysis Type → Set Parameters → Generate Reports → Export Results
   ```

3. **Data Integration Workflow**:
   ```
   Connect Custodian → Validate Data → Import Positions → Reconcile Holdings → Update Accounts
   ```

## Support and Documentation

For additional support and detailed schema definitions, refer to:
- OpenAPI specification file: `EndPoints.txt`
- Sample documentation: `sample_api_documentation.md`
- Sample Linvest21 docs: `sample_linvest21_api_docs.md`

---

*This documentation covers 304 API endpoints across the Linvest21 Private Public Service API platform. For the most current information, always refer to the OpenAPI specification file.*