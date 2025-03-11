
# 3in1CryptoBot for Discord

A Discord bot that displays real-time cryptocurrency prices through bot nicknames and statuses. This bot can track multiple cryptocurrencies simultaneously by running separate bot instances.

![Bot Preview](https://via.placeholder.com/800x100?text=Bot+Preview+Image)

## Features

- **Real-time price tracking** for multiple cryptocurrencies
- **Visual indicators** (↑/↓) for price movements
- **Multiple currencies** support (USD and configurable secondary currency)
- **Discord integration** showing prices in bot nicknames and statuses
- **Command support** for fetching detailed price information
- **Rate limiting** to respect API quotas
- **Configurable** through environment variables or config file

## Requirements

- Python 3.8+
- Discord Bot tokens for each cryptocurrency you want to track
- CoinMarketCap API key (free tier works)

## Installation

1. Clone the repository:
   ```
   git clone https://github.com/yourusername/3in1CryptoBot.git
   cd 3in1CryptoBot
   ```

2. Install required packages:
   ```
   pip install -r requirements.txt
   ```

3. Create a `.env` file based on the template:
   ```
   cp .env.template .env
   ```

4. Edit the `.env` file with your API keys and Discord tokens

## Configuration

You can configure the bot through either:

1. Environment variables (in `.env` file)
2. A `config.json` file

The bot will check for both, with values in `config.json` taking precedence.

### Required Configuration

- `CMC_API_KEY`: Your CoinMarketCap API key
- `DISCORD_TOKEN_XXX`: Discord bot tokens for each cryptocurrency (replace XXX with the symbol, e.g., `DISCORD_TOKEN_BTC`)

### Optional Configuration

- `API_RATE_LIMIT`: How often to call the CoinMarketCap API (in seconds, default: 300)
- `DISPLAY_UPDATE_INTERVAL`: How often to update bot display (in seconds, default: 120)
- `TRACKED_CRYPTOS`: Comma-separated list of cryptocurrency symbols to track
- `EXCHANGE_API_URL`: URL for currency exchange rate API
- `EXCHANGE_UPDATE_INTERVAL`: How often to update exchange rates (in seconds, default: 43200 - 12 hours)
- `SECONDARY_CURRENCY`: Secondary currency code (default: AUD)

## Setting Up Discord Bots

For each cryptocurrency you want to track, you'll need to create a separate Discord bot:

1. Go to (https://discord.com/developers/applications)
2. Click "New Application" and give it a name (e.g., "Bitcoin Price Tracker")
3. Go to the "Bot" tab and click "Add Bot"
4. Under "Privileged Gateway Intents", enable "Message Content Intent"
5. Copy the token and add it to your `.env` file as `DISCORD_TOKEN_XXX`
6. Go to OAuth2 > URL Generator
7. Select the following scopes: `bot`
8. Select the following bot permissions: `Change Nickname`, `Send Messages`, `Read Messages/View Channels`
9. Copy the generated URL and open it in your browser to add the bot to your server
10. Repeat for each cryptocurrency

## Usage

To start the bot:

```
python 3in1CryptoBot.py
```

### Discord Commands

- `!btc` - Show Bitcoin price information
- `!sol` - Show Solana price information
- `!xrp` - Show XRP price information
- `!price` - Show price information for the specific bot you're interacting with

## License

MIT License - see LICENSE file for details.

## Acknowledgements

- [CoinMarketCap](https://coinmarketcap.com/) for the cryptocurrency price API
- [Discord.py](https://discordpy.readthedocs.io/) for the Discord bot framework
