
# 📄 Automated AWS Instance Health Classification & Reporting System

---

## 1. 📌 Problem Statement

The organization operates approximately **2000 AWS EC2 instances** across its infrastructure. At the end of each month, a report is required to assess the health of these instances based on resource utilization metrics such as CPU, memory, and other performance indicators.

### Current Workflow:

* Data is exported from ServiceNow into an Excel/CSV file
* The manager manually:

  * Reviews utilization metrics
  * Classifies instances into:

    * 🟢 Green (Optimal usage)
    * 🟡 Amber (Moderate usage)
    * 🔴 Red (High/critical usage)

### Key Challenges:

* Manual effort leads to **significant time consumption**
* High risk of **inconsistent classification**
* Process is **not scalable** for growing infrastructure
* Lack of **automation and standardization**
* No **quick insights or summary reporting**

---

## 2. 🎯 Objective

To build an **automated, scalable, and reliable system** that:

* Accepts input files (ServiceNow export)
* Processes and cleans data automatically
* Classifies instances into Green, Amber, and Red categories
* Generates a structured Excel report with:

  * Detailed classification
  * Summary statistics
  * Actionable insights
* Minimizes manual intervention

---

## 3. 🧠 Solution Overview

The proposed solution is a **serverless, event-driven data processing pipeline** built on AWS.

### High-Level Flow:

1. User uploads file
2. File is automatically processed
3. Instances are classified using predefined rules
4. Output report is generated and shared

---

## 4. 🏗️ Proposed Architecture

### Core AWS Services Used:

* Amazon S3 → File storage (input & output)
* AWS Lambda → Processing engine
* Amazon SNS → Notification system (optional)
* Amazon CloudWatch → Logging & monitoring

---

### Workflow:

1. **File Upload**

   * User uploads ServiceNow export file to S3

2. **Trigger**

   * S3 event triggers Lambda function

3. **Processing**

   * Lambda reads file
   * Cleans and validates data
   * Applies classification logic

4. **Output Generation**

   * Processed Excel file generated
   * Stored back in S3

5. **Notification (Optional)**

   * Email notification sent to stakeholders

---

## 5. ⚙️ Classification Logic

The classification is based on predefined thresholds.

### Example Logic (Customizable):

| Category | CPU Usage | Memory Usage |
| -------- | --------- | ------------ |
| 🟢 Green | < 50%     | < 60%        |
| 🟡 Amber | 50–75%    | 60–80%       |
| 🔴 Red   | > 75%     | > 80%        |

> Note: Thresholds can be configured based on business requirements.

---

## 6. 📊 Output Report Structure

The generated Excel report will contain:

### Sheet 1: Detailed Report

* Instance ID
* CPU Utilization
* Memory Utilization
* Classification (Green/Amber/Red)

### Sheet 2: Summary Report

* Total instances
* Count of:

  * Green
  * Amber
  * Red

### Sheet 3: Insights (Optional)

* High-risk instances
* Underutilized instances
* Recommendations

---

## 7. 🔄 Data Processing Flow

### Steps Performed:

1. File ingestion
2. Data validation (missing/null checks)
3. Data cleaning
4. Rule-based classification
5. Aggregation
6. Report generation

---

## 8. 🚀 Benefits

### Business Benefits:

* ⏱️ Reduces manual effort by **90%+**
* 📉 Minimizes human error
* 📊 Provides consistent and standardized reports
* ⚡ Faster decision-making

### Technical Benefits:

* Scalable (handles thousands of instances)
* Serverless → no infrastructure management
* Cost-efficient (pay-per-use)
* Easily extensible

---

## 9. 🔒 Security & Compliance

* Data stored securely in Amazon S3 with access control
* IAM roles for secure access to AWS Lambda
* Logging and monitoring via Amazon CloudWatch
* Encryption (optional):

  * S3 encryption
  * Data in transit (HTTPS)

---

## 10. 📈 Future Enhancements

### Phase 2 Enhancements:

* Dashboard integration using Amazon QuickSight
* Historical trend analysis
* Cost optimization insights
* Auto-scaling recommendations
* Integration with Slack/Email alerts

---

## 11. 🤖 Optional GenAI Enhancement

Using Amazon Bedrock:

* Generate natural language summaries:

  * “30% of instances are over-utilized”
* Provide recommendations
* Convert technical reports into business insights

---

## 12. 🧪 Implementation Plan

### Phase 1 (Core Automation)

* Define classification rules
* Develop Lambda processing script
* Configure S3 triggers
* Generate Excel output

### Phase 2 (Enhancements)

* Notifications
* Dashboard integration
* GenAI insights

---

## 13. 🎯 Conclusion

This solution transforms a **manual, error-prone reporting process** into a **fully automated, scalable, and intelligent system**.

It ensures:

* Consistency
* Efficiency
* Faster insights
* Better infrastructure management

