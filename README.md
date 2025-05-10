

## 🏠 HomeEasyTask Project Overview

This project is a Flask-based backend service integrated with a Hugging Face transformer model (BART) to analyze sales performance data. It's designed for easy deployment (e.g., using Google Colab + ngrok) and provides endpoints to upload sales data and generate AI-powered feedback.

---

### 🔧 Technologies Used

* **Flask**: Lightweight web framework for serving APIs.
* **Pandas**: For data ingestion and processing.
* **Transformers (Hugging Face)**: Used for summarization/analysis (e.g., `facebook/bart-large-cnn` model).
* **Ngrok**: To expose the Flask app publicly for testing (especially in Colab).

---

### 📁 Key Functionalities

#### 1. **Upload Sales Data**

```http
POST /upload
```

* Accepts `.csv` or `.json` files.
* Saves uploaded content as `sales_data.json` for downstream analysis.

---

#### 2. **Individual Performance Analysis**

```http
GET /api/rep_performance?rep_id=123
```

* Fetches individual data by `employee_id`.
* Formats it for readability.
* Passes it to the LLM with a custom prompt for performance review.

---

#### 3. **Team Performance Summary**

```http
GET /api/team_performance
```

* Aggregates team metrics: total revenue, tours booked, and average close rate.
* Sends to LLM for an executive-level summary.

---

#### 4. **Performance Trends Over Time**

```http
GET /api/performance_trends?time_period=monthly
```

* Supported values: `monthly`, `quarterly`, `yearly`.
* Groups data by the selected period and summarizes it.
* Returns trend data as JSON (not LLM-interpreted in current form).

---

#### 5. **Named Employee Feedback**

```http
GET /individual/<name>
```

* Fetches and formats data for an employee by name.
* Sends it to LLM for natural-language feedback.

---

### 🧠 LLM Integration

The Hugging Face summarization model (`facebook/bart-large-cnn`) is used to generate:

* Executive summaries
* Personalized insights
* Trend observations

It receives prompts like:

> "You are an expert sales analyst. Based on the following sales data, provide feedback on individual performance..."

---

### 🚀 Deployment Notes

* `ngrok.connect(5000)` is used to expose the app in Colab.
* App listens on port `5000`.
* Ngrok public URL is printed for testing.

---


![t5](https://github.com/user-attachments/assets/a0f7329d-6718-4b79-9651-f4c63871967f)
![t1](https://github.com/user-attachments/assets/0ffc8f94-1b73-4497-9359-61986df1816a)
![t2](https://github.com/user-attachments/assets/8f234b22-aa0a-48db-907d-2638f87c8c4b)
![t4](https://github.com/user-attachments/assets/40a51ef3-fd26-448f-a9f6-b46e35c4d03c)
![t3](https://github.com/user-attachments/assets/083803bb-f17d-4567-82c5-3ceb5e93d022)
