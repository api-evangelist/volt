---
name: Send a WhatsApp message via Volt
description: Find a contact and send them a WhatsApp message through the Volt MCP server.
api: mcp/volt-mcp.yml
transport: https://mcp.voltchat.com/mcp
operations: [search-contact, list-chats, send-message, set-chat-read-state]
---

# Send a WhatsApp message via Volt

Volt exposes WhatsApp to agents through an authenticated remote MCP server at
`https://mcp.voltchat.com/mcp`. The user must have the Volt desktop app installed
with Volt Cloud connected. Message content stays under WhatsApp end-to-end
encryption; Volt does not relay content through its own servers.

## Prerequisites
- Connect the Volt MCP server (OAuth custom connector in Claude/ChatGPT, or an
  `Authorization: Bearer YOUR_VOLT_API_KEY` header via `mcp-remote`).

## Steps
1. Resolve the recipient with the `search-contact` tool (name or number). If the
   user gave a chat rather than a contact, use `list-chats` to find the chat id.
2. Confirm the exact recipient with the user before sending — messages are real
   and irreversible.
3. Call `send-message` with the resolved chat/contact and the message body.
4. Optionally call `set-chat-read-state` to mark the conversation read/unread.

## Rules
- Never send to a recipient you have not confirmed; there is no undo.
- Do not fabricate contact ids — always resolve via `search-contact`/`list-chats`.
