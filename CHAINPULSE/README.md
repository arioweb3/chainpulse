# CHAINPULSE — On-Chain Intelligence Dashboard

**CHAINPULSE** is a responsive, browser-based dashboard for exploring public cryptocurrency market data and Bitcoin network activity. It is built with plain HTML, CSS, and JavaScript, with no build step and no wallet connection.

> **Live data only:** the interface does not substitute mock market values when an API fails. Unavailable data is clearly shown as unavailable.

## Features

- Market overview for Bitcoin (BTC), Ethereum (ETH), Solana (SOL), and Polygon ecosystem token (POL, queried through CoinGecko's `matic-network` ID).
- 24-hour price-change percentages and compact visual trend accents.
- Seven-day Bitcoin price history rendered with the Canvas API.
- Bitcoin tip height from mempool.space.
- Ethereum gas-price estimate from a public JSON-RPC endpoint.
- Bitcoin address lookup: estimated balance from confirmed chain stats and transaction counts.
- Bitcoin transaction lookup: confirmation status, block height when confirmed, fee, inputs, and outputs.
- API/source health states, last successful data refresh, activity events, loading states, and error handling.
- Responsive layout, reduced-motion support, and no wallet integration.

## Technology

- HTML5
- CSS3 (responsive CSS Grid, gradients, accessible focus states)
- Vanilla JavaScript (Fetch API, AbortController, DOM APIs)
- Canvas 2D for the historical price chart
- Public APIs: CoinGecko, mempool.space, Cloudflare Ethereum Gateway

## Run locally

No dependencies or build process are required.

1. Download or clone this repository.
2. Open `index.html` in a modern browser.

For a more representative local test, serve the folder with any static HTTP server. For example, with Python installed:

```bash
python -m http.server 8000
```

Then open `http://localhost:8000`. This is optional; there is no package installation step.

## Deploy to GitHub Pages

1. Create a **public** repository named `chainpulse` under the `arioweb3` GitHub account.
2. Upload `index.html`, `README.md`, `LICENSE`, and `.gitignore` to the repository root (the `assets/` directory is reserved for future media).
3. Open **Settings → Pages**.
4. Under **Build and deployment**, choose **Deploy from a branch**.
5. Select branch `main` and folder `/(root)`, then save.
6. Wait for the Pages deployment to finish. Open the URL shown in the Pages settings.

Expected URL (available only after the repository and Pages configuration are published correctly):  
`https://arioweb3.github.io/chainpulse/`

## API sources

- CoinGecko simple price endpoint: `https://api.coingecko.com/api/v3/simple/price`
- CoinGecko market chart endpoint: `https://api.coingecko.com/api/v3/coins/bitcoin/market_chart`
- mempool.space API: `https://mempool.space/api`
- Cloudflare Ethereum JSON-RPC endpoint: `https://cloudflare-eth.com/`

The browser calls these public endpoints directly. Endpoint policies, CORS behavior, rate limits, uptime, and response formats may change. Public/free endpoints do not provide an availability guarantee. CoinGecko may rate-limit unauthenticated requests, especially during high traffic. If one source is unavailable, its values remain blank/unavailable rather than being replaced with sample data.

## Security and privacy notes

- No API key, secret, private key, seed phrase, or wallet connection is required.
- Never enter a private key or recovery phrase. The explorer accepts only public Bitcoin addresses or transaction IDs.
- Explorer search queries are sent to mempool.space. Use of third-party endpoints is subject to their privacy policies and terms.
- Inputs are length-limited and validated before requests; user input is encoded in URL path segments and displayed as text rather than injected as HTML.
- This is a read-only dashboard. It does not create, sign, or broadcast transactions.
- The dashboard is a public-data viewer, not financial advice or a trading tool.

## Limitations

- Data can be delayed, temporarily unavailable, rate-limited, or inconsistent across providers.
- The Polygon ecosystem asset is requested using CoinGecko's `matic-network` identifier; provider naming/asset mappings can evolve.
- The Ethereum gas figure is the result of `eth_gasPrice` from a public RPC endpoint, not a guaranteed transaction fee or a full EIP-1559 fee recommendation.
- Bitcoin address balance is calculated from confirmed funded minus spent outputs; it does not represent every possible pending/mempool effect.
- The address explorer shows aggregate counts and recent transactions returned by the API, not a complete paginated transaction history.
- This static project has no backend, persistence, user accounts, or automated tests. Browser extensions, network filters, and API CORS/rate policies can affect behavior.

## Screenshots

Place screenshots in `assets/` and link them here, for example:

```markdown
![CHAINPULSE dashboard](assets/chainpulse-dashboard.png)
```

No screenshot is bundled by default.

## Project information

- **Project:** CHAINPULSE — On-Chain Intelligence Dashboard
- **Author:** Ario Web3
- **GitHub:** [arioweb3](https://github.com/arioweb3)
- **Contact:** ario.web3.dev@gmail.com

## License

Released under the MIT License. See [`LICENSE`](LICENSE).
