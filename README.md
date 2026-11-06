# PROG101_Assignment1_Must-apha-Saadiq-Bangura-_905005983
Logical design Solutions for Sierra Leone Community Challengers in the health Sector
A simple, open-source Python program that helps a nurse or clerk record patient arrivals, validate the details entered, and calculate a **priority score** so that the most urgent patients are identified first.

Built for **PROG101: Principles of Programming Logic and Design** (BBIT 1101, Department of ICT) as a prototype for health facilities in Sierra Leone.

> **Important:** This is an educational prototype. The scores are illustrative and are **not** official Sierra Leone Ministry of Health triage standards. The score supports decision-making and does not replace clinical judgement. Any patient who appears to be in a life-threatening condition must be seen by a clinician immediately, whatever the score says.

---

## What the code does

The program runs in the terminal and loops until the operator chooses to stop. For each patient it:

1. **Collects** a patient reference (e.g. `HN-0001`), a condition category, days since symptoms began, number of reported symptoms, and whether the patient is vulnerable (child under 5, pregnant woman, or elderly).
2. **Validates** the entry. Reports with a blank reference, negative numbers, or an unrecognised condition are rejected with an error.
3. **Calculates** a priority score.
4. **Classifies** the patient as HIGH, MEDIUM or LOW priority.
5. **Displays and stores** the report in a list for the current session.
6. **Asks** whether to enter another patient. When finished, it shows a session summary.

### Scoring rules

| Condition category | Base score |
| --- | --- |
| CRITICAL (life-threatening) | 40 |
| URGENT | 35 |
| MODERATE | 25 |
| ROUTINE | 15 |

| Risk indicator | Points added |
| --- | --- |
| Vulnerable patient (child under 5, pregnant woman, elderly) | +20 |
| Symptoms present for 7 days or more | +10 |
| Five or more reported symptoms | +5 |

| Final score | Priority level |
| --- | --- |
| 60 or above | HIGH |
| 35 to 59 | MEDIUM |
| Below 35 | LOW |

### Sample output

```
--- PATIENT TRIAGE REPORT ---
Record ID: 1
Patient reference: HN-0001
Condition: CRITICAL
Days since symptoms began: 2
Vulnerable patient: Yes
Reported symptoms: 1
Priority score: 60
Priority level: HIGH
Action: Alert the duty clinician for immediate assessment.
```

### How it is structured

The program is modular, with each part having a single responsibility:

| Module / function | Responsibility |
| --- | --- |
| Input | Collects patient information |
| Validation | Checks the information is complete and valid |
| `calculate_priority()` | Computes the score from condition, days, vulnerability and symptom count |
| `classify_priority()` | Turns the score into HIGH / MEDIUM / LOW |
| Display | Prints the report |
| Record | Stores accepted reports in a list |
| Main control | Runs the `while` loop and coordinates everything |

Core concepts used: variables and data types (integer, string, boolean, list), decision structures (`if / elif / else`), repetition (`while`), and functions. The design process followed computational thinking: decomposition, pattern recognition and abstraction.

### Privacy by design

The program deliberately does **not** collect patient names or other personal details. It uses only a reference number and the minimum clinical indicators needed to compute priority.

---

## Why it matters

- **Faster identification of urgent cases.** Crowded waiting areas and limited staff can cause critically ill patients to wait behind less serious ones. A consistent scoring method helps surface them sooner.
- **Fair, consistent assessment.** Every patient is scored by the same rules, regardless of who is on duty.
- **Better records.** Counts of critical cases and case types can help managers spot peak periods and plan staffing and supplies.
- **Low cost and adaptable.** It needs only Python and a basic computer, so district hospitals, primary health centres and clinics could adapt it to local needs.
- **Aligned with global goals.** It supports UN Sustainable Development Goals 3 (Good Health and Well-being), 9 (Industry, Innovation and Infrastructure) and 10 (Reduced Inequalities), and, more loosely, 16 and 17.

Open-source code can also grow into a **Digital Public Good** if it is documented, openly licensed, responsibly maintained, and protects privacy. Public source code alone does not make it a formally recognised Digital Public Good.

---

## Getting started

### Requirements

- Python 3 (any recent version)
- A terminal on Windows, Linux or macOS
- Optional: Git, and a code editor such as Visual Studio Code

### Run it

```bash
git clone <your-repository-url>
cd <repository-folder>
python triage.py
```

Replace `triage.py` with the name of the main script in this repository. Then follow the prompts. Enter `YES` or `NO` when asked whether another patient should be entered.

---

## How others can use it

- **Students:** a worked example of computational thinking, pseudocode, flowcharts and modular Python. Read the code alongside the pseudocode and try changing the scoring rules.
- **Educators:** use it as a teaching case for decision structures, loops, functions and validation.
- **Health facilities and developers:** treat it as a starting point for a real tool, but only after clinical review of the scoring rules and a proper privacy and security assessment.

---

## How to contribute

Contributions are welcome, from code to documentation to clinical review.

1. **Fork** the repository and create a branch: `git checkout -b feature/your-idea`
2. **Make your change**, keeping functions small and single-purpose, and adding comments where logic is not obvious.
3. **Test it** with a range of inputs, including invalid ones (blank reference, negative days, unknown condition) and boundary scores (34/35 and 59/60).
4. **Commit** with a clear message and push your branch.
5. **Open a pull request** describing what you changed and why.

You can also open an **issue** to report a bug or suggest a feature.

### Ideas for improvement

The prototype has known limitations, which are good places to start:

- Reports are held in memory only and are lost when the program ends. Add storage in **SQLite** or **PostgreSQL**, or export to CSV.
- Add a **web interface** that works on tablets and computers.
- Add **offline recording and synchronisation** for facilities with unreliable connectivity.
- Capture **vital signs** (temperature, pulse) and patient-status tracking.
- Add **alerts** for duty clinicians and ward staff.
- Add **authentication, access controls and audit logs** for patient data.
- Add **local-language support**.
- Build a **dashboard** for waiting times and case numbers.
- Have the scoring rules **reviewed by clinicians** and aligned with national guidelines.

### Contribution guidelines

- Keep patient privacy first: never add real patient data to the repository or to issues.
- Do not present the scoring as an approved clinical standard.
- Be respectful and constructive in discussions.

---

## Limitations

- Scores are illustrative and need clinical review before any operational use.
- Reports are not saved after the session ends.
- The program does not verify the accuracy of what the operator enters.
- There are no user accounts, access control or database.
- It does not alert staff automatically.
