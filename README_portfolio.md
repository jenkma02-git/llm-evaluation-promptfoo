# LLM Evaluation Practice with Promptfoo

A small, hands-on quality engineering project exploring how to evaluate **large language model (LLM)** responses with [Promptfoo](https://www.promptfoo.dev/). This is an evolving learning project, not a production evaluation framework.

## Why I built this

My background is in software quality engineering and test automation. Traditional automated tests often check predictable outcomes; LLM-generated answers introduce variability even when the prompt stays the same. I wanted to explore how familiar QA principles—clear expected behavior, meaningful assertions, repeatability, and investigating failures—translate to AI-powered applications.

## Evaluation scenario

The initial exercise uses a fictional **Acme Store return policy**. The goal is to see whether an assistant answers policy questions consistently and stays aligned with the reference information supplied to it.

Sample questions explored include:

- Whether an item can be returned after **20 days**.
- How long a **refund** takes to process.

I ran evaluations more than once and compared the outputs, paying attention to variations in wording and the challenges of distinguishing harmless differences from meaningful failures.

## What I'm exploring

- **Expected behavior:** Defining what a correct, useful answer should communicate.
- **Grounding:** Checking whether an answer is supported by the policy provided, rather than making up details.
- **Nondeterminism:** Observing how repeated model calls can produce different responses.
- **Assertion design:** Thinking about checks that catch real problems without requiring every answer to use identical wording.
- **Evaluation reliability:** Understanding retries, provider variability, and the difference between a flaky test and a genuinely inconsistent answer.

These are learning goals and areas of investigation—not claims of comprehensive automated coverage.

## Tools

- **Promptfoo** for organizing and running prompt evaluations.
- **Anthropic Claude** as a model provider during experimentation.
- **Node.js / npm** for the local development environment.

See `promptfooconfig.yaml` for the prompts, provider configuration, test cases, and assertions actually implemented in this repository.

## Run locally

You'll need Node.js and access to any model provider configured in `promptfooconfig.yaml`.

1. Clone the repository and open it in a terminal.
2. Install dependencies if the repository includes a `package.json`: `npm install`.
3. Configure your provider credentials **locally**, following that provider's instructions. Do not commit API keys or `.env` files.
4. Run the evaluation:

   ```bash
   npx promptfoo eval
   ```

5. View results:

   ```bash
   npx promptfoo view
   ```

If Promptfoo is installed globally, `promptfoo eval` and `promptfoo view` work as well. The exact provider setup and results depend on the current configuration.

## What I've learned so far

A response can differ in phrasing without being incorrect. Conversely, a polished, confident response can still contradict its source material. For AI quality engineering, the challenge is to define the **behavior that matters**, evaluate it against a reliable source of truth, and inspect surprising or inconsistent results rather than treating a single pass/fail result as the whole story.

## Next steps

- Add more policy questions, including edge cases and ambiguous requests.
- Strengthen assertions to test important facts without overfitting to exact wording.
- Compare repeat runs and document meaningful failure examples.
- Experiment with additional providers and evaluation approaches.
- Expand documentation with findings supported by actual test results.

## References

- [Promptfoo documentation](https://www.promptfoo.dev/docs/intro/)
- [Configuration guide](https://www.promptfoo.dev/docs/configuration/guide/)
- [Assertions and metrics](https://www.promptfoo.dev/docs/configuration/expected-outputs/)

---

*Portfolio note: This repository documents ongoing, hands-on exploration of LLM evaluation through the lens of software quality engineering.*
