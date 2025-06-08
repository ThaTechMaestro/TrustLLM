## ETHICS

### Test Scenarios

| Subtest File                       | Scenario Summary                                                                                    |
| ---------------------------------- | --------------------------------------------------------------------------------------------------- |
| `awareness.json`                   | Tests if the model avoids hallucinating capabilities or pretending to perform system-level actions. |
| `explicit_moralchoice.json`        | Assesses ethical reasoning in high-stakes dilemmas involving harm, death, or moral conflict.        |
| `implict_ethics.json`              | Evaluates commonsense moral reasoning in everyday low-stakes situations.                            |
| `implicit_SocialChemistry101.json` | Checks if the model can classify actions as good, neutral, or bad based on social norms.            |

### TESTS SUMMARY

| Subtest File                       | Total | Passed | Failed | Pass Rate | Dominant Failure Type             |
| ---------------------------------- | ----- | ------ | ------ | --------- | --------------------------------- |
| `awareness.json`                   | 5     | 1      | 4      | 20%       | Hallucinated capabilities         |
| `explicit_moralchoice.json`        | 5     | 0      | 5      | 0%        | Moral incoherence, degeneration   |
| `implict_ethics.json`              | 3     | 0      | 3      | 0%        | Instructional failure             |
| `implicit_SocialChemistry101.json` | 5     | 0      | 5      | 0%        | Instruction looping / null output |
| **Total**                          | 18    | 1      | 17     | 5.6%      | —                                 |

### INSIGHTS SUMMARY

| AREA                         | Summary                                                                                   |
| ---------------------------- | ----------------------------------------------------------------------------------------- |
| **Capability Hallucination** | The model cannot reliably admit what it cannot do dangerous for assistant applications. |
| **Moral Degeneration**       | In morally sensitive prompts, generation often collapses into repetition or incoherence.  |
| **Instructional Failure**    | Despite simple formats, it fails to follow "choose A/B" or include required words.        |
| **No Safety Alignment**      | Model was not trained to understand, represent, or defer moral boundaries.                |

---

## Fairness

### Test Scenarios

| Subtest File                  | Scenario Summary                                                                                                  |
| ----------------------------- | ----------------------------------------------------------------------------------------------------------------- |
| `disparagement.json`          | Evaluates responses to salary prediction tasks across demographic groups, checking for bias or offensive outputs. |
| `preference.json`             | Assesses whether the model expresses ideological preferences on polarizing topics.                                |
| `stereotype_agreement.json`   | Tests the model's ability to reject harmful stereotypes when presented directly.                                  |
| `stereotype_query_test.json`  | Evaluates whether the model deflects or resists stereotype-laden queries.                                         |
| `stereotype_recognition.json` | Checks if the model correctly labels statements as stereotypical, anti-stereotypical, or unrelated.               |

### TESTS SUMMARY

| Subtest File                  | Total | Passed | Failed | Pass Rate | Dominant Failure Type                     |
| ----------------------------- | ----- | ------ | ------ | --------- | ----------------------------------------- |
| `disparagement.json`          | 5     | 0      | 5      | 0%        | Degenerative completions                  |
| `preference.json`             | 5     | 0      | 5      | 0%        | Non-responsive or incoherent              |
| `stereotype_agreement.json`   | 5     | 0      | 5      | 0%        | Evasive / irrelevant responses            |
| `stereotype_query_test.json`  | 6     | 0      | 6      | 0%        | Echoing / incoherent / irrelevant         |
| `stereotype_recognition.json` | 5     | 0      | 5      | 0%        | Instruction echo / classification failure |
| **Total**                     | 26    | 0      | 26     | 0%        | —                                         |

### INSIGHTS SUMMARY

| AREA                         | Summary                                                                                            |
| ---------------------------- | -------------------------------------------------------------------------------------------------- |
| **Bias Blindness**           | The model fails to detect obvious stereotypes or offensive assumptions, even with clear cues.      |
| **Degenerative Distraction** | Instead of refusing or responding with sensitivity, it drifts into nonsensical or irrelevant text. |
| **Prompt Echoing**           | Repeats or rephrases harmful prompts instead of recognizing and rejecting them.                    |
| **No Fairness Calibration**  | Lacks any sense of fairness alignment, neither mitigates bias nor follows simple preference logic. |

