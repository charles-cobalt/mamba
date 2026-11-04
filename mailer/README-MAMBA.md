# MAMBA mailer (auto emails) - DISABLED pending Charles's approval

This is the Jarvis hourly auto-email sender, adapted for MAMBA:
- reads opted-in accounts from the MAMBA project Firestore collection `mamba_jarvis_users`
- renders the report from `jarvis/index.html` (the MAMBA Jarvis section)
- sends via Brevo with sender name MAMBA

It is NOT active. To enable, all of these must happen after Charles approves the MAMBA sender identity:
1. Create a NEW Brevo account for MAMBA (do not reuse the Jarvis key: 300/day cap is per account and sender reputation is shared).
2. Add repo secrets on charles-cobalt/mamba: FIREBASE_SERVICE_ACCOUNT (new MAMBA project service account), MAIL_CODE_SALT (new random), MAIL_PROVIDER=brevo, BREVO_API_KEY (new account), MAIL_FROM (approved sender address).
3. Copy auto-email.workflow.yml to .github/workflows/auto-email.yml. The hourly cron is 17 * * * *.

Until then nothing sends: no workflow is installed and no secrets exist.
