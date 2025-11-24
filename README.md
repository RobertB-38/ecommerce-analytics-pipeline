# E-Commerce Customer Analytics Pipeline

**Course:** CSC1142 - Data Analytics  
**Institution:** Dublin City University  
**Technology:** Apache Spark (PySpark)  
**Dataset:** Olist Brazilian E-Commerce

---

## Project Overview

Scalable e-commerce customer analytics pipeline processing 96,478 orders from 93,358 customers using Apache Spark for distributed data processing, customer segmentation, and predictive analytics.

### Key Metrics
- **Total Revenue**: R$ 15.4M
- **Average Order Value**: R$ 159.83
- **Customer Satisfaction**: 4.16/5.0
- **On-time Delivery**: 91.9%

---

## Technology Stack

**Apache Spark 4.0.1** - Distributed data processing  
**PySpark** - Python API for Spark  
**Jupyter Notebook** - Interactive development  
**Parquet** - Columnar storage format

### Why Spark?

1. **Scalability**: Handles datasets from GB to PB
2. **Performance**: 10-100x faster than MapReduce
3. **Complex Joins**: Efficient multi-table operations on 7 normalized tables
4. **Window Functions**: RFM scoring across 93K customers
5. **Industry Standard**: Netflix, Uber, Airbnb production pipelines

---

## Dataset

**Source**: Olist Brazilian E-Commerce (Kaggle)  
**Size**: 550K+ records across 7 tables  
**Format**: CSV files (~150MB)

### Data Model
```
CUSTOMERS → ORDERS → ORDER_ITEMS → PRODUCTS
                ↓         ↓
            PAYMENTS   SELLERS
                ↓
            REVIEWS
```

---

## Pipeline Stages

### 1. Data Ingestion
- Load 7 CSV datasets into Spark DataFrames
- Schema validation
- Data quality checks

### 2. Data Cleaning
- Remove invalid records
- Handle missing values
- Aggregate multi-payment orders
- Calculate delivery metrics

### 3. Feature Engineering
**Temporal**: year, month, day_of_week, time_of_day  
**Customer**: total_orders, revenue, recency, lifetime_days  
**RFM Scores**: Recency (1-5), Frequency (1-5), Monetary (1-5)

### 4. Customer Segmentation
7 segments: Champions, Loyal, At Risk, Potential Loyalists, Cannot Lose Them, New, Lost

### 5. Advanced Analytics
- Customer Lifetime Value (CLV)
- Market Basket Analysis
- Churn Risk Scoring
- Geographic Analysis
- Seller Performance

---

## Project Structure

```
ecommerce-pipeline/
├── data/
│   ├── raw/                  # CSV files
│   └── processed/            # Parquet files
├── notebooks/
│   ├── 01_data_ingestion_exploration.ipynb
│   ├── 02_data_cleaning_transformation.ipynb
│   └── 03_advanced_analytics.ipynb
├── src/
│   └── ingestion/
├── outputs/
├── README.md
└── .gitignore
```

---

## Setup

### Prerequisites
- Python 3.8+
- Java 11+
- 4GB+ RAM

### Installation
```bash
pip install pyspark pandas matplotlib seaborn jupyter
```

### Download Dataset
https://www.kaggle.com/datasets/olistbr/brazilian-ecommerce

Place CSV files in `data/raw/`

---

## Usage

```bash
jupyter notebook
# Run notebooks in sequence:
# 1. 01_data_ingestion_exploration.ipynb
# 2. 02_data_cleaning_transformation.ipynb
# 3. 03_advanced_analytics.ipynb
```

---

## Key Results

### Customer Segments

| Segment | Count | Avg Revenue |
|---------|-------|-------------|
| Champions | 15,234 | R$ 342.50 |
| Loyal | 18,902 | R$ 285.20 |
| At Risk | 12,456 | R$ 198.40 |
| New | 19,847 | R$ 128.90 |

### Business Insights
- Top 10% customers = 60% revenue (Pareto)
- 8.1% late deliveries
- R$ 2.3M revenue at churn risk
- São Paulo: 42% of orders

---

## Challenges Solved

1. **Data Quality**: Filtered 2,963 orders with missing dates
2. **Payment Aggregation**: Handled multiple payment methods per order
3. **Performance**: Optimized joins from 3+ min to <1 min
4. **Customer ID**: Used customer_unique_id for accurate aggregation

---

## Author

**Robert Borkar**  
MSc Computing (Data Analytics)  
Dublin City University  
robert.borkar2@mail.dcu.ie
