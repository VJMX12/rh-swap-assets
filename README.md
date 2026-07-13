# rh-swap — logo & token-info assets

Distinct, clearly-labeled **testnet** token branding. These are NOT real USDC/WBTC/DOGE
and deliberately don't use any real project's logo — each carries a `t` badge and a
TESTNET band so nobody can mistake it for a real asset.

## Files

| Token | SVG | PNG (512) | Address (testnet, chainId 46630) |
|-------|-----|-----------|----------------------------------|
| tUSDC | `logos/tusdc.svg` | `logos/tusdc.png` | `0x3d12ae41e065e6eb818a8f3a6cf04260118a05e2` |
| tWBTC | `logos/twbtc.svg` | `logos/twbtc.png` | `0xbc7b28a0608b7113f887bea13644237ca2214da2` |
| tDOGE | `logos/tdoge.svg` | `logos/tdoge.png` | `0x19bf8bade92965105264b728358ad3ecf03a4f8e` |

`*_preview.png` files are 256px previews; ignore them for hosting.

## Step 1 — host the images publicly

A logo lives off-chain; each platform fetches it from a URL. Easiest free option:
commit the PNGs to a public GitHub repo and use the **raw** URL, e.g.
`https://raw.githubusercontent.com/<you>/<repo>/main/tusdc.png`.
(IPFS via Pinata/web3.storage also works and is more permanent.)

Then edit `rh-swap.tokenlist.json` and replace each `REPLACE_WITH_YOUR_HOST` with the
real base URL.

## Step 2 — submit token info on Blockscout (per token)

Contracts are already verified, so each token has a page like:
`https://explorer.testnet.chain.robinhood.com/token/<address>`

On Blockscout, request/submit token info from the token page (look for
"Submit token info" / a "Token info" request form; some instances route this through
a support form or a `/token/<addr>/token-info` page). Provide:
- Project name: e.g. "rh-swap (testnet)"
- Logo URL: the hosted PNG from Step 1
- Website / docs (optional): your repo
- Description: make explicit it is a **testnet test token**, not a real asset.

Note: some Blockscout deployments gate token-info edits behind admin approval or a
verified-owner signature. If the form isn't available on this instance, the token list
(Step 3) still gives you logos in wallets and DEX UIs.

## Step 3 — publish the token list (for wallets / DEX frontends)

Host `rh-swap.tokenlist.json` at a public URL too. Wallets (MetaMask custom lists) and
DEX frontends can import it by URL and will then show your names + logos automatically.

## Step 4 — MetaMask quick check (per user, cosmetic)

Import a token by address in MetaMask; it will pick up name/symbol/decimals from the
contract. Logos appear once the token list is imported or the image is recognized.

---
Reminder: keep this branding testnet-only and test-labeled. For any mainnet version,
pair against **real** bridged USDC/USDG rather than a self-issued stablecoin.
