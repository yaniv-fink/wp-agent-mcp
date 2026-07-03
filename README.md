<!-- mcp-name: com.getwpagent/wordpress -->

# WP Agent — WordPress MCP Server

**WordPress publishing and management with Claude.** Connect your **self-hosted WordPress**
site to AI assistants (Claude, ChatGPT, Cursor, and any MCP client) and run your whole site
from chat: write and publish posts and pages, create AI featured and in-post images, manage
SEO, media, categories, tags and menus, moderate comments, and manage plugins, themes and site
settings — all on your own site, with your own credentials.

> **WP Agent** is a Model Context Protocol (MCP) server for WordPress. **69 tools.** Remote
> **Streamable HTTP** with **OAuth 2.0** — keyless, no API key to paste. A free account is
> created on first connect (25 posts/month, no card).

- 🌐 **Website:** https://www.getwpagent.com
- 📚 **Install & docs:** https://www.getwpagent.com/docs
- 🔌 **Endpoint:** `https://mcp.getwpagent.com/mcp`

---

## Connect

WP Agent is a **remote** MCP server — no install, no local process. Point your client at the
endpoint; OAuth runs automatically on first connect.

- **Endpoint:** `https://mcp.getwpagent.com/mcp` (Streamable HTTP)
- **Auth:** **OAuth 2.0** (Dynamic Client Registration + PKCE — keyless). An account is
  auto-created on first sign-in.

### Claude / generic MCP client (JSON)
```json
{
  "mcpServers": {
    "wp-agent": {
      "url": "https://mcp.getwpagent.com/mcp"
    }
  }
}
```

### Cursor
Add the `url` above in Cursor's **Settings → Tools & MCP**, or install from the listing on
`cursor.directory`.

<!--
MAINTAINER NOTE (cursor.directory): the GitHub auto-scanner reads mcp.json but STRIPS the
`mcpServers` wrapper, leaving only `{ "type": "http", "url": ... }` in the listing's Component
"Content". That drops the server name, so Cursor's install dialog shows "server" instead of
"wp-agent". After any re-scan, re-paste the FULL wrapper into the listing Content and keep the
key a lowercase slug (`wp-agent`, not "WP Agent" — it's a config identifier):
  { "mcpServers": { "wp-agent": { "url": "https://mcp.getwpagent.com/mcp" } } }
The connected display name comes from the server's own serverInfo ("WP Agent"), not this key.
-->


Full per-client instructions: **https://www.getwpagent.com/docs**

To connect a WordPress site, install the free **WP Agent Connector** plugin (or use an
application password on WordPress 5.6+); the assistant walks you through it on first use.

---

## What you can do (69 tools)

| Area | Example tools |
|---|---|
| **Content generation** | `create_post`, `replace_post_content`, `patch_post_content`, `generate_image` |
| **Posts & pages** | `list_posts`, `list_pages`, `publish_post`, `schedule_post`, `update_post_title`, `update_post_excerpt` |
| **SEO** | `get_post_seo_analysis`, `update_post_seo`, `get_posts_seo_overview` |
| **Images & media** | `generate_image`, `set_featured_image`, `add_media_from_url`, `search_stock_photos`, `update_media` |
| **Taxonomies & menus** | `create_category`, `create_tag`, `list_categories`, `create_menu`, `add_menu_item` |
| **Comments** | `list_comments`, `moderate_comment`, `delete_comment` |
| **Site management** | `get_site_settings`, `update_site_settings`, `install_plugin`, `activate_plugin`, `update_custom_css` |
| **Sites & usage** | `list_sites`, `connect_site`, `get_site_overview`, `get_usage` |

Read operations are read-only; destructive and publish operations require explicit user intent.

---

## How it works / data ownership

WP Agent does **not** wrap or resell a third-party API. **Each user connects their own
self-hosted WordPress site with their own credentials.** WP Agent provides the AI content and
site-management infrastructure. Credentials are encrypted at rest; OAuth tokens are scoped per
user. Image generation exists only to create supporting visuals (featured/hero/in-post images)
saved into your own WordPress media library — not as a standalone service.

## Support

- Docs: https://www.getwpagent.com/docs
- Email: hello@getwpagent.com
- Issues: use this repository's issue tracker.

## License

MIT — see [LICENSE](./LICENSE). (This repository hosts the MCP server's public metadata and
documentation; the server itself runs at `mcp.getwpagent.com`.)
