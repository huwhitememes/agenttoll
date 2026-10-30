# Discover and quote an AgentToll tool

Use the free discovery surfaces before asking a wallet to approve payment.

## 1. Read the current manifest

```bash
curl -s https://agenttoll.dev/.well-known/agent.json
```

The manifest publishes the live tool catalog, payment network, asset, seller wallet, prices, and input schemas.

## 2. Find a matching route

```bash
curl -s 'https://agenttoll.dev/api/routes/find?q=x402%20listing%20audit'
```

## 3. Request a quote

```bash
curl -s 'https://agenttoll.dev/api/quote?tool=x402_rank_audit'
```

Confirm the tool name, route, method, price, network, asset, seller wallet, and input shape against the live manifest.

## 4. Inspect the unpaid route

```bash
curl -i https://agenttoll.dev/paid/x402/rank-audit
```

A paid route returns an HTTP `402` challenge until the buyer supplies a valid x402 payment payload.

## 5. Ask for approval

Tell the user what the call costs and what the result will do. Cap the wallet authorization at the quoted price. Do not substitute a different payment address, network, or asset.

## 6. Keep the result and receipt

A successful paid JSON response includes an `agenttoll_receipt` object. Save it with the result. If the buyer runtime exposes a settlement transaction hash, verify it at:

```text
https://agenttoll.dev/receipt/<transaction-hash>
```

Read [the receipt schema](../docs/receipt-v1.md) for field definitions and limitations.
