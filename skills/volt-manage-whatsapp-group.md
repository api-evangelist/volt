---
name: Create and manage a WhatsApp group via Volt
description: Create a WhatsApp group, add participants, and manage admins through the Volt MCP server.
api: mcp/volt-mcp.yml
transport: https://mcp.voltchat.com/mcp
operations: [create-group, add-participants-to-group, promote-participants-to-admins, remove-participants-from-group, demote-participants-from-admins, search-contact]
---

# Create and manage a WhatsApp group via Volt

Group administration flows over the Volt MCP server at
`https://mcp.voltchat.com/mcp`. Requires the Volt desktop app with Volt Cloud
connected and an authenticated MCP session.

## Steps
1. Resolve each intended participant with `search-contact`.
2. Call `create-group` with the group name and initial participants.
3. Add more members later with `add-participants-to-group`.
4. Grant admin rights with `promote-participants-to-admins`; revoke with
   `demote-participants-from-admins`.
5. Remove members with `remove-participants-from-group`.

## Rules
- Confirm the participant list with the user before creating or modifying a group;
  adds/removes are visible to all members and cannot be silently undone.
- Resolve every participant via `search-contact` — never invent identities.
