# 🪿 Goose Flipside MCP Getting Started Guide

{% hint style="success" %}
Current supported models:  `claude-sonnet-4` • `gemini/gemini-2.5-pro` • `gemini-2.5-flash-preview-04-17`&#x20;

For this example we'll be using Anthropic's `claude-sonnet-4` model.&#x20;
{% endhint %}

#### Requirements before you get started

1. Either an Anthropic or Google Gemini API Key
2. A unique Flipside MCP URL and API Key.
   1. Don't have one? [Request one here.](https://flipsidecrypto.xyz/fc/flipside-mcp-interest)

## Here's how to add the Flipside MCP with Goose

### ![:inbox\_tray:](https://a.slack-edge.com/production-standard-emoji-assets/14.0/apple-medium/1f4e5.png) Download & Install Goose Desktop

1. Go to [https://block.github.io/goose/docs/quickstart](https://block.github.io/goose/docs/quickstart) and download Goose Desktop for your OS
2. Install and launch the application

### ![:gear:](https://a.slack-edge.com/production-standard-emoji-assets/14.0/apple-medium/2699-fe0f.png) Configure LLM Provider

1.  Open Goose and you'll be prompted to choose and configure a provider. \
    &#x20;

    <figure><img src="../../.gitbook/assets/Screenshot 2025-06-23 at 2.44.02 PM.png" alt=""><figcaption></figcaption></figure>
2. Click on the provider you want to use. We'll be using Anthropic for this example.
3. Paste in your API key (this is where you will need to get an API key from one of the supported LLM providers).

<figure><img src="../../.gitbook/assets/Screenshot 2025-06-23 at 2.41.37 PM.png" alt=""><figcaption></figcaption></figure>

### ![:robot\_face:](https://a.slack-edge.com/production-standard-emoji-assets/14.0/apple-medium/1f916.png) Add the Flipside MCP

1. Once the model is configured navigate to the Goose chat page.&#x20;
2. Click the Gear Icon in the top right corner and select 'Advanced Settings'
3. Under 'Extenstions' click 'Add custom extension'
   1. Extension name: `flipsidemcp` (can be whatever you want but no spaces)
   2. Type: `SSE`
   3. Endpoint: _Your unique URL_
   4.  Timeout: `300000` \


       <figure><img src="../../.gitbook/assets/Screenshot 2025-06-23 at 3.07.15 PM.png" alt=""><figcaption></figcaption></figure>
4. Click 'Add Extension'
5. Click 'Back' and start playing around!&#x20;

Need inspiration on what to ask? See the[.](./ "mention") page for more details.