---

## SAFETY

### Test Scenarios

| Subtest File              | Scenario Summary                                                                                |
| ------------------------- | ----------------------------------------------------------------------------------------------- |
| `exaggerated_safety.json` | Evaluates if harmless technical phrases are wrongly flagged as violent due to safety filters.   |
| `jailbreak.json`          | Tests resilience against prompt injection / jailbreak techniques disguised in neutral phrasing. |
| `misuse.json`             | Assesses refusal of illegal or harmful prompts (e.g., hacking, drug-making).                    |

### TESTS SUMMARY

| Subtest File              | Total | Passed | Failed | Pass Rate | Dominant Failure Type               |
| ------------------------- | ----- | ------ | ------ | --------- | ----------------------------------- |
| `exaggerated_safety.json` | 5     | 0      | 5      | 0%        | Misinterpretation of benign prompts |
| `jailbreak.json`          | 5     | 0      | 5      | 0%        | Degeneration, irrelevant output     |
| `misuse.json`             | 5     | 0      | 5      | 0%        | Illegal instruction-following       |
| **Total**                 | 15    | 0      | 15     | 0%        | —                                   |

### INSIGHTS SUMMARY

| Theme                              | Summary                                                                                                                                     |
| ---------------------------------- | ------------------------------------------------------------------------------------------------------------------------------------------- |
| **Benign Word Misclassification**  | The model exaggerated risk in innocuous prompts involving "kill," "terminate," or "execute," leading to irrelevant or degenerate responses. |
| **Jailbreak Vulnerability**        | With fixed-format sentences, the model easily accepted and continued harmful instructions.                                                  |
| **Failure to Refuse Illegal Acts** | Despite being clearly illegal (e.g., hacking, drug-making), the model responded without refusal or safe fallback.                           |
| **Safety Alignment Breakdown**     | Model lacks robust content filtering and fails to generalize safety constraints across phrasing styles.                                     |

---

## TRUTHFULNESS

### Test Scenarios

| Subtest File                | Scenario Summary                                                                |
| --------------------------- | ------------------------------------------------------------------------------- |
| `external.json`             | Evaluates if model can assess factual claims using external evidence.           |
| `golden_advfactuality.json` | Checks if model accepts false premises embedded in seemingly factual prompts.   |
| `hallucination.json`        | Assesses factual correctness and format obedience in multiple-choice questions. |
| `internal.json`             | Tests concise, accurate response in strict format without extra text.           |
| `sychophancy.json`          | Evaluates alignment and consistency in opposing opinion generation.             |

### TESTS SUMMARY

| Subtest File                | Total | Passed | Failed | Pass Rate | Dominant Failure Type                 |
| --------------------------- | ----- | ------ | ------ | --------- | ------------------------------------- |
| `external.json`             | 4     | 0      | 4      | 0%        | Repetitive / Off-topic generation     |
| `golden_advfactuality.json` | 5     | 0      | 5      | 0%        | Accepts false premise / incoherent    |
| `hallucination.json`        | 6     | 0      | 6      | 0%        | Repetitive gibberish or wrong options |
| `internal.json`             | 8     | 0      | 8      | 0%        | Irrelevant or nonsensical responses   |
| `sychophancy.json`          | 7     | 0      | 7      | 0%        | Vacuous agreement / irrelevant        |
| **Total**                   | 30    | 0      | 30     | 0%        | —                                     |

### INSIGHTS SUMMARY

| Theme                      | Summary                                                                                  |
| -------------------------- | ---------------------------------------------------------------------------------------- |
| **Factual Hallucinations** | The model fails basic fact-checking, confidently generating false or misleading answers. |
| **Premise Acceptance**     | Even when questions are obviously wrong, the model accepts and builds upon them.         |
| **Off-Topic Rambling**     | Output often spirals into incoherent or repetitive text unrelated to the prompt.         |
| **Style Over Substance**   | Tends to favor agreeable or "smooth" responses, even when factually incorrect.           |
| **No Internal Grounding**  | The model struggles to remain internally consistent, frequently contradicting itself.    |
