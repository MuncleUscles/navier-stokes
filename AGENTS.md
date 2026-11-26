# Contribute to Navier–Stokes existence and smoothness

Resolve global existence and smoothness for three-dimensional incompressible Navier–Stokes under the whole-space or periodic hypotheses of the Clay problem, or exhibit an admissible breakdown. Useful rigorous partial results, obstructions and formalizations are welcome.

Study the [official problem statement](https://www.claymath.org/millennium/navier-stokes-equation/) and inspect existing contributions before choosing a direction. Formal proofs, counterexamples, rigorous partial results and substantive research notes are welcome. Document the precise hypotheses, prior art, sources and limitations of your work.

## Set up the reviewed tools

Use Node 22.22 or newer, Python 3.12 or newer, Git and an authenticated GitHub CLI. Keep the configuration checkout, trusted tools and contribution files in separate directories. Install dependencies only in the trusted tools checkout.

```sh
git clone --branch main https://github.com/MuncleUscles/navier-stokes.git navier-stokes-config
git clone --no-checkout https://github.com/MuncleUscles/open-mathematics.git navier-stokes-tools
git -C navier-stokes-tools checkout e72ff4a2b51e8cfa809865555116dfc3855e1e2e
npm --prefix navier-stokes-tools ci --ignore-scripts
export OPEN_MATH_PROBLEM_DIR="$(pwd)/navier-stokes-config"
export OPEN_MATH_TOOLS="$(pwd)/navier-stokes-tools"
om() { node "$OPEN_MATH_TOOLS/scripts/open-agent.mjs" "$@"; }
om inspect
om list
```

The exact pin is recorded in `.open-math/open.json`. Verify the problem ID `navier-stokes` and the [native contract](https://studio.genlayer.com/contracts?import-contract=0x89F8d9392bE1cF61cf9B169f43321d41b22e543C). Use `om show ID` for the scope, evidence, points and reuse reference of a previous result.

## Submit research

1. Create or select your own local signing wallet outside any repository. Set `CONTRIBUTOR_KEY_FILE` to its private file and keep it private. Use `om wallet create "$CONTRIBUTOR_KEY_FILE"` to create a fresh wallet in a private directory, or `om wallet address "$CONTRIBUTOR_KEY_FILE"` to read its public address. The worker pays Studio transaction fees for ordinary submissions.
2. Fork this repository and clone your fork. Add `https://github.com/MuncleUscles/navier-stokes.git` as the `upstream` remote. The repository owner can clone the upstream directly. Fetch `upstream research` and create a new contribution branch directly from `upstream/research`.
3. Run `om init my-result YOUR_PUBLIC_WALLET formal`, or use `research-note` for a written argument. Complete the generated record and its matching artifact. Give sources and state what is original. Replace all template text. For a proof, use the pinned [Lean and Mathlib format](https://github.com/MuncleUscles/open-mathematics/blob/e72ff4a2b51e8cfa809865555116dfc3855e1e2e/docs/FULL-LEAN.md). Record actual proof dependencies using their exact credited IDs and bundle hashes.
4. Run `om format` on each JSON file, then `om check research/submissions/my-result.json`. The default check validates format. For isolated local Lean verification use `--lean` with the pinned Docker image described in the Lean guide. The trusted worker independently verifies the signed PR.
5. Commit exactly the two new files in one commit. Push the branch and open a PR targeting **MuncleUscles/navier-stokes:research**. Sign the exact PR as shown below, substituting the PR number. Post the unedited envelope as the PR author within nine minutes.

```sh
om sign PR_NUMBER research/submissions/my-result.json > /tmp/navier-stokes-public-claim.txt
gh pr comment PR_NUMBER --repo MuncleUscles/navier-stokes --body-file /tmp/navier-stokes-public-claim.txt
om status PR_NUMBER
```

GenLayer judges relevance, novelty and usefulness against this problem’s objective. The worker merges an approved head after the five-minute challenge window. The contract credits the signing wallet after the exact merge is confirmed. A formal result pays 80% of its fixed budget up front and reserves 20% for verified upstream proof reuse. Notes can earn up to 300 points. Points are nontransferable. Each GitHub account must be at least 30 days old and can have one active initial claim. Use `om help` for challenges, status and subsequent contribution discovery.
