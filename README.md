# STI Information Assistant — GitHub/Streamlit Ready
Bilingual English/Kiswahili educational/research prototype. It is not a diagnostic or prescribing system.

## Deploy
Upload this folder's contents to the root of a GitHub repository. In Streamlit Community Cloud create an app from the repository, choose `main`, and set the entrypoint to `app.py`.

In Streamlit App Settings > Secrets add:
```toml
ADMIN_USERNAME = "your-admin-name"
ADMIN_PASSWORD = "your-long-unique-password"
```
Do not commit real credentials. `.gitignore` excludes `.streamlit/secrets.toml` and `sti_app.db`.

## Local run
Set `ADMIN_USERNAME` and `ADMIN_PASSWORD` as environment variables, then:
```bash
python -m pip install -r requirements.txt
python -m streamlit run app.py
```

## Content governance
All seeded content is `pending_review`; only explicitly approved content is learner-visible. The application does not manufacture expert approval. A qualified Kenyan STI clinician/public-health reviewer and Kiswahili health-communication reviewer should approve content before real deployment.

## Important persistence note
This prototype uses SQLite. Hosted Streamlit local storage is not durable production storage; approvals, audit records, and inquiries may be lost on rebuild/replacement. For a real pilot/production system requiring persistent records, migrate the SQLAlchemy connection to a managed persistent database and complete security/privacy review.

The bundled TF-IDF + Logistic Regression model and tiny bilingual training dataset demonstrate the NLP pipeline; their evaluation is not research-grade validation.


## Changing the deployed admin login
`ADMIN_USERNAME` and `ADMIN_PASSWORD` in Streamlit App Settings > Secrets are authoritative. After changing either value, save the Secrets and reboot/redeploy the app. On startup, the application synchronizes the admin account automatically; no manual database editing is required.
