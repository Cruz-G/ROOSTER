# 🐓 ROOSTER – Rule-Based Employee Roster Prediction System

A modular, rule-based Python solution for generating smart employee rosters from historical booking data. This system analyzes each employee’s weekday-wise booking patterns, accounts for weekends and holidays, enforces attendance constraints, and outputs a predictive Excel roster for any future month.

> 🔄 A model-based (ML) variant also exists — ideal for more complex, adaptive predictions. This repo focuses on the **rule-based logic** version for transparency, speed, and control.

---

## 🚀 Features

- 📂 Cleans and reshapes Excel rosters into a usable long format  
- 📊 Calculates attendance frequency per weekday per employee  
- 📆 Excludes weekends and uploaded holiday calendars  
- 🔁 Predicts future bookings using customizable rule thresholds  
- ✅ Enforces at least 3 bookings per week  
- 📤 Outputs formatted Excel files with `'Y'` marked bookings  

---

## 🧩 Modules

| Module | Description |
|--------|-------------|
| `clean_roster_excel()` | Parses raw Excel rosters into structured format with dates & weekdays |
| `get_working_days()` | Generates a work calendar, excluding weekends and location-specific holidays |
| `generate_booking_predictions()` | Applies rule-based logic using past behavior + attendance constraints |
| `apply_predictions_to_template()` | Marks `'Y'` in a formatted Excel template based on prediction output |

---

## 🧠 Use Cases

- Hybrid or on-site work policy automation  
- HR/Operations scheduling workflows  
- Attendance-based performance estimation  
- Forecasting staff presence without complex ML models

---

## 📦 Example Workflow

```python
# Step 1: Clean historical Excel file
df_cleaned = clean_roster_excel("Roster_June.xlsx")

# Step 2: Generate valid workdays for target month
working_days = get_working_days(month=7, year=2025, holiday_file="India_Holidays_2025.xlsx")

# Step 3: Apply rule-based prediction
predicted_df = generate_booking_predictions(df_cleaned, working_days)

# Step 4: Inject predictions into Excel template
apply_predictions_to_template(predicted_df, "Blank_Template.xlsx", "Final_Roster_July.xlsx")
