# 🗄️ Superstore Database — SQLAlchemy ETL Project
 
A complete **ETL pipeline** that loads a cleaned Superstore CSV dataset into a normalized **PostgreSQL** database using **SQLAlchemy**, with analytical SQL views for business reporting.
 
---
 
## 📌 Overview
 
This project transforms a flat CSV file (`superstore_clean.csv`) into a fully normalized relational database with 5 tables and 4 analytical views — ready to power dashboards and BI tools.
 
---
 
## 🗂️ Project Structure
 
```
├── SQLALCHEMY_PROJECT.ipynb   # Full ETL pipeline (connection → create → load → views)
└── superstore_clean.csv       # Source dataset
```
 
---
 
## 🗃️ Database Schema
 
The data is normalized into **5 tables** with proper foreign key relationships:
 
```
locations
    └── customers (location_id → locations)
            └── orders (customer_id → customers)
                    └── order_details (order_id → orders)
                                      (product_id → products)
products
    └── order_details
```
 
| Table           | Key Columns                                                 |
|----------------|-------------------------------------------------------------|
| `locations`     | location_id, country, city, state, postal_code, region     |
| `customers`     | customer_id, customer_name, segment, location_id           |
| `products`      | product_id, product_name, category, sub_category, cost     |
| `orders`        | order_id, order_date, ship_date, ship_mode, delivery_delay |
| `order_details` | order_detail_id, sales, profit, profit_ratio               |
 
---
 
## 📊 SQL Views
 
Four analytical views are created for reporting:
 
| View | Description |
|------|-------------|
| `total_sales_per_product` | Total revenue ranked by product |
| `total_sales_per_region` | Total revenue ranked by region |
| `total_sales_per_category` | Total revenue ranked by category |
| `profit_moyen_par_client` | Average profit per customer |
 
---
 
## ⚙️ Setup & Installation
 
### 1. Clone the repository
 
```bash
git clone https://github.com/your-username/superstore-sqlalchemy.git
cd superstore-sqlalchemy
```
 
### 2. Install dependencies
 
```bash
pip install -r requirements.txt
```
 
**Required packages:**
```
pandas
sqlalchemy
psycopg2-binary
jupyter
```
 
### 3. Configure PostgreSQL
 
Make sure PostgreSQL is running and create the target database:
 
```sql
CREATE DATABASE superstore_db;
```
 
Then update the connection string in the notebook if needed:
 
```python
engine = create_engine("postgresql://your_user:your_password@localhost:5432/superstore_db")
```
 
### 4. Run the notebook
 
```bash
jupyter notebook SQLALCHEMY_PROJECT.ipynb
```
 
Execute cells in order — the notebook will:
1. Connect to PostgreSQL
2. Drop and recreate all tables
3. Load data from `superstore_clean.csv`
4. Create all analytical views
 
---
 
## 🔄 ETL Pipeline Steps
 
```
CSV File
   │
   ▼
Load with pandas
   │
   ▼
Extract & deduplicate each entity
(locations → customers → products → orders → order_details)
   │
   ▼
Insert into PostgreSQL via SQLAlchemy
   │
   ▼
Create analytical SQL Views
```
 
> **Note:** Tables are loaded in dependency order to respect foreign key constraints.
 
---
 
## 📁 Data Source
 
Based on the [Superstore Sales dataset](https://www.kaggle.com/datasets/vivek468/superstore-dataset-final) — a fictional US retail dataset commonly used for BI practice.
