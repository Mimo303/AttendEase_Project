# 🧠 AttendEase: A Web Application for Simplifying Attendance Tracking

### A simple, offline attendance management system for BCA colleges — built with zero dependencies.

No frameworks. No server. No database. Just open the file and use it.

---

## What it does

AttendEase lets a teacher manage student attendance entirely inside the browser. Everything — students, semesters, subjects, daily records — is stored in `localStorage` and persists between sessions automatically.

```
Add students → Add semesters → Add subjects → Mark attendance → View reports → Download CSV
```

That's the entire workflow. No login. No setup. No internet required after the first load.

---

## Live demo

> Download [`AttendEase.html`](./AttendEase.html), double-click it, done.

Works in Chrome, Firefox, Edge, and Safari. Tested on desktop and mobile.

---

## Features

| Feature | Details |
|---|---|
| 👤 Student management | Add / remove student names |
| 🎓 Semester management | Semester 1 through 6, add as many as needed |
| 📚 Subject management | Multiple subjects under each semester |
| ✅ Daily attendance | Mark each student Present or Absent per subject per date |
| 📅 Date picker | Defaults to today, any date selectable |
| 💾 Auto-save | Saves to `localStorage` on every Save click |
| 📊 Attendance view | Filter by semester, subject, and date with per-student % |
| ⬇ CSV export | Download a formatted attendance report as a `.csv` file |
| 📱 Responsive | Full mobile layout with tab-bar navigation |
| 🔁 Auto-load | All data reloads automatically every time you open the file |

---

## How to use it

**1. Download the file**
```
AttendEase.html
```
Keep it anywhere on your computer. No other files needed.

**2. Open it**
```
Double-click AttendEase.html  →  opens in your browser
```

**3. Set up your class**

- Go to **Students** → type a name → click Add
- Go to **Semesters** → pick from the dropdown → click Add
- Go to **Subjects** → choose a semester → type the subject → click Add

**4. Mark attendance**

- Select **Semester**, **Subject**, and **Date**
- Click ✅ Present or ❌ Absent for each student
- Click **Save Attendance** → green confirmation appears

**5. View and export**

- Go to **View Attendance** → select semester + subject → click View
- See per-day columns, totals, and percentage for every student
- Click **Download CSV** to export the table as a `.csv` file

---

## How data is stored

Everything lives in four `localStorage` keys in your browser:

```
students     →  ["Alice", "Bob", "Charlie"]

semesters    →  ["Semester 1", "Semester 2"]

subjects     →  {
                  "Semester 1": ["Mathematics", "C Programming"],
                  "Semester 2": ["DBMS", "Data Structures"]
                }

attendance   →  {
                  "Semester 1": {
                    "Mathematics": {
                      "2025-06-10": {
                        "Alice":   "Present",
                        "Bob":     "Absent",
                        "Charlie": "Present"
                      }
                    }
                  }
                }
```

Data is read once on page load (`DOMContentLoaded`) and written to localStorage every time you click **Save Attendance**.

```js
// save
localStorage.setItem("attendance", JSON.stringify(attendance));

// load
attendance = JSON.parse(localStorage.getItem("attendance")) || {};
```

Dates are stored as `YYYY-MM-DD` (ISO 8601) for easy sorting, displayed as `DD/MM/YYYY` in the UI.

---

## File structure

```
AttendEase.html        ← the entire project, single file
    ├── <style>        ← all CSS (CSS Grid layout, custom properties, responsive)
    └── <script>       ← all JavaScript (data logic, DOM, localStorage, CSV export)
```

No `node_modules`. No `package.json`. No build step.

---

## Technologies

- **HTML5** — structure and form elements
- **CSS3** — Grid, Flexbox, CSS custom properties, responsive design
- **JavaScript (ES6)** — DOM manipulation, event handling, data logic
- **Web Storage API** — `localStorage` for persistence
- **Blob API** — client-side CSV file generation and download
- **Google Fonts** — Syne (headings) + DM Sans (body) — loaded from CDN, optional

---

## Limitations

- Data is stored per-browser, per-device. It does not sync across devices.
- Clearing browser site data will erase all records — export CSV regularly as backup.
- Does not work in incognito/private mode (localStorage is blocked).
- No multi-user or login system.

---

## Project context

Built as a BCA college minor project demonstrating practical use of core web technologies covered in a standard curriculum — DOM manipulation, event-driven programming, client-side storage, responsive layout, and file export — without any external dependencies.

---

## License

Free to use, modify, and submit for educational purposes.

---

*Open the file. It just works.*


