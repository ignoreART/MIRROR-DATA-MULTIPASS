# MIRROR Multipass Card

A futuristic, real-time dashboard displaying MIRROR token statistics on the Chia blockchain. Features a sleek multipass card design with live API integration, multiple fallback sources, and world clocks.

![MIRROR Token](https://icons.dexie.space/0957ed359f099d5846c2c74c42e7c2eb9608b58c32e320e144840e3efab0b747.webp)

## 🌐 Live Demo

Visit the live page: [https://ignoreart.github.io/MIRROR-DATA-MULTIPASS/](https://ignoreart.github.io/MIRROR-DATA-MULTIPASS/)

## ✨ Features

- **Real-time Token Data**: Live statistics from multiple API sources
- **Multi-Source Price Fetching**: Intelligent fallback chain for maximum reliability
- **Response Caching**: 5-minute cache to minimize API calls and avoid rate limits
- **Retry Logic**: Exponential backoff for failed requests
- **Visual Status Indicators**: Color-coded indicators showing current data source
- **World Clocks**: Real-time display of 11 major time zones
- **Auto-refresh**: Updates every 10 minutes
- **Responsive Design**: Sleek futuristic card design inspired by sci-fi aesthetics

## 📊 Data Sources

### XCH Price (USD)

The system uses a robust fallback chain for XCH price data:

1. **CoinGecko API** (Primary)
   - Endpoint: `https://api.coingecko.com/api/v3/simple/price?ids=chia&vs_currencies=usd`
   - Most reliable and widely-used crypto price API
   - Free tier with good rate limits

2. **SpaceScan API** (Secondary Fallback)
   - Endpoint: `https://api.spacescan.io/stats/price?currency=usd`
   - Chia-specific blockchain explorer API
   - Automatic fallback if CoinGecko fails

3. **Cached Price** (Tertiary Fallback)
   - Uses last successful price fetch
   - TTL: 5 minutes
   - Ensures display even if all APIs are temporarily down

### Token Data

**Dexie.space API** (Primary)
- Endpoint: `https://api.dexie.space/v1/cats`
- Provides: Holders, Total Supply, Circulating Supply, Price in XCH
- Enhanced with 3 retry attempts using exponential backoff
- Automatic fallback to manual data if API is unavailable

### Manual Data Mode

Optional fallback configuration for when APIs are unavailable:
```javascript
const MANUAL_DATA = {
  enabled: false,  // Set to true to use hardcoded values
  holders: 2117,
  totalSupply: 31000000,
  circulatingSupply: 29908241.29,
  priceXch: 0
};
```

## 🎨 Status Indicators

Visual indicators in the top-right corner show the current data source:

- 🟢 **Green** - Active API (CoinGecko/SpaceScan/Dexie)
- 🔵 **Cyan** - Using cached data
- 🔵 **Blue** - Manual/hardcoded data mode
- 🟠 **Orange** - Loading/attempting connection
- 🔴 **Red** - Error state

## 🚀 Quick Start

### View Locally

1. Clone the repository:
```bash
git clone https://github.com/ignoreART/MIRROR-DATA-MULTIPASS.git
cd MIRROR-DATA-MULTIPASS
```

2. Open in browser:
```bash
# Using Python
python3 -m http.server 8000

# Using Node.js
npx http-server

# Or simply open index.html in your browser
```

3. Visit `http://localhost:8000` in your browser

### GitHub Pages Setup

This repository is configured for GitHub Pages:

1. Go to **Settings → Pages**
2. Under **Source**, select **main** branch
3. Click **Save**
4. Your page will be live at: `https://ignoreart.github.io/MIRROR-DATA-MULTIPASS/`

## 🔧 Configuration

### Enable Manual Data Mode

To use hardcoded values instead of live APIs (useful for testing or when APIs are down):

1. Open `index.html`
2. Find the `MANUAL_DATA` object (around line 274)
3. Set `enabled: true`
4. Update the hardcoded values as needed

### Adjust Cache TTL

To change how long prices are cached:

1. Open `index.html`
2. Find `priceCache` object (around line 438)
3. Modify `ttl: 5 * 60 * 1000` (currently 5 minutes in milliseconds)

### Change Refresh Interval

To adjust auto-refresh frequency:

1. Open `index.html`
2. Find `UPDATE_INTERVAL` constant (around line 271)
3. Modify `10 * 60 * 1000` (currently 10 minutes in milliseconds)

## 📱 Token Information

- **Token Name**: MIRROR
- **Token ID**: `0957ed359f099d5846c2c74c42e7c2eb9608b58c32e320e144840e3efab0b747`
- **Blockchain**: Chia (XCH)
- **Launch Date**: March 12, 2025 at 11:19:31 UTC
- **Total Supply**: 31,000,000 MIRROR
- **Circulating Supply**: ~29,908,241 MIRROR
- **Burned**: ~1,091,758 MIRROR

## 🔍 API Error Handling

The application includes comprehensive error handling:

- **Automatic Retries**: Up to 3 attempts with exponential backoff (2s, 4s, 8s)
- **Graceful Degradation**: Falls back to alternative sources on failure
- **User-Friendly Messages**: Clear status indicators and console logging
- **Cache Fallback**: Uses stale cache if all APIs fail
- **Manual Override**: Optional hardcoded values as last resort

## 🌍 World Clocks

Real-time display of current time in 11 major cities:
- UTC
- New York
- Chicago
- Los Angeles
- London
- Paris
- Dubai
- Mumbai
- Beijing
- Tokyo
- Sydney

## 📈 Statistics Displayed

- **Launch Date**: Token deployment date and time (UTC)
- **Days Deployed**: Calculated from launch date
- **Holders**: Total number of token holders
- **Total Supply**: Maximum token supply
- **Circulating Supply**: Tokens currently in circulation
- **Burned**: Tokens removed from circulation
- **Price (XCH)**: Current price in XCH with USD equivalent
- **Current Date**: Today's date with live world clocks

## 🛠️ Technical Details

- **Frontend**: Pure HTML5, CSS3, JavaScript (ES6+)
- **No Dependencies**: No external libraries or frameworks required
- **CORS-Ready**: Designed to work from any origin
- **Mobile Responsive**: Optimized for all screen sizes
- **Caching Strategy**: Intelligent client-side caching with TTL
- **API Rate Limiting**: Built-in protection against rate limits

## 🎯 Browser Support

- Chrome/Edge (latest)
- Firefox (latest)
- Safari (latest)
- Opera (latest)

## 📝 Console Logging

The application provides detailed console logs for debugging:

```
🚀 MIRROR Multipass v3.0
📊 Token ID: 0957ed...
🔄 Fetching XCH price from CoinGecko...
✅ CoinGecko XCH price: 21.50
📡 Trying Dexie.space API...
✅ Found MIRROR on Dexie: {...}
✅ Success via Dexie!
```

Open your browser's Developer Console (F12) to view real-time API status.

## 🤝 Contributing

Contributions are welcome! To contribute:

1. Fork the repository
2. Create a feature branch (`git checkout -b feature/AmazingFeature`)
3. Commit your changes (`git commit -m 'Add some AmazingFeature'`)
4. Push to the branch (`git push origin feature/AmazingFeature`)
5. Open a Pull Request

## 📄 License

This project is open source and available under the MIT License.

## 🔗 Links

- **Dexie.space**: [MIRROR Token](https://dexie.space/offers/0957ed359f099d5846c2c74c42e7c2eb9608b58c32e320e144840e3efab0b747)
- **SpaceScan**: [Chia Explorer](https://spacescan.io)
- **CoinGecko**: [Chia Price](https://www.coingecko.com/en/coins/chia)

## 📧 Contact

For issues, questions, or suggestions, please open an issue on GitHub.

---

**Built with ❤️ for the Chia community**
