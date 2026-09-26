# daterange-kit

Parse and validate human date ranges into typed `{ from, to }` objects:
`"last 7 days"`, `"2026-09-01..2026-09-26"`, `"this month"`.

Built during ETHGlobal Tokyo 2026 as the working project of the End Credits demo: the library is
written by a Claude Code session, and End Credits pays the open-source packages that session used.

## Demo fixtures

The dev dependencies `@endcredits-demo/moved-payout`, `@endcredits-demo/left-padder-pro` and
`@endcredits-demo/unclaimed-utils` are End Credits demo fixtures, not real libraries. They exist so
the demo can show a held payment (a payout address that changed), a refused payment (a sanctioned
address) and a reserved payment (no wallet yet). No real package is ever shown as suspicious.

## License

MIT
