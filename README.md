# CommissionIQ — MF Commission Tracker

A **free, browser-based** tool to calculate expected trail and upfront commissions from your WealthMagic exports. No server, no login — runs entirely in your browser.

## 🔗 Live App
> **[Open CommissionIQ](https://sakethdonepudi.github.io/commissioniq/)**  
> *(Replace with your actual GitHub Pages URL after deployment)*

---

## ✨ Features
- Upload AUM Report + Transaction Report from WealthMagic (Excel/CSV)
- Maintain your own **Rate Master** — AMC + Fund → Trail % + Upfront %
- **Auto-adjusts AUM** using post-snapshot transactions (purchases/redemptions)
- Calculates **expected trail commission** = Adjusted AUM × Annual Rate ÷ 12
- Calculates **expected upfront** on PUR/SIP/STP-I transactions
- Groups results by AMC — see what each AMC owes you
- Folio-level scheme detail view
- Export dashboard & detail as CSV
- Rates saved in browser (persist across sessions)
- Works on mobile, tablet, desktop

---

## 📁 Repository Structure
```
commissioniq/
├── index.html                          # The full app (single file)
├── templates/
│   ├── AUM_Report_Template.xlsx        # AUM upload format
│   └── Transaction_Report_Template.xlsx # Transaction upload format
└── README.md
```

---

## 🚀 Deploy to GitHub Pages (5 minutes)

### Step 1 — Create Repository
1. Go to [github.com](https://github.com) → Sign in → Click **"New repository"**
2. Name it: `commissioniq`
3. Set to **Public**
4. Click **"Create repository"**

### Step 2 — Upload Files
1. Click **"uploading an existing file"** on the repo page
2. Drag and drop:
   - `index.html`
   - `templates/AUM_Report_Template.xlsx`
   - `templates/Transaction_Report_Template.xlsx`
   - `README.md`
3. Click **"Commit changes"**

### Step 3 — Enable GitHub Pages
1. Go to repo **Settings** → **Pages** (left sidebar)
2. Under **Source**, select **"Deploy from a branch"**
3. Branch: **main** | Folder: **/ (root)**
4. Click **Save**
5. Wait ~2 minutes → your app is live at:  
   `https://YOUR-USERNAME.github.io/commissioniq`

---

## 📋 How to Use

### First Time Setup
1. Go to **⚙️ Rate Master** tab
2. Click **+ Add Rate** for each AMC + Fund combination
3. Enter the Annual Trail % and Upfront % as per your AMC agreements

### Every Month
1. Export AUM Report from WealthMagic → save as Excel/CSV
2. Export Transaction Report from WealthMagic → save as Excel/CSV
3. Go to **📤 Upload Reports** tab
4. Upload both files
5. Set the **Report Month** and **AUM Snapshot Date**
6. Click **⚡ Calculate Expected Commissions**
7. View results in **📊 Dashboard** tab

---

## 🧮 Calculation Logic

### Trail Commission
```
Adjusted AUM = AUM (from report) + Purchases after AUM date − Redemptions after AUM date
Expected Trail = (Adjusted AUM × Annual Trail Rate%) ÷ 12
```

### Upfront Commission
```
Expected Upfront = Purchase Amount × Upfront Rate%
Eligible transaction types: PUR, SIP, STP-I
```

### Transaction Type Classification
| Type | Effect | Upfront? |
|------|--------|----------|
| PUR / SIP | ➕ Adds to AUM | ✅ Yes |
| STP-I | ➕ Adds to AUM | ✅ Yes |
| STP-O | ➖ Reduces AUM | ❌ No |
| RED / SWP | ➖ Reduces AUM | ❌ No |
| Div-R / Rev-I | ➕ Stays | ❌ No |

---

## ⚠️ Important Notes
- **Rates are stored locally** in your browser. They will persist unless you clear browser data.
- Export your rates as CSV (Rate Master → Export CSV) for backup.
- Amounts must be in **₹ absolute** (not lakhs) in the upload files.
- Dates should be in **DD-MMM-YYYY** format (e.g. 15-Mar-2025).

---

## 📞 Support
Built for internal use at wealth management firms. For issues or feature requests, open a GitHub Issue.
