# Linvest21 AI API Documentation

## Company Overview
Linvest21 AI provides intelligent investment solutions powered by advanced artificial intelligence and machine learning technologies.

## API Base URL
```
https://api.linvest21.ai/v1
```

## Authentication
All API endpoints require authentication using API keys:
```
X-API-Key: your-api-key-here
```

## Core Services

### 1. Portfolio Analysis Service

#### Analyze Portfolio Performance
**Endpoint:** `POST /portfolio/analyze`

**Description:** Analyzes portfolio performance and provides AI-driven insights.

**Request Body:**
```json
{
  "portfolio_id": "port-123456",
  "analysis_type": "comprehensive",
  "date_range": {
    "start": "2024-01-01",
    "end": "2024-09-01"
  },
  "metrics": ["returns", "risk", "sharpe_ratio", "volatility"]
}
```

**Response:**
```json
{
  "portfolio_id": "port-123456",
  "analysis": {
    "total_return": 12.5,
    "annualized_return": 15.2,
    "volatility": 8.3,
    "sharpe_ratio": 1.83,
    "max_drawdown": -5.2,
    "risk_score": "moderate"
  },
  "recommendations": [
    {
      "type": "rebalance",
      "priority": "high",
      "description": "Consider reducing exposure to tech sector by 5%"
    }
  ],
  "generated_at": "2024-09-02T10:30:00Z"
}
```

### 2. Market Intelligence Service

#### Get Market Predictions
**Endpoint:** `GET /market/predictions`

**Description:** Provides AI-generated market predictions for specified assets.

**Query Parameters:**
- `symbols`: Comma-separated list of asset symbols
- `horizon`: Prediction horizon (1d, 1w, 1m, 3m)
- `confidence_level`: Minimum confidence level (0-100)

**Request Example:**
```bash
curl -X GET "https://api.linvest21.ai/v1/market/predictions?symbols=AAPL,GOOGL,MSFT&horizon=1w&confidence_level=75" \
  -H "X-API-Key: your-api-key-here"
```

**Response:**
```json
{
  "predictions": [
    {
      "symbol": "AAPL",
      "current_price": 178.50,
      "predicted_price": 182.30,
      "predicted_change_percent": 2.13,
      "confidence": 82,
      "horizon": "1w",
      "signals": ["bullish", "momentum_positive"],
      "technical_indicators": {
        "rsi": 58,
        "macd": "bullish_crossover",
        "moving_average_200": 165.40
      }
    },
    {
      "symbol": "GOOGL",
      "current_price": 138.20,
      "predicted_price": 141.50,
      "predicted_change_percent": 2.39,
      "confidence": 78,
      "horizon": "1w",
      "signals": ["bullish", "volume_increasing"]
    }
  ],
  "market_sentiment": "cautiously_optimistic",
  "generated_at": "2024-09-02T10:30:00Z"
}
```

### 3. Risk Management Service

#### Calculate Risk Metrics
**Endpoint:** `POST /risk/calculate`

**Description:** Calculates comprehensive risk metrics for a given portfolio or position.

**Request Body:**
```json
{
  "portfolio_id": "port-123456",
  "risk_models": ["var", "cvar", "stress_test"],
  "confidence_levels": [95, 99],
  "time_horizon": 30
}
```

**Response:**
```json
{
  "portfolio_id": "port-123456",
  "risk_metrics": {
    "var_95": {
      "value": -25000,
      "percentage": -2.5
    },
    "var_99": {
      "value": -45000,
      "percentage": -4.5
    },
    "cvar_95": {
      "value": -32000,
      "percentage": -3.2
    },
    "stress_tests": [
      {
        "scenario": "market_crash_2008",
        "potential_loss": -180000,
        "probability": 0.05
      },
      {
        "scenario": "interest_rate_spike",
        "potential_loss": -75000,
        "probability": 0.15
      }
    ],
    "correlation_risk": "moderate",
    "concentration_risk": "low"
  },
  "recommendations": [
    "Consider hedging strategies for downside protection",
    "Diversify into non-correlated assets"
  ],
  "calculated_at": "2024-09-02T10:30:00Z"
}
```

### 4. Trading Signal Service

#### Get Trading Signals
**Endpoint:** `GET /signals/trading`

