# daterange-kit

Parse and validate human date ranges into typed `{ from, to }` objects:
`"last 7 days"`, `"2026-09-01..2026-09-26"`, `"this month"`.

Built during ETHGlobal Tokyo 2026 as the working project of the End Credits demo: the library is
written by a Claude Code session, and End Credits pays the open-source packages that session used.

## Demo fixtures

The dev dependencies under `@endcredits-demo/*` are End Credits demo fixtures, not real libraries.
They exist so one session can show every outcome End Credits handles, without ever showing a real
package as suspicious:

| Fixture | Shows |
|---|---|
| `moved-payout` | a payout address that changed: held until the owner signs |
| `left-padder-pro` | a sanctioned address: refused by Intercepta |
| `unclaimed-utils` | no wallet yet: reserved until the maintainer claims |
| `tip-jar` | paid through the maintainer's own x402 endpoint |
| `swapped-jar` | an endpoint that asks to be paid somewhere else: refused before signing |

## License

MIT
