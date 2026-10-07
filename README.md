# Khair group fund dashboard

A read-only Streamlit dashboard connected to the published Khair Google Sheet. It fetches the CSV from the server when a new app session opens and includes a **Refresh data** button for an immediate update. It does not write to the sheet.

The dashboard also ranks members with the most unpaid months, estimates current P/L for the 7.7 g 22K and 10 g 24K holdings from the latest published Bahrain reference rates, prepares WhatsApp reminder drafts, and creates a downloadable group-update image. WhatsApp drafts are opened for review; the app never sends messages automatically. Gold values are estimates based on the linked rate source and may differ from a shop's buyback price.

## Run on Windows

From this folder:

```powershell
python -m venv .venv
.venv\Scripts\Activate.ps1
python -m pip install -r requirements.txt
python -m streamlit run app.py
```

Streamlit will print a local address (usually `http://localhost:8501`) to open in your browser. This avoids the browser restrictions that affected the standalone HTML file.

The source CSV is published for public reading. Anyone with the published URL can read the data exposed by that sheet. To change payments or ledger values, edit the Google Sheet itself and refresh the dashboard.

## Host online with Streamlit Community Cloud

1. Create a GitHub repository and upload this project folder, including `app.py`, `requirements.txt`, `.streamlit/config.toml`, and `assets/khair-logo.png`.
2. Sign in at [share.streamlit.io](https://share.streamlit.io/) with GitHub and choose **Create app**.
3. Select the repository and branch, set the app file to `app.py`, and deploy.
4. Use the app's **Settings → Sharing** options to choose who can view it. Invite specific viewers if the app should be restricted.

The published Google CSV is independently public, even if the dashboard itself is private. Do not add private phone or email data to a publicly published CSV. To protect member data, the sheet connection must be changed to an authenticated Google Sheets API before publishing those details online.
