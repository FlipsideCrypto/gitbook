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
