# SQL_Music-Store-Analysis
Analysis of music store with sql
# 🎶 Music Store Data Analysis (SQL Project)

## 📌 Project Overview
This project analyzes a **Music Store Database** using SQL to extract meaningful business insights.  
The dataset is based on a typical music store schema (similar to the Chinook database), containing information about **customers, invoices, employees, tracks, albums, artists, and genres**.  

The goal is to practice **SQL queries for data analysis** and showcase how SQL can answer real-world business questions.

---

## 📂 Database Schema
The database includes the following key tables:

- **Customer** → customer_id, first_name, last_name, country, email  
- **Invoice** → invoice_id, customer_id, invoice_date, total  
- **InvoiceLine** → invoice_line_id, invoice_id, track_id, unit_price, quantity  
- **Track** → track_id, name, album_id, genre_id, composer, milliseconds  
- **Album** → album_id, title, artist_id  
- **Artist** → artist_id, name  
- **Employee** → employee_id, first_name, last_name, title, reports_to  
- **Genre** → genre_id, name  
- **MediaType** → media_type_id, name  

---

## 📊 Key Business Questions Answered
1. **Sales & Revenue**
   - Which countries generate the most revenue?
   - What are the top 5 customers by spending?

2. **Music Trends**
   - Who are the top-selling artists?
   - Which are the most popular genres?

3. **Customer Insights**
   - Which customers purchase the most tracks?
   - Which countries have the most customers?

4. **Employee Performance**
   - Which sales representatives bring in the most revenue?

---

## 📝 Sample Queries

### 🔹 Top 5 Countries by Total Revenue
```sql
SELECT c.country, SUM(i.total) AS total_revenue
FROM Invoice i
JOIN Customer c ON i.customer_id = c.customer_id
GROUP BY c.country
ORDER BY total_revenue DESC
LIMIT 5;

