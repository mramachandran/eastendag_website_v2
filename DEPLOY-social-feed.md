# Rename to ".env" locally, OR paste these as Environment Variables in Vercel/Netlify.
# NEVER commit real values to git. These stay server-side only.

# Long-lived Facebook Page token (or a System User token — preferred, never expires)
META_PAGE_TOKEN=paste-your-long-lived-token-here

# Facebook Page ID for facebook.com/eastendag (from GET /me/accounts)
FB_PAGE_ID=paste-your-page-id-here

# Instagram Business account ID (from GET /{PAGE_ID}?fields=instagram_business_account)
# Leave blank to show Facebook only.
IG_USER_ID=paste-your-instagram-id-here

# Graph API version — use the current one shown in your Meta App Dashboard
GRAPH_VERSION=v21.0
