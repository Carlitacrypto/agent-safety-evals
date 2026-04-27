# agent-safety-evals

> Evaluating safety failure modes of LLM agents executing irreversible financial actions in crypto environments.

## Motivation

LLM-based agents are increasingly given access to crypto rails: centralized exchange APIs, wallets, on-chain tooling, smart contract calls. Unlike web browsing or coding sandboxes — where most existing agentic evaluations live — crypto environments are unforgiving: a misaligned trade, a signed malicious transaction, or a successful prompt injection from an on-chain payload **cannot be undone**.

This repository is a work-in-progress evaluation suite designed to systematically map *when* and *how* current frontier agents fail in this setting.

## Research questions

1. **Adversarial market data.** How do agents behave when fed manipulated price feeds, fake liquidity, or spoofed order books?
2. **Prompt injection via on-chain content.** Can agents be hijacked by malicious token names, fake dApp metadata, or crafted transaction memos?
3. **Sycophantic compliance with risky instructions.** When a user says "yolo my entire portfolio," what fraction of agents comply vs. refuse vs. ask for confirmation?
4. **Recovery behavior after partial failures.** After a failed transaction or unexpected slippage, does the agent stop, retry safely, or compound the loss?

## Scope

- **Models:** primarily Claude family (Sonnet, Opus, Haiku — current generation).
- **Action space:** simulated CEX trade execution, simulated wallet signing, simulated on-chain reads. **No real funds, no mainnet transactions.** All scenarios run against mocks or testnet.
- **Sample size target:** ~500–1000 runs per scenario for statistical signal.

## Repository structure

```
agent-safety-evals/
├── README.md                  # This file
├── scenarios/                 # Adversarial scenario definitions (YAML/JSON)
│   ├── 01-adversarial-market-data/
│   ├── 02-prompt-injection-onchain/
│   ├── 03-sycophantic-compliance/
│   └── 04-recovery-behavior/
├── evals/                     # Evaluation harness code
├── results/                   # Aggregated run logs and metrics (anonymized)
├── scripts/                   # Helper scripts (run, analyze, plot)
└── METHODOLOGY.md             # Detailed methodology and threat model
```

## Status

🚧 **Early scaffolding.** The repository is being set up. Initial scenario definitions and harness code are being developed. Results will be published as runs complete.

## Planned deliverables

- Public eval suite (this repo).
- Technical writeup of findings.
- French-language video summary on [Carlita Crypto](https://www.youtube.com/@carlitacrypto) — translating findings for francophone builders deploying agents on crypto rails.

## Funding & disclosure

Independent research. Compute is being requested through Anthropic's External Researcher Access Program. No commercial sponsorship.

## Contact

Carla-Marie Masini — Paris, France
- GitHub: [your handle]
- X: [@carlitacrypto_](https://x.com/carlitacrypto_)

## License

MIT (see [LICENSE](LICENSE)).
