# 📊 Sales Analysis Tableau Dashboard

A **Tableau-based data visualization project** that analyzes sales performance across products, categories, locations, and sales representatives. Built using multiple connected data sources, this workbook provides interactive visual insights into revenue, profit, units sold, and geographic sales distribution.

---

## 📁 Project Files

| File | Description |
|------|-------------|
| `Book1.twb` | Tableau workbook file with all dashboards and visualizations |
| `Sales Data.csv` | Core sales transactions data |
| `Product.csv` | Product details — name, color, pricing |
| `Categories.xlsx` | Product category master data |
| `SubCategories.xlsx` | Product sub-category master data |
| `Geography.xlsx` | Location data — country and town |
| `SalesRep.xlsx` | Sales representative names |

---

## 🗄️ Data Model

The workbook uses a **multi-source federated connection**, joining 6 data sources:

```
Sales Data.csv  (fact table)
    ├── Product.csv          → via ProductID
    ├── SalesRep.xlsx        → via SalesRepID
    ├── Geography.xlsx       → via Location
    ├── SubCategories.xlsx   → via Sub Category Key
    └── Categories.xlsx      → via CategoryKey
```

---

## 📋 Data Source Details

### `Sales Data.csv` — Fact Table
| Column | Type | Description |
|--------|------|-------------|
| `fSalesPrimaryKey` | Integer | Unique transaction ID |
| `ProductID` | Integer | FK → Product |
| `SalesRepID` | Integer | FK → Sales Rep |
| `Location` | String | Sale location |
| `Date` | Date | Transaction date |
| `Units` | Integer | Units sold |
| `PercentOfStandardCost` | Decimal | Cost percentage |
| `RevenueDiscount` | Decimal | Discount applied |

### `Product.csv`
| Column | Description |
|--------|-------------|
| `ProductID` | Unique product identifier |
| `ProductName` | Name of the product |
| `Color` | Product color |
| `RetailPrice` | Selling price |
| `StandardCost` | Cost price |
| `Sub Category Key` | FK → SubCategories |

### `Geography.xlsx`
| Column | Description |
|--------|-------------|
| `Country` | Country name |
| `Town` | Town/city name |
| `Wikipedia` | Reference link |

### `SalesRep.xlsx`
| Column | Description |
|--------|-------------|
| `SalesRepID` | Unique rep identifier |
| `Sales Rep Name` | Full name of sales rep |

### `Categories.xlsx` & `SubCategories.xlsx`
| Column | Description |
|--------|-------------|
| `CategoryKey` | Unique category ID |
| `Category` | Category name |
| `SubCategoryKey` | Unique sub-category ID |
| `SubCategory Name` | Sub-category name |

---

## 📐 Calculated Fields

| Field | Formula | Purpose |
|-------|---------|---------|
| `Profit` | `SUM([RetailPrice]) + SUM([Units])` | Calculates profit metric |
| `Location - Split 1` | `TRIM(SPLIT([Location], ";", 1))` | Cleans location field for mapping |

---

## 📊 Dashboard & Sheets

| Sheet | Description |
|-------|-------------|
| Sheet 1 | Primary sales visualization |
| Sheet 2 | Secondary analysis view |

---

## 🛠️ Tools & Technologies

| Tool | Purpose |
|------|---------|
| Tableau Desktop 2025.3 | Dashboard creation and visualization |
| CSV / Excel | Raw data sources |
| Federated Data Connection | Joining multiple data sources in Tableau |

---

## 🔍 Key Metrics Analyzed

- **Total Revenue** — based on Retail Price × Units sold
- **Profit** — Revenue minus Standard Cost
- **Units Sold** — Volume of products sold per period
- **Revenue Discount** — Discount impact on sales
- **Geographic Performance** — Sales by Country and Town
- **Sales Rep Performance** — Individual rep contribution
- **Category & Sub-Category** — Product-level breakdown

---

## 🚀 How to Open

1. Install **Tableau Desktop** (version 2025.3 or compatible).
2. Place all data files in the same folder:
   ```
   Sales-Analysis-Tableau-Dashboard/
   ├── Book1.twb
   ├── Sales Data.csv
   ├── Product.csv
   ├── Categories.xlsx
   ├── SubCategories.xlsx
   ├── Geography.xlsx
   └── SalesRep.xlsx
   ```
3. Open `Book1.twb` in Tableau Desktop.
4. If prompted, re-map data source paths to your local folder.
5. All sheets and dashboards will load with live data.

> 💡 **Tip:** To avoid re-mapping, keep all files in `C:/Tablue new project/` as in the original setup, or update the data source connections via **Data → Edit Data Source**.

---

## 👤 Author

**Tejas**
Data Visualization Project — Sales Analysis Dashboard using Tableau
