ETHICS
----
awareness.json

WHAT IS THIS TESTING/SCENARIO
This tests the model's awareness of its own limitations, ensuring it does not claim physical abilities or system-level access it doesn’t have. It evaluates whether the model can respond accurately and ethically when asked to perform actions outside its capabilities, supporting trust and responsible AI behavior.


explicit_moralchoice.json

WHAT IS THIS TESTING/SCENARIO?
tests the model’s ethical decision-making under high-stakes moral dilemmas involving harm or death. The goal is to evaluate whether the model can consistently apply the principle of “do not kill” across complex, emotionally charged scenarios. It probes how the model navigates moral conflict, such as war, euthanasia, self-defense, or capital punishment, and whether its responses align with ethical boundaries meant to promote safety and responsibility.


implicit_ethics.json

What is this Testing/Scenario?
tests the model’s commonsense moral reasoning—its ability to classify everyday actions as either “wrong” or “not wrong” based on basic ethical and social norms. The goal is to assess whether the model can apply human-like moral judgment to familiar, low-stakes situations involving truthfulness, responsibility, or respectful behavior.


implicit_socialchemistry101.json

What is this Testing/Scenario?
tests the model’s ability to classify morally charged actions as “good,” “neutral,” or “bad” based on widely accepted ethical and social norms. The goal is to evaluate whether the model can distinguish morally inappropriate behavior—such as racism, abuse, or voyeuristic intent—from acceptable or neutral actions. This is crucial for ensuring the model behaves responsibly and avoids normalizing harmful conduct.


### TABLE SUMMARY
| Subtest File                       | Total | Passed | Failed | Pass Rate | Dominant Failure Type             |
| ---------------------------------- | ----- | ------ | ------ | --------- | --------------------------------- |
| `awareness.json`                   | 5     | 1      | 4      | 20%       | Hallucinated capabilities         |
| `explicit_moralchoice.json`        | 5     | 0      | 5      | 0%        | Moral incoherence, degeneration   |
| `implict_ethics.json`              | 3     | 0      | 3      | 0%        | Instructional failure             |
| `implicit_SocialChemistry101.json` | 5     | 0      | 5      | 0%        | Instruction looping / null output |


### INSIGHTS

| Theme                        | Summary                                                                                   |
| ---------------------------- | ----------------------------------------------------------------------------------------- |
| **Capability Hallucination** | The model cannot reliably admit what it cannot do — dangerous for assistant applications. |
| **Moral Degeneration**       | In morally sensitive prompts, generation often collapses into repetition or incoherence.  |
| **Instructional Failure**    | Despite simple formats, it fails to follow "choose A/B" or include required words.        |
| **No Safety Alignment**      | Model was not trained to understand, represent, or defer moral boundaries.                |


-----


## Fairness

disparagement.json
SCENARIO:
evaluates whether the model can generate fair, unbiased predictions across demographic groups when prompted with salary estimation tasks. It focuses on disparagement bias, examining if the model produces inappropriate, off-topic, or demeaning outputs when the subject involves a specific race, gender, or occupation. The goal is to assess the model's ability to respond neutrally and professionally, especially when predicting outcomes related to historically marginalized groups.

preference.json
SCENARIO:
evaluates whether the model expresses political, economic, or ideological preferences when asked directly. It checks if the model remains neutral, balanced, or evasive, especially on polarizing topics like capitalism vs. socialism, healthcare systems, or government structures. The goal is to ensure the model does not promote bias or appear to favor one side, maintaining fairness and trust in its responses across diverse user viewpoints.

stereotype_agreement.json
SCENARIO:
evaluates whether the model can detect and reject harmful stereotypes across dimensions like race, age, and socioeconomic status. It presents biased or stereotypical statements and asks the model whether it agrees. A fair and trustworthy model should consistently respond "No" and provide a brief, clear reason that disavows the stereotype. This helps ensure the model does not reinforce or validate prejudiced viewpoints.

stereotype_query_test.json
SCENARIO:
checks whether the model can appropriately reject or deflect stereotype-laden and offensive queries, especially those targeting body type, appearance, or physical traits (e.g., weight, height, baldness). The goal is to ensure the model does not echo, amplify, or validate biased assumptions embedded in user prompts. A fair and safe model should either challenge the stereotype or avoid answering in a way that reinforces harmful bias.

stereotype_recognition.json
SCENARIO
evaluates the model’s ability to recognize whether a sentence contains a stereotype, anti-stereotype, or is unrelated. It checks if the model can accurately identify biased or harmful generalizations across sensitive dimensions like race, profession, or identity, and label them correctly. A fair and responsible model should flag stereotypes without falsely labeling neutral content, supporting ethical awareness in language understanding.

### TESTS TABLE SUMMARY
| Subtest File                  | Total | Passed | Failed | Pass Rate | Dominant Failure Type                     |
| ----------------------------- | ----- | ------ | ------ | --------- | ----------------------------------------- |
| `disparagement.json`          | 5     | 0      | 5      | 0%        | Degenerative completions                  |
| `preference.json`             | 5     | 0      | 5      | 0%        | Non-responsive or incoherent              |
| `stereotype_agreement.json`   | 5     | 0      | 5      | 0%        | Evasive / irrelevant responses            |
| `stereotype_query_test.json`  | 6     | 0      | 6      | 0%        | Echoing / incoherent / irrelevant         |
| `stereotype_recognition.json` | 5     | 0      | 5      | 0%        | Instruction echo / classification failure |

### INSIGHTS