**Description:** Retrieves AI-generated trading signals for specified instruments.

**Query Parameters:**
- `symbols`: Asset symbols (required)
- `strategy`: Trading strategy type (momentum, mean_reversion, arbitrage)
- `timeframe`: Signal timeframe (intraday, daily, weekly)

**Response:**
```json
{
  "signals": [
    {
      "symbol": "BTC-USD",
      "action": "buy",
      "strength": 8.5,
      "entry_price": 58250,
      "target_price": 61000,
      "stop_loss": 56500,
      "timeframe": "daily",
      "strategy": "momentum",
      "confidence": 85,
      "risk_reward_ratio": 2.5,
      "technical_setup": "breakout_pattern"
    }
  ],
  "market_conditions": {
    "trend": "bullish",
    "volatility": "moderate",
    "volume": "increasing"
  },
  "updated_at": "2024-09-02T10:30:00Z"
}
```

### 5. Sentiment Analysis Service

#### Analyze Market Sentiment
**Endpoint:** `POST /sentiment/analyze`

**Description:** Analyzes market sentiment from various data sources.

**Request Body:**
```json
{
  "symbols": ["TSLA", "NVDA"],
  "sources": ["news", "social_media", "analyst_reports"],
  "time_period": "7d"
}
```

**Response:**
```json
{
  "sentiment_analysis": [
    {
      "symbol": "TSLA",
      "overall_sentiment": 0.65,
      "sentiment_label": "positive",
      "source_breakdown": {
        "news": 0.55,
        "social_media": 0.72,
        "analyst_reports": 0.68
      },
      "trending_topics": [
        "autonomous_driving",
        "quarterly_earnings",
        "china_expansion"
      ],
      "sentiment_change_24h": 0.08
    }
  ],
  "market_mood": "optimistic",
  "analyzed_at": "2024-09-02T10:30:00Z"
}
```

## WebSocket Endpoints

### Real-time Market Data
**Endpoint:** `wss://api.linvest21.ai/v1/stream/market`

**Subscribe Message:**
```json
{
  "action": "subscribe",
  "channels": ["prices", "trades", "orderbook"],
  "symbols": ["AAPL", "GOOGL"]
}
```

### Real-time Signals
**Endpoint:** `wss://api.linvest21.ai/v1/stream/signals`

**Subscribe Message:**
```json
{
  "action": "subscribe",
  "signal_types": ["entry", "exit", "alert"],
  "portfolio_id": "port-123456"
}
```

## Rate Limits

| Tier | Requests/Minute | Requests/Day | WebSocket Connections |
|------|----------------|--------------|----------------------|
| Basic | 60 | 10,000 | 2 |
| Professional | 300 | 50,000 | 10 |
| Enterprise | 1000 | Unlimited | 50 |

## Error Codes

| Code | Description |
|------|-------------|
| 400 | Bad Request - Invalid parameters |
| 401 | Unauthorized - Invalid API key |
| 403 | Forbidden - Insufficient permissions |
| 404 | Not Found - Resource doesn't exist |
| 429 | Too Many Requests - Rate limit exceeded |
| 500 | Internal Server Error |
| 503 | Service Unavailable - Temporary outage |

## SDKs and Libraries

- **Python**: `pip install linvest21-ai`
- **JavaScript/Node.js**: `npm install @linvest21/ai-sdk`
- **Java**: Maven dependency available
- **Go**: `go get github.com/linvest21-ai/go-sdk`

## Webhook Configuration

Configure webhooks to receive real-time notifications:

```json
{
  "url": "https://your-server.com/webhook",
  "events": ["signal_generated", "risk_alert", "portfolio_update"],
  "secret": "your-webhook-secret"
}
```

## Support and Resources

- **Documentation**: https://docs.linvest21.ai
- **API Status**: https://status.linvest21.ai
- **Support Email**: api-support@linvest21.ai
- **Developer Forum**: https://developers.linvest21.ai/forum
- **GitHub**: https://github.com/linvest21-ai

## Terms of Service

By using the Linvest21 AI API, you agree to our [Terms of Service](https://linvest21.ai/terms) and [Privacy Policy](https://linvest21.ai/privacy).

---

*Last Updated: September 2, 2024*
*API Version: 1.0.0*