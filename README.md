# AgentToll

AgentToll gives AI agents paid access to data and decision tools through MCP and HTTP. Every paid route publishes its price before purchase, settles in USDC on Base, and returns a receipt with the result.

The production service runs at [agenttoll.dev](https://agenttoll.dev). This repository contains the public integration materials. The production service code and operating data are private.

## Connect

- MCP endpoint: `https://agenttoll.dev/mcp`
- Tool directory: [agenttoll.dev/tools](https://agenttoll.dev/tools)
- Agent manifest: [agenttoll.dev/.well-known/agent.json](https://agenttoll.dev/.well-known/agent.json)
- x402 discovery: [agenttoll.dev/.well-known/x402](https://agenttoll.dev/.well-known/x402)
- OpenAPI spec: [agenttoll.dev/openapi.json](https://agenttoll.dev/openapi.json)
- Full agent context: [agenttoll.dev/llms-full.txt](https://agenttoll.dev/llms-full.txt)

Prices and tool availability can change. Read the live manifest or quote endpoint before approving a payment.

## Inspect a tool before paying

```bash
curl -s https://agenttoll.dev/.well-known/agent.json
curl -s 'https://agenttoll.dev/api/quote?tool=x402_rank_audit'
curl -s https://agenttoll.dev/paid/x402/rank-audit
```

A paid call should match the published route, method, network, asset, seller wallet, and maximum price. The buyer should approve the spend before its wallet signs anything.

See [examples/discover-and-quote.md](examples/discover-and-quote.md) for the buyer flow.

## Public integration materials

- [AgentToll Base MCP buyer skill](skills/agenttoll-base-mcp-buyer/SKILL.md)
- [Receipt schema](docs/receipt-v1.md)
- [Discovery and quote example](examples/discover-and-quote.md)
- [Security policy](SECURITY.md)

Install the buyer skill with:

```bash
npx skills add huwhitememes/agenttoll --skill agenttoll-base-mcp-buyer
```

## Service boundary

This repository documents how buyers discover, inspect, purchase, and verify AgentToll work products. It does not contain the production Worker, private operating data, feed assembly, metering controls, or institutional evidence archive.

## Support

Report public integration problems through [GitHub Issues](https://github.com/huwhitememes/agenttoll/issues). For account, institutional, or security matters, email [sales@agenttoll.dev](mailto:sales@agenttoll.dev).

## License

The documentation and examples in this repository are available under the [MIT License](LICENSE). Access to the hosted AgentToll service remains subject to its published terms, prices, and upstream data-source restrictions.
