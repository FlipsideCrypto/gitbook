# 🤖 Anthropic Flipside MCP Getting Started Guide

{% hint style="success" %}
Current supported models:  `claude-sonnet-4` • `gemini/gemini-2.5-pro` • `gemini-2.5-flash-preview-04-17` \
\
For this example we'll be using Anthropic's `claude-sonnet-4` model.&#x20;
{% endhint %}

#### Requirements before you get started

1. A Claude Pro account
2. A unique Flipside MCP API Key.
   1. Don't have one? [Request one here.](https://flipsidecrypto.xyz/fc/flipside-mcp-interest)

### Quick Setup Instructions

1. Open Claude Settings
   1. Navigate to Settings in your Claude interface
   2. Click on "Integrations" in the left sidebar
2. Access Integration Settings
   1. In the Integrations section, look for the "Add integration" button
   2. Click the "+" Add integration button
3. Add Flipside Integration
   1. Enter "Flipside" as the integration name
   2. Enter the server URL: `https://mcp.flipsidecrypto.xyz/beta/sse?apiKey=[YOUR-API-KEY]`
   3. Click "Update" to save the integration
4. Enable the Integration
   1. Once added, make sure the Flipside integration shows as "Enabled"
   2. The integration should now appear in your list of available integrations

Step 1-2: Settings and Integrations Page&#x20;

<figure><img src="https://lh7-rt.googleusercontent.com/docsz/AD_4nXf1GHAIhBI55hNkR5Ma4FD2ZGUPoCKEMhm1jQi7EeQVHGsxxUO-RrwkghOlFKf3Yxa5dfMFXCa5rPKDR3N5s9TnhHaBoFQbIFhMxNxNwR9wgHlN6wznSHIjxP5SjaBzfBoWxZrrfg?key=8-5ED9M-dSUtvcBHLz0_9A" alt=""><figcaption></figcaption></figure>

Step 3: Adding the Integration&#x20;

<figure><img src="https://lh7-rt.googleusercontent.com/docsz/AD_4nXcTyscF7pGtdpRpCHBHWjKEdhHYHav8IshOVw-BFzlP6j9Ey4pyeHjF9bgVhpXIMwoh5smfUhjC86sDnT2Npe-SX39NGAnO6KzsQHR738zXTqqOrJO64imRHyXT5luWoH9hi6UCVQ?key=8-5ED9M-dSUtvcBHLz0_9A" alt=""><figcaption></figcaption></figure>

Your Flipside MCP server is now ready to use! You can start asking questions about blockchain data and analytics.

Example Analysis: “I want a report on Aptos for the month of may”

<figure><img src="https://lh7-rt.googleusercontent.com/docsz/AD_4nXeX83OsdCIiTjuCmxgZeFAYbvbhExIs2WU2l-tfUHITUfWzCtHiY_l_7Akk9MZqRhprjQK6tmLickwMB7TZ8cld5SRVBMvGWKQtXhrKzawxmYYYPfRQhO2GdMtwctvArqWpnyfK?key=8-5ED9M-dSUtvcBHLz0_9A" alt=""><figcaption></figcaption></figure>

\


## Here's how to add the Flipside MCP to your Pro Claude Account

#### **Claude Enterprise and Team (Owners and Primary Owners)**

_Note:_ While anyone can build and host integrations using remote MCP, only Primary Owners or Owners can enable it on Claude for Work plans (Team and Enterprise). Once an integration has been configured on a Team or Enterprise account, users individually authenticate into the integration. This ensures that Claude can only access tools and data that the individual user has access to.

1. Navigate to[ Settings > Integrations](https://claude.ai/settings/integrations)
2. Toggle to “Organization integrations” at the top of the page
3. Locate the “Integrations” section
4. Click “Add custom integration” at the bottom of the section
5. Add your integration’s remote MCP server URL
   1. &#x20;`https://mcp.flipsidecrypto.xyz/beta/sse?apiKey=[YOUR-API-KEY]`
6. Finish configuring your integration by clicking “Add”

#### **Claude Pro/Max**

1. Navigate to [Settings > Integrations](https://claude.ai/settings/integrations)
2. Locate the “Integrations” section
3. Click “Add custom integration” at the bottom of the section
4. Add your integration’s remote MCP server URL
   1. &#x20;`https://mcp.flipsidecrypto.xyz/beta/sse?apiKey=[YOUR-API-KEY]`
5. Finish configuring your integration by clicking “Add”

That's it! Need inspiration on what to ask? See the[.](./ "mention") page for more details.
