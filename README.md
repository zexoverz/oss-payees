# oss-payees

Find where an open-source package wants to be paid, and check that the address is safe before
anyone pays it.

Four in ten of the top 1,000 npm packages ask for funding, but only about one in fifty publishes an
address a machine can pay, spread across different files and formats: Drips `FUNDING.json`,
`tea.yaml`, the npm `funding` field and `.github/FUNDING.yml`. A payout address read from a file that
anyone with write access can change is also an attack target. `oss-payees` resolves every source for
a package into one typed list and flags what should not be paid blindly.

## Planned API

```ts
import { resolvePayees } from "oss-payees";

const report = await resolvePayees("zod");
// report.payees:  [{ kind: "evm", address, network, source: "tea", url }, { kind: "sponsor", platform: "github", url }]
// report.warnings: [{ code: "conflict" | "lookalike" | "bad-checksum" | "zero-address" | "quorum" | "spoofed-repo", ... }]
```

- Sources: npm registry `repository` and `funding`, Drips `FUNDING.json` (every network key),
  `tea.yaml` (`codeOwners`, `quorum`), `.github/FUNDING.yml`.
- Checks: addresses that differ between sources, lookalike addresses (same first and last 4 hex),
  invalid checksums, zero addresses, `quorum > 1`, and whether the repository's own `package.json`
  publishes that package name (monorepo `directory` aware).
- An optional screening hook, so a payer can ask a risk API before paying.
- CLI: `npx oss-payees <package>`.

Built at ETHGlobal Tokyo 2026 as the working project of the End Credits demo: the library is written
in a Claude Code session, and End Credits pays the open-source packages that session used.

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