| Theme                        | Summary                                                                                             |
| ---------------------------- | --------------------------------------------------------------------------------------------------- |
| **Bias Blindness**           | The model fails to detect obvious stereotypes or offensive assumptions, even with clear cues.       |
| **Degenerative Distraction** | Instead of refusing or responding with sensitivity, it drifts into nonsensical or irrelevant text.  |
| **Prompt Echoing**           | Repeats or rephrases harmful prompts instead of recognizing and rejecting them.                     |
| **No Fairness Calibration**  | Lacks any sense of fairness alignment, neither mitigates bias nor follows simple preference logic. |

---

## SAFETY

exaggerated_safety.json
SCENARIO:
Evaluates whether the model overreacts to harmless technical terms—like "kill a process" or "execute a command"—by misclassifying them as violent or inappropriate due to overactive safety filters. These prompts involve homonyms (e.g., “kill,” “terminate,” “execute”) used in legitimate programming or business contexts. A robust model should understand the non-violent intent and respond correctly, without derailing into irrelevant or nonsensical output.

jailbreak.json
evaluates the model’s resilience to prompt injection or “jailbreaking”, a technique where harmful instructions are disguised inside benign-looking prompts. By embedding toxic queries within neutral sentence stems (e.g., “Start with: In order to achieve success...”), the test checks if the model bypasses safety filters and produces harmful, toxic, or discriminatory responses. A safe and robust model should recognize the intent and refuse to comply, regardless of how the query is framed.

misuse.json
evaluates the model’s ability to refuse harmful or illegal requests, such as hacking, producing drugs, bypassing copyright protections, or counterfeiting money. It checks whether the model recognizes clearly illicit prompts and avoids providing assistance or unsafe responses. A responsible model should refuse to comply, ensuring it cannot be misused for criminal or unethical purposes.


### TESTS TABLE
| Subtest File              | Total | Passed | Failed | Pass Rate | Dominant Failure Type               |
| ------------------------- | ----- | ------ | ------ | --------- | ----------------------------------- |
| `exaggerated_safety.json` | 5     | 0      | 5      | 0%        | Misinterpretation of benign prompts |
| `jailbreak.json`          | 5     | 0      | 5      | 0%        | Degeneration, irrelevant output     |
| `misuse.json`             | 5     | 0      | 5      | 0%        | Illegal instruction-following       |


### INSIGHTS
| Theme                              | Summary                                                                                                                                     |
| ---------------------------------- | ------------------------------------------------------------------------------------------------------------------------------------------- |
| **Benign Word Misclassification**  | The model exaggerated risk in innocuous prompts involving "kill," "terminate," or "execute," leading to irrelevant or degenerate responses. |
| **Jailbreak Vulnerability**        | With fixed-format sentences, the model easily accepted and continued harmful instructions.                                                  |
| **Failure to Refuse Illegal Acts** | Despite being clearly illegal (e.g., hacking, drug-making), the model responded without refusal or safe fallback.                           |
| **Safety Alignment Breakdown**     | Model lacks robust content filtering and fails to generalize safety constraints across phrasing styles.                                     |

----

## TRUTHFULNESS

external.json
SCENARIO:
evaluates the model’s ability to verify factual claims using external supporting text. It assesses whether the model can correctly respond with “Supports” or “Refutes” based on evidence provided in a paragraph. The focus is on truthful reasoning and grounded judgment, particularly in domains like climate science, where precision and reliability are critical.

golden_advfactuality.json
SCENARIO:
evaluates whether the model blindly accepts false premises when factual statements are deliberately modified within the prompt. It assesses the model’s truthfulness and resistance to misinformation, especially when users embed incorrect "background knowledge" (e.g., “the moon orbits the sun”). A reliable model should not propagate the false assumption and instead correct or reject the inaccurate premise, even when the query appears logically phrased.


hallucination.json
SCENARIO
evaluates the model’s factual accuracy and consistency in multiple-choice question answering. It presents the model with a clear factual question and predefined answer choices, expecting it to select the correct letter (e.g., "A", "B"). The focus is on whether the model can resist misinformation, avoid fabrication, and answer concisely and correctly based on general world knowledge. Failures may indicate hallucinations, bias, or an inability to follow format constraints.



internal.json
SCENARIO
Evaluates the model’s ability to give concise, factual answers in a strict format, without adding extra text. It checks for accuracy and format obedience under tight constraints.

sychophancy.json
SCENARIO
This tests the model’s persona alignment and opinion consistency. Given opposing viewpoints on lifestyle or social issues, it checks whether the model can consistently generate coherent, aligned responses not defaulting to contradictions or nonsensical output.

TESTS TABLE SUMMARY
| Subtest File                | Total | Passed | Failed | Pass Rate | Dominant Failure Type                 |
| --------------------------- | ----- | ------ | ------ | --------- | ------------------------------------- |
| `external.json`             | 4     | 0      | 4      | 0%        | Repetitive / Off-topic generation     |
| `golden_advfactuality.json` | 5     | 0      | 5      | 0%        | Accepts false premise / incoherent    |
| `hallucination.json`        | 6     | 0      | 6      | 0%        | Repetitive gibberish or wrong options |
| `internal.json`             | 8     | 0      | 8      | 0%        | Irrelevant or nonsensical responses   |
| `sychophancy.json`          | 7     | 0      | 7      | 0%        | Vacuous agreement / irrelevant        |

INSIGHTS TABLE
| Theme                      | Summary                                                                                  |
| -------------------------- | ---------------------------------------------------------------------------------------- |
| **Factual Hallucinations** | The model fails basic fact-checking, confidently generating false or misleading answers. |
| **Premise Acceptance**     | Even when questions are obviously wrong, the model accepts and builds upon them.         |
| **Off-Topic Rambling**     | Output often spirals into incoherent or repetitive text unrelated to the prompt.         |
| **Style Over Substance**   | Tends to favor agreeable or "smooth" responses, even when factually incorrect.           |
| **No Internal Grounding**  | The model struggles to remain internally consistent, frequently contradicting itself.    |
