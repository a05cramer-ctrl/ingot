# ingot

paired with gold. the fees come back as metal.

A single-file static site. `index.html` has no dependencies and no build step —
open it directly, or serve the folder with any static host.

```
python -m http.server 8000
```

## Configuration

Everything configurable sits at the top of the `<script>` block in `index.html`.

```js
const CFG  = { coinApi:"", gldApi:"", feeWallet:"", explorer:"https://robinhoodchain.blockscout.com" };
const META = { ca:"", x:"", contact:"" };
```

| key | drives |
| --- | --- |
| `coinApi` | ingot market cap and holder count |
| `gldApi` | the $GLD price and 24h change |
| `feeWallet` | the activity ledger, read from Blockscout |
| `explorer` | explorer base URL used for every hash link |
| `ca` | the contract address in the header pill |
| `x` / `contact` | footer links |

## Data rules

Empty or unreachable endpoints render an em dash. The page never shows a
spinner and never invents, estimates, or carries over a value. If the fee
wallet has no matching transactions the ledger shows a single `no routings
yet` row rather than placeholder data.

While `gldApi` is empty the metal figures fall back to two public reference
feeds — gold spot from `api.gold-api.com` and PAX Gold from CoinGecko. In that
mode the cell labels change to `gold / oz` and `gold 1d` and the panel is
marked *reference only · not a $gld quote*, so no figure is presented as
something it is not. Setting `gldApi` replaces them.

Figures repoll every 60 seconds and pause while the tab is hidden.

## Files

| file | |
| --- | --- |
| `index.html` | the whole site, favicon inlined as base64 |
| `ingot.png` | source artwork, 1024×1024 |
| `icon180.png` | apple touch icon |
| `icon64.png` | favicon source, already inlined into `index.html` |

Not affiliated with State Street, SPDR, Robinhood or Pons.
