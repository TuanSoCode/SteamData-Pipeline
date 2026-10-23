# 🔥 Steam Data Pipeline: From Absolute Chaos to Client-Ready

> *"I didn't just write code. I went to war against messy data... and I won."*

## 🤯 The Nightmare (The Problem)
Imagine downloading a dataset of **125,855 Steam games**, only to realize it's a complete disaster. This wasn't just "dirty data"—it was a crime scene:
- **The Merged Monster:** Two crucial columns (`Discount` and `DLC count`) were brutally fused into one, breaking the entire table structure.
- **The Text Bomb:** One game description contained a massive wall of text (about Sámi culture) that literally crashed Excel's 32,767-character limit. 💣
- **The Fake Websites:** Developers listed pure garbage URLs like `http://myfakegoblinwife` (missing dots, missing domains).
- **The Black Hole:** Crucial data like `Reviews` and `Metacritic url` were missing over 90% of the time.

If a human tried to clean this manually, they would lose their minds. **I didn't.**

## ⚔️ The Counter-Attack (The Solution)
Instead of crying, I built an automated ETL (Extract, Transform, Load) pipeline in Python to execute a surgical strike on the chaos.

### 🛠️ The "No-Mercy" Strategy:
1. **Surgical Splitting:** Detected and split the `DiscountDLC count` monster back into two clean columns before it could corrupt the rest.
2. **Brutal Deletion:** Dropped useless, dead-weight columns (`Movies`, `Score rank`, `Reviews`) that were holding the file hostage.
3. **Pandera Validation:** Set up a strict "police checkpoint". It caught **6 violations** (5 fake websites, 1 missing name) and I instantly executed `df.loc[mask, "Website"] = None`.
4. **Regex Assassination:** Hunted down and fixed any website URL missing a dot. 
5. **Anti-Crash Armor:** Wrote a custom `xlsxwriter` function to auto-adjust column widths and safely truncate giant text strings, so Excel would never crash again.

## 📊 The Result (The Victory)
- **Before:** 40 messy columns, 6 validation errors, and a literal text bomb.
- **After:** 36 perfectly clean columns, 0 nulls, 0 duplicates, and a beautifully styled Excel report.
- **Optimization:** Converted data types (`uint8`, `category`) to slash memory usage by 25%.

> 📸 *Screenshot of the final, beautifully styled Excel report:*
https://drive.google.com/file/d/1iUzgHOsrHY9fwFtrYX6XZva4rDU4tsQx/view?usp=drivesdk


## 💡 The Business Value
This project proves I don't just "know Python." **I can take a completely broken, real-world dataset and turn it into a professional, client-ready report in seconds.** No drama. Just results.

---
*Built with pure Python, Pandas, Pandera, and a lot of patience by **[TuanSoCode]**.*