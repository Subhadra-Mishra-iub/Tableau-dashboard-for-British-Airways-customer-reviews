# ✈️ British Airways Reviews Dashboard

This Tableau dashboard visualizes British Airways customer review data from 2016–2023, showcasing insights into service categories such as food, staff, comfort, and value.

🔗 [View the Published Dashboard](https://public.tableau.com/views/BritishAirwaysReviews_17533092418760/Dashboard1)

## 📊 Key Features
- Trend analysis by month
- Country-wise average ratings (Map)
- Aircraft-specific customer ratings and review count
- Filterable by seat type, continent, aircraft group, and traveler type

## ✅ Built With
- Tableau Public
- Data source: `ba_reviews.csv` (from YouTube tutorial [here](https://www.youtube.com/watch?v=KlAKAarfLRQ))

---

## 🧩 Step-by-Step Build Guide

### 1. Data Import
- Open Tableau Public Desktop.
- Connect to the provided .csv file: `ba_reviews.csv`.
- Tableau automatically detects the headers and assigns data types.

### 2. Key Dimensions & Measures Used
**Dimensions:**
- Date
- Aircraft (group)
- Traveller Type
- Seat Type
- Continent
- Country

**Measures:**
- Rating
- Cabin Staff Service
- Entertainment
- Food Beverages
- Ground Service
- Seat Comfort
- Value For Money

### 3. Create Key Visualizations
#### a. Summary Score Tiles (Sheet: summary)
- Drag Measure Names to Columns.
- Drag Measure Values to Text on the Marks card.
- Filter Measure Names to include: Rating, Cabin Staff Service, Entertainment, etc.
- Customize text: Set <Measure Values> on top and <Measure Names> below in the text box.
- Adjust font size and alignment to center.
- **Customization:** Used red background and made this row visually pop.

#### b. Line Chart – Rating Trend by Month (Sheet: Month)
- Drag Date to Columns → change to Month.
- Drag Rating to Rows (AVG aggregation).
- Customize line color (magenta).
- Add filters: Traveller Type, Seat Type, Aircraft (group), Continent.

#### c. Map – Average Rating by Country (Sheet: Map)
- Drag Country to Detail (Tableau assigns geographic role).
- Drag Rating to Color (AVG aggregation).
- Customize color scale (light to dark red).
- Add necessary filters.

#### d. Bar Charts – Ratings by Aircraft (Sheet: Aircraft)
- Drag Aircraft (group) to Rows.
- Drag Rating to Columns (AVG aggregation).
- Add Number of Records or COUNT(Rating) to a dual-axis bar (secondary chart).
- Format as: Left bars (Ratings), Right bars (Count of reviews).
- Customize bar color (teal + blue).

### 4. Calculated Field (Optional)
```tableau
IF [Rating] >= 4 THEN "High" ELSE "Low" END
```
To classify sentiment or filter.

### 5. Build Dashboard
- Go to Dashboard → New Dashboard.
- Set Size: 1200 x 800 (or responsive).
- Add sheets: summary at top (KPI tiles), Month, Map, and Aircraft below in grid layout.
- Add filters: Drag filter fields from one sheet → apply to all using: Right-click filter → Apply to Worksheets → All Using This Data Source.

---

## 🛠️ Metrics, Parameters, and Calculated Fields – How I Built Them

### 1. Creating Metrics (Measure Values)
- **Purpose:** Display KPIs like Average Rating, Cabin Staff Service, Entertainment, etc., as summary tiles.
- **Steps:**
  1. Go to a new worksheet (e.g., `summary`).
  2. Drag **Measure Names** to Columns.
  3. Drag **Measure Values** to Text on the Marks card.
  4. Click the filter on Measure Names and select only the metrics you want (e.g., `Rating`, `Cabin Staff Service`, `Entertainment`, etc.).
  5. Edit the text on the Marks card to show the value above and the metric name below.
  6. Format: Center-align, increase font size, and set background color (red, in your case).

### 2. Creating Parameters
- **Purpose:** Allow dynamic user input or control over the dashboard (e.g., to switch between metrics or set a threshold).
- **Steps:**
  1. Right-click in the Data pane and select **Create Parameter**.
  2. Name your parameter (e.g., `Select Metric` or `Rating Threshold`).
  3. Set the data type (e.g., Integer, Float, String).
  4. For a metric selector, provide a list of metric names as values.
  5. Show Parameter Control on the worksheet/dashboard for user interaction.

**Example: Metric Selector Parameter**
- **Name:** `Select Metric`
- **Data Type:** String
- **Allowable Values:** List
- **List of Values:** Rating, Cabin Staff Service, Entertainment, etc.

### 3. Creating Calculated Fields
- **Purpose:** Derive new insights, classify data, or create custom logic.
- **Steps:**
  1. Right-click in the Data pane and select **Create Calculated Field**.
  2. Name your field (e.g., `Rating Sentiment`).
  3. Enter your formula.

**Example: Rating Sentiment Calculated Field**
```tableau
IF [Rating] >= 4 THEN "High" ELSE "Low" END
```
- **Usage:** Drag this field to Color or Filters to segment reviews by sentiment.

**Example: Dynamic Metric Display (using Parameter)**
```tableau
CASE [Select Metric]
  WHEN "Rating" THEN [Rating]
  WHEN "Cabin Staff Service" THEN [Cabin Staff Service]
  WHEN "Entertainment" THEN [Entertainment]
  // Add more as needed
END
```
- **Usage:** Use this calculated field in your visualizations to dynamically display the selected metric.

### 4. Applying Calculated Fields and Parameters
- Drag your calculated field (e.g., `Rating Sentiment`) to Color, Filters, or Rows/Columns as needed.
- Use the parameter control to let users switch between metrics or set thresholds.
- Combine parameters and calculated fields for interactive dashboards.

---

## 🎓 Credits
- Dataset and original layout inspired by: [YouTube Tableau Tutorial – British Airways Reviews](https://www.youtube.com/watch?v=KlAKAarfLRQ)
- Customization, analysis, and dashboard design by: Subhadra Mishra

---

## 📚 My Learning & Reflections
- Gained hands-on experience with Tableau’s calculated fields, filters, and dashboard layout.
- Practiced customizing color schemes and interactivity for business storytelling.
- Understood the importance of clear KPI tiles and filterable visualizations for end-users.
- Improved skills in data cleaning, aggregation, and visual best practices.

---

*For questions or feedback, feel free to connect!* 