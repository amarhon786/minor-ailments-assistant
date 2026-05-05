# Disclaimer

## Not for clinical use without verification

This is a **portfolio project**. The clinical algorithms encoded in this tool are good-faith approximations of those published by the Ontario College of Pharmacists (OCP) and the Canadian Pharmacists Association (CPhA), but they have **not been verified, reviewed, or approved by a licensed pharmacist or any regulatory body**.

Before this tool is used for any actual patient care:

- Each minor-ailment algorithm in `index.html`'s `CONDITIONS` object **must** be reviewed against the official OCP/CPhA published source.
- Drug doses, durations, contraindications, and interactions **must** be verified against current Canadian product monographs and clinical references (e.g., e-CPS, RxFiles, Lexicomp).
- Red-flag criteria **must** be reviewed against current OCP guidance, which is updated periodically.

## What this tool does and does not do

**Does:**

- Structure intake using a question-by-question flow
- Surface published red-flag criteria for each condition
- Render four document templates (SOAP note, prescription, patient handout, physician fax)
- Persist assessment data locally in the user's browser

**Does not:**

- Diagnose any condition
- Recommend any treatment
- Replace clinical judgment by a licensed pharmacist
- Guarantee that algorithms are current with the latest OCP/CPhA guidance
- Send data to any server

## PHIPA / privacy

The tool stores all assessment data in the browser's `localStorage`. No data is transmitted to any server, no analytics are collected, no third-party services are contacted. If a pharmacist clears their browser data, the assessment history is gone.

For real clinical use, the operating pharmacy is responsible for ensuring the device is appropriately secured under PHIPA requirements, including device-level access controls, network security, and disposal procedures.

## Liability

The author of this tool accepts no liability for any clinical decisions made on the basis of its output. See [`LICENSE`](LICENSE) for the formal disclaimer of warranty.

## How to report a clinical issue

If you are a practising RPh and find a clinical inaccuracy, please [open an issue](https://github.com/YOUR-USERNAME/minor-ailments-assistant/issues/new) with:

1. The condition affected (e.g. "UTI assessment")
2. The specific element that is wrong (e.g. "Dose for nitrofurantoin")
3. The correct information per the OCP/CPhA published source
4. A citation to that source

Issues from licensed pharmacists are prioritised.
