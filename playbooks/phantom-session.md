# Phantom agent-session playbook (never self-ban)

## Reality
Agent wallet via Phantom Connect is OAuth/KMS on the box. Sessions expire and Cloudflare 1015 on `auth.phantom.app` can block refresh for minutes–hours. There is no permanent “always connected” mode like a personal Phantom extension.

## Desk rules (lock)
1. **One signer:** only Crypto Trader (or CoS if Trader blocked) calls Phantom execute. Market Watch / Scout / Risk never call `login` / `buy` / `wallet_balances` in a storm.
2. **No prophylactic login.** Call `login` only after a hard AUTH_EXPIRED / disconnected status — not before every quote.
3. **After 1015:** zero auth calls for ≥10–15 minutes. One retry, then double backoff (15→30→60). Never multi-agent parallel login.
4. **Do not RestartMcpServers** mid-exit unless the connector is hung; restart itself can force re-auth.
5. **Pre-trade health:** one `wallet_status` only. If connected, go straight to quote/execute. If 1015, abort new entries; protect open sleeves with earlier bank bias.
6. **Flaky-session day:** prefer banking +2/+4 sooner; start overnight flatten earlier (e.g. 8 PM) so we are not dependent on auth at 9 PM.
7. **User:** when a real login card appears, approve once. Do not open parallel Phantom Connect tabs.

## Incident 2026-09-23
FWOG +4% bank blocked ~7–8pm ET by Cloudflare 1015 after concurrent stop-sell retries. SOL stayed ~0.7177 (still open).
