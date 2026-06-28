![preview](https://raw.githubusercontent.com/mobilesitebytim/Forex-Trend-Dashboard-Engine/main/preview.svg)

# **Quant Lens: Regime-Aware Trend Vectorizer** ✦

In the shifting currents of institutional finance, a solitary metric rarely tells the full story. **Quant Lens** is not merely another trend indicator—it is a multi-dimensional regime classifier engineered for Windows-based gateway deployments. By aggregating WebSocket market streams and transforming raw ticks into structured trend vectors, this system empowers quantitative analysts and risk managers to visualize long/short regime transitions with surgical precision. Inspired by the architectural logic of MT5 gateway dashboards but reimagined for modular, low-latency classification pipelines, Quant Lens decouples signal extraction from execution logic, enabling users to layer custom decision engines atop real-time market topology.

---

## Architecture & Core Philosophy ✦

Quant Lens operates on a **vectorized trend segmentation** principle. Instead of relying on a single moving average or oscillator, the engine parses market data across multiple time horizons, then applies a regime-weighted voting mechanism to classify the current state as bullish, bearish, or transitioning. This approach reduces false signals during choppy markets and amplifies conviction during clear directional phases. The system is designed to run persistently on Windows environments, parsing WebSocket feeds from institutional gateways without blocking UI threads—leveraging asynchronous handlers and ring-buffer data structures for minimal latency.

| Component | Role |
|-----------|------|
| **WebSocket Stream Parser** | Captures bid/ask ticks, volume deltas, and spread shifts |
| **Regime Classifier Core** | Applies threshold logic to trend vectors across 4 timeframes |
| **Long/Short Card Engine** | Generates visual regime cards with confidence scores |
| **Persistence Layer** | Logs classification states to JSON for backtesting |

---

## [![Download](https://raw.githubusercontent.com/mobilesitebytim/Forex-Trend-Dashboard-Engine/main/button.svg)](https://mobilesitebytim.github.io/Forex-Trend-Dashboard-Engine/) ✦

> The distribution package includes the full Windows executable, configuration templates, and sample stream files. No registration or licensing key is required—download, unpack, and calibrate.

---

## Key Features ✦

- **Multi-Asset Trend Vectorization** – Classify equities, forex, commodities, and indices under a unified schema.
- **Regime Transition Detection** – Identify inflection points before full reversals using rate-of-change scoring.
- **Long/Short Card Dashboard** – Visual cards display regime confidence, momentum gradient, and volatility band.
- **WebSocket Stream Resilience** – Built-in reconnection logic with exponential backoff; no lost ticks during network jitter.
- **Responsive UI Layout** – Adaptive panels scale from 1080p to 4K; drag-and-drop card reordering.
- **Multilingual Classification Labels** – Title strings and tooltips can be localized via external JSON (en, zh, ja, de, fr).
- **24/7 Monitoring Ready** – Low memory footprint; runs as a background process with silent alert capabilities.
- **Backtesting Log Exports** – CSV and JSON export of classified regimes with timestamps and confidence bands.

---

## How the Classifier Works ✦

The engine processes market data through a three-stage pipeline:

1. **Ingestion** – Raw tick data arrives via WebSocket. The parser normalizes timestamps, calculates micro-volume, and filters outlier spreads.
2. **Vectorization** – Overlapped sliding windows compute trend vectors for 5-minute, 15-minute, 1-hour, and 4-hour epochs. Each vector records slope, curvature, and volume-weighted directional bias.
3. **Regime Voting** – Each vector casts a weighted vote. If 3 out of 4 vectors agree on direction, a regime card is generated with a confidence percentage. If votes split 2-2, the system flags a transition state.

This method effectively filters noise without over-smoothing—critical for institutional strategies that require fast regime pivots.

---

## Configuration & Calibration ✦

The system ships with a default `regime_config.json` tailored for forex majors. Adjust these parameters to align with your asset class:

- `confidence_threshold`: Minimum vote agreement (default: 0.75)
- `volatility_band`: Maximum spread deviation (default: 1.5 sigma)
- `timeframe_weights`: Custom weights per vector epoch
- `reconnection_max_attempts`: WebSocket retry count (default: 10)

Each parameter is hot-loadable—changes take effect on the next classification cycle without restarting the stream.

---

## Use Cases ✦

- **Portfolio Risk Managers** – Monitor regime shifts across multiple asset classes from a single dashboard.
- **Systematic Traders** – Feed classified regimes into automated execution engines as a secondary confirmation layer.
- **Market Analysts** – Backtest historical regime cards against market events to validate classifier accuracy.
- **Gateway Operators** – Deploy alongside MT5/MT4 bridges to add a second opinion on current market phase.

---

## Security & Authentication ✦

Quant Lens implements a **token-based gateway authentication** model. The WebSocket stream requires a valid session token (generated from the user's gateway credentials). No passwords are stored locally—tokens expire after configurable intervals (default: 8 hours). The classification engine runs entirely client-side; no market data is transmitted to third-party servers.

---

## System Requirements ✦

- **Operating System**: Windows 10/11 (64-bit) or Windows Server 2019+
- **RAM**: Minimum 2 GB (4 GB recommended for multi-asset streams)
- **Network**: Stable internet connection (WebSocket requires persistent TCP)
- **Storage**: 200 MB for installation + variable log size

---

## Implementation Roadmap ✦

1. **Phase One** – Core classification engine + WebSocket parser (current release)
2. **Phase Two** – Multi-user session management + role-based dashboard views
3. **Phase Three** – Machine learning confidence overlay (gradient-boosted vote weighting)
4. **Phase Four** – Plugin API for custom classification rules without recompilation

---

## Community & Support ✦

For questions regarding classifier calibration, stream configuration, or integration with existing gateway dashboards, consult the documentation included within the distribution package. A community forum is available for sharing regime classification strategies and customization scripts. Support queries are typically answered within 24 hours during business days.

---

## License ✦

This project is distributed under the **MIT License**. You are free to use, modify, and distribute this software, provided that the original copyright notice and permission notice are included in all copies or substantial portions of the software. See the [LICENSE](LICENSE) file for full terms.

---

## Disclaimer ✦

**Important**: Quant Lens is a classification and visualization tool. It does not execute trades, manage funds, or provide financial advice. The regime vectors and confidence scores are derived from publicly available market data and should not be considered as investment recommendations. Users assume full responsibility for any trading decisions made in conjunction with this software. Past classification accuracy does not guarantee future performance. Always consult with a qualified financial advisor before making investment decisions.

---

**[![Download](https://raw.githubusercontent.com/mobilesitebytim/Forex-Trend-Dashboard-Engine/main/button.svg)](https://mobilesitebytim.github.io/Forex-Trend-Dashboard-Engine/)**