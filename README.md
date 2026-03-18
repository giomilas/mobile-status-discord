# Discord Mobile Status

This simple Python script allows your `discord.py` bot to appear online with the mobile phone status icon.

## How It Works

The script works by "monkey-patching" the `identify` method of the `DiscordWebSocket` class from `discord.py`. It overrides the default browser and device properties sent during the websocket connection handshake, replacing them with `'Discord Android'` to mimic a mobile client.

## Requirements

*   Python 3.6+
*   [discord.py](https://pypi.org/project/discord.py/) library

## Installation & Usage

1.  **Add the file to your project**
    
    Download the `status.py` file and place it in the same directory as your main bot file.

2.  **Install dependencies**
    
    Make sure you have `discord.py` installed. If not, run the following command:
    
    ```sh
    pip install discord.py
    ```

3.  **Modify your bot's main file**
    
    In your main bot script, import the `status` function and call it *before* you initialize and run your bot client.

## Example

Here is a minimal example of how to integrate the script into your bot.

`main.py`
```python
import discord
from status import status # Import the function

# Call the function to apply the mobile status patch
status()

# Replace with your own intents if needed
intents = discord.Intents.default() 

client = discord.Client(intents=intents)

@client.event
async def on_ready():
    print(f'Logged in as {client.user}')
    print('Bot should now appear with a mobile status icon.')

# Replace 'YOUR_BOT_TOKEN' with your actual bot token
client.run('YOUR_BOT_TOKEN')
