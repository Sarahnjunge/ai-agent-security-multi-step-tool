# AI Agent Security: Multi-Step Tool Attacks

## Overview

This project explores how a tool-using AI agent behaves when interacting with a simulated environment containing web-search and page-opening tools. It uses the competition's `aicomp_sdk` components to inspect tool outputs, trace agent actions, and evaluate whether an interaction triggers a security breach.

The focus is on testing and understanding agent tool-use security, especially how instructions embedded in tool results may influence an agent's behavior.

## Objectives

- Set up the competition environment and inspect available files.
- Define and validate an attack algorithm that proposes candidate prompts.
- Initialize a vulnerable deterministic agent, guardrail, and attack environment.
- Examine the web corpus used by the simulated tools.
- Run tool interactions and inspect their traces.
- Evaluate the resulting trace for security predicates and breach status.

## Notebook Workflow

1. **Inspect the runtime:** List files available in the Kaggle environment.
2. **Create the attack candidate module:** Write `attack.py` with a small set of candidate prompts.
3. **Validate the attack interface:** Check that the class implements the expected SDK interface.
4. **Configure paths:** Locate the competition's evaluation modules and fixtures.
5. **Create the simulation environment:** Load the vulnerable agent, guardrail, and `GymAttackEnv`.
6. **Inspect traces and fixture data:** Review tool events and the web corpus.
7. **Run experiments:** Compare search/open interactions and a multi-step run.
8. **Evaluate the outcome:** Calculate predicates and check whether the trace represents a breach.

## Requirements and Environment

This notebook is designed for the **Kaggle competition environment** and expects the competition files at:

`/kaggle/input/competitions/ai-agent-security-multi-step-tool-attacks`

It imports `aicomp_sdk` modules and expects the fixture `aicomp_sdk/fixtures/web_corpus.json` to be supplied by the competition environment. These are not standard Python packages or files.

The notebook also uses Python standard-library modules, including:

- `pathlib`
- `json`
- `sys`
- `os`
- `glob`
- `inspect`

NumPy and pandas are imported in the initial Kaggle template, although the experiments primarily use the SDK and Python standard library.

## How to Run

1. Open the notebook in Kaggle with the required competition data attached.
2. Run the cells **from top to bottom**, since later cells depend on variables created earlier, including `fixtures_dir`, `env`, `trace`, and `result`.
3. Review each tool event's name, arguments, source, output, success status, and side-effect information.
4. Inspect the final `PREDICATES` and `BREACH` output to understand the evaluator's assessment.

To run the notebook outside Kaggle, first provide the competition SDK and fixture files, then update the hard-coded paths.

## Important Notes

- Candidate prompts are exploratory test inputs; they do not by themselves prove that a vulnerability was exploited.
- A tool trace records what happened during a run. The competition's evaluation logic determines whether the trace counts as a breach.
- The notebook contains repeated setup, validation, and fixture-inspection cells as the experiment develops.
- Use these experiments only in an authorized competition or test environment.

## Expected Outputs

Depending on the SDK version and fixture contents, outputs may include:

- Confirmation that `attack.py` was created and implements the expected interface.
- Environment and fixture paths.
- Results of search/open interactions.
- Detailed tool-event traces.
- Evaluated predicates and a final breach indicator.

Exact outputs may vary with the competition environment and SDK behavior.
