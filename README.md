## AkshayaMetrics

AkshayaMetrics is a **web-based Food Distribution and Waste Tracking System**.
It supports the **AkshayaShakti Foundation’s AkshayaAahaar initiative**, helping volunteers log, visualize, and analyze food distribution data to reduce waste and improve efficiency.

---

## 🌱 Project Overview

The platform allows volunteers to:
- Record meals cooked, distributed, and wasted at various centers.
- View total efficiency and trends through interactive charts.
- Generate visual reports and export data as CSV.
- Share feedback directly with the admin dashboard.

Admins can review and manage all volunteer feedback through a clean, separate **Admin Panel**.
---
## 🧩 Core Files

### 1. `dashboard.html`
The main web application interface where volunteers interact.  
It includes multiple sections:
- **Dashboard:** Real-time metrics and charts using Chart.js  
- **Data Entry:** Add or manage daily meal records  
- **Reports:** Filter, visualize, and export data  
- **About:** Project background and SDG alignment  
- **Contact:** Feedback form saved to local storage  

### 2. `admin.html`
A minimal admin dashboard that reads stored feedback data from `localStorage` and allows the admin to clear or review submissions.

---

## ⚙️ Technical Stack

| Component | Technology Used |
|------------|----------------|
| Structure | HTML5 |
| Styling | CSS3 (Custom Variables & Grid Layout) |
| Scripting | Vanilla JavaScript (ES6) |
| Data Storage | Browser `localStorage` |
| Charts & Reports | Chart.js (via CDN) |
| Icons & Fonts | Google Fonts: *Poppins* |

No external backend or database is required — the app works entirely on the client side.

---

## 🔍 Main JavaScript Functions

### From `dashboard.html`

#### Storage Management
- **`loadEntriesLocal()`** – Reads stored entries from localStorage.  
- **`saveEntriesLocal(list)`** – Saves the updated list to localStorage.  
- **`persist()`** – Syncs the in-memory data with storage.

#### CRUD Operations
- **`addEntry(entry)`** – Adds a new food record and updates charts.  
- **`updateEntry(id, updated)`** – Edits existing entries.  
- **`removeEntry(id)`** – Deletes an entry from the record list.

#### Validation & Helpers
- **`validateEntry(obj)`** – Checks data before saving.  
- **`formatDateISO(d)`**, **`escapeHtml(s)`**, **`uid(prefix)`** – Utility helpers.

#### UI Rendering
- **`refreshKPIs()`** – Updates total cooked, distributed, wasted, and efficiency data.  
- **`refreshTables()`** – Rebuilds data tables.  
- **`refreshCharts()`** – Draws bar and line charts (Meals Cooked vs Distributed, Wastage Over Time).  
- **`drawEffGauge(percent)`** – Displays circular efficiency gauge.  
- **`refreshReports()`**, **`applyReportFilters()`**, **`buildFilteredReports()`** – Handle report analytics and filtering.  
- **`exportCSV()`** – Downloads data as a `.csv` report.  
- **`refreshAll()`** – Runs all updates on page load or data change.

#### Contact & Feedback
Handles feedback submission via:
```js
const STORAGEKEY = 'akshaya_feedbacks';
localStorage.setItem(STORAGEKEY, JSON.stringify(feedbacks));
```

---

### From `admin.html`

#### Data Handling
- **`loadFeedbacks()`** – Loads all saved feedback entries from localStorage and displays them in a table.  
- **Clear Button Event** – Wipes feedback data upon confirmation.

---

## 📊 How Data Works

1. When a volunteer fills out the Data Entry form, details are stored in browser storage (`akshayametrics_entries_v1`).
2. The dashboard and charts automatically update to reflect total meals, distributed meals, and wastage.
3. Reports can be filtered by date or center, and the summarized data can be exported to CSV.
4. Feedback submitted from the Contact page is stored under `akshaya_feedbacks`.
5. The admin dashboard (`admin.html`) reads this stored feedback for review.

---

## 🚀 How to Run Locally

1. **Download** the repository or clone it:  
   ```bash
   git clone https://github.com/your-username/AkshayaMetrics.git
   ```
2. Place both files (`dashboard.html` and `admin.html`) in the same folder along with your logo image (`logo.png`).
3. Open `dashboard.html` in your browser.
4. Use the navigation bar to explore all pages.
5. Admin panel can be accessed via the “Admin” link → login with demo credentials:
   ```
   Username: admin
   Password: akshayahar
   ```

---

## 🎯 Features Summary

- Simple data logging interface  
- Interactive charts (Chart.js)  
- LocalStorage persistence  
- Report filtering and CSV export  
- Efficiency gauge visualization  
- Feedback storage and admin view  
- Fully responsive design  

---

## 🌍 Credits

Developed by:  
**Nupoor Mahajan**, **Aishwarya Thorat**, **Neha Raparti**, **Aryan Gajra**, and **Daksh Talla**  
as part of the **Community Engagement Programme (CEP)** at SAKEC.  
In collaboration with **AkshayaShakti Foundation** — *for the AkshayaAahaar initiative.*

---

## 🧠 Future Enhancements
- Integration with Google Sheets or Firebase for cloud sync  
- Role-based user authentication  
- Multi-center analytics dashboard  
- Real-time volunteer collaboration  
