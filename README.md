# Lab: AWS Cost Explorer and Cost Optimization

There wwasn't any fees charged to my account. I and the Mr. Instructor suspect it might be due to the fact that my account is in free trial. I had a thourought check on this lab and did my best to practice it as if I wasn't on the free trial. I believe I now have enough knowledge on cost optimization.




**Estimated Time:** 90 minutes  
**Difficulty:** Intermediate  
**Prerequisites:** Cost Estimation lab completed, AWS account with billing access

## Learning Objectives

By the end of this lab, you will be able to:
- Navigate and use AWS Cost Explorer effectively
- Analyze spending trends and patterns
- Identify cost optimization opportunities
- Use Cost Explorer filters and groupings
- Create custom cost reports
- Set up Cost Anomaly Detection
- Implement cost allocation tags
- Generate cost optimization recommendations
- Present cost analysis to stakeholders

## Scenario

Your manager has noticed AWS costs are trending upward. You're tasked with:
1. Analyzing current spending to understand where money goes
2. Identifying services and resources driving costs
3. Finding cost optimization opportunities
4. Creating a monthly cost review process
5. Implementing cost allocation tags for better tracking
6. Setting up anomaly detection to catch unexpected spikes

## Lab Overview

You will:
1. Enable and configure Cost Explorer
2. Analyze historical spending data
3. Create custom cost reports
4. Use advanced filters and groupings
5. Implement cost allocation tags
6. Set up Cost Anomaly Detection
7. Identify optimization opportunities
8. Create a cost optimization action plan

## Prerequisites

- AWS Account (preferably with some usage history)
- IAM user with billing access or root account
- Completed Cost Estimation lab
- Basic understanding of AWS services

---

## Part 1: Enable and Configure Cost Explorer

### Step 1: Enable Cost Explorer

Cost Explorer requires one-time setup.

**Steps:**
1. Log into AWS Console
2. Click account name (top right) → **Billing and Cost Management**
3. In left menu, click **Cost Explorer**
4. If first time: Click **Enable Cost Explorer**
   - Note: Takes 24 hours to populate with data
5. Wait for data to load (if already enabled, data appears immediately)

**📸 Screenshot 1:** Cost Explorer dashboard

**📋 Note:** If your account is new with no usage history, some charts may be empty. That's okay - practice with the interface and filters.

---

## Part 2: Analyze Historical Spending

### Step 2: View Monthly Cost Trends

Understand your spending over time.

**Steps:**
1. In Cost Explorer, ensure you're on the **Cost and Usage** view
2. Set date range: **Last 6 months**
3. Granularity: **Monthly**
4. Group by: **Service**
5. Review the chart and table

**Analysis Questions:**
- What's your average monthly spend?
- Which month had the highest cost?
- What caused the spike (if any)?

**📸 Screenshot 2:** 6-month cost trend

**📋 Record in solution file:**
- Total spend (last 6 months): $__________
- Average monthly: $__________
- Highest month: __________, $__________

### Step 3: Daily Cost Analysis

Identify daily spending patterns.

**Steps:**
1. Change date range: **Last 30 days**
2. Granularity: **Daily**
3. Group by: **Service**
4. Observe daily patterns

**Look for:**
- Consistent daily costs (predictable workloads)
- Spikes on specific days
- Weekend vs. weekday differences

**📸 Screenshot 3:** Daily cost analysis

**📋 Observations:**
```
_____________________________________________________________
_____________________________________________________________
_____________________________________________________________
```

---

## Part 3: Service-Level Cost Analysis

### Step 4: Identify Top Cost Drivers

Find which services cost the most.

**Steps:**
1. Date range: **Last month**
2. Granularity: **Monthly**
3. Group by: **Service**
4. In the table below chart, sort by **Cost** (descending)

**Top 5 Services:**
1. __________________: $__________
2. __________________: $__________
3. __________________: $__________
4. __________________: $__________
5. __________________: $__________

**📸 Screenshot 4:** Top services by cost

### Step 5: Drill Down into EC2 Costs

Analyze compute costs in detail.

**Steps:**
1. Click **Filters** dropdown
2. Add filter: **Service** → Select **EC2-Instances (Elastic Compute Cloud - Compute)**
3. Group by: **Instance Type**
4. Review which instance types cost most

**Further drill-down:**
- Group by: **Usage Type**
- Look for:
  - On-Demand instances
  - Reserved Instances
  - Data transfer costs

**📸 Screenshot 5:** EC2 cost breakdown

**📋 EC2 Insights:**
```
Most expensive instance type: ________X___________________
Total EC2 cost last month: $__________0_________________
Percentage of total bill: _______X_%
```

### Step 6: Analyze S3 Storage Costs

Review storage and data transfer costs.

**Steps:**
1. Clear previous filters
2. Add filter: **Service** → Select **S3 (Simple Storage Service)**
3. Group by: **Usage Type**
4. Review breakdown:
   - Storage costs (GB-Month)
   - Request costs (PUT, GET, etc.)
   - Data transfer costs

**📸 Screenshot 6:** S3 cost breakdown

**📋 S3 Analysis:**
```
Total S3 cost: $______________0_____________
Storage cost: $________________0___________
Request cost: $_________________0__________
Data transfer cost: $____________0_______________
```

---

## Part 4: Advanced Filtering and Grouping

### Step 7: Filter by Region

Identify regional cost distribution.

**Steps:**
1. Remove service filters
2. Group by: **Region**
3. Date range: **Last 3 months**
4. Granularity: **Monthly**

**📸 Screenshot 7:** Cost by region

**📋 Regional Analysis:**
```
Most expensive region: ___X________________________
Cost: $___________0________________

Are you using resources in regions you don't need?
___________________________________________________________
```

### Step 8: Filter by Tag (if available)

Tags enable cost allocation tracking.

**Steps:**
1. Click **Group by** → **Tag**
2. If you have tags:
   - Select tag key (e.g., Environment, Project, Team)
   - Review cost breakdown by tag value
3. If no tags exist yet, skip to Step 9 where we'll create them

**📸 Screenshot 8:** Cost by tag (if applicable)

**📋 Note:** If no tags exist, write "No tags implemented yet" in solution.

---

## Part 5: Implement Cost Allocation Tags

### Step 9: Activate Cost Allocation Tags

Enable tags for cost tracking.

**Steps:**
1. In Billing Dashboard, click **Cost Allocation Tags** (left menu)
2. You'll see two sections:
   - **AWS-Generated Tags** (automatically created by AWS)
   - **User-Defined Tags** (tags you create)
3. In AWS-Generated Tags section, activate:
   - ☑ `aws:createdBy`
   - ☑ `aws:cloudformation:stack-name`
4. Click **Activate**
5. Note: Tags take 24 hours to appear in Cost Explorer

**📸 Screenshot 9:** Activated cost allocation tags
<img width="1280" height="831" alt="image" src="https://github.com/user-attachments/assets/a45aad94-d24a-434b-a95b-621fcde9dcae" />
<img width="1280" height="831" alt="image" src="https://github.com/user-attachments/assets/a45aad94-d24a-434b-a95b-621fcde9dcae" />


### Step 10: Create User-Defined Tags

Plan your tagging strategy.

**Recommended tags:**
- **Environment:** (production, staging, development)
- **Project:** (project name or code)
- **Team:** (team or department name)
- **CostCenter:** (for chargeback)
- **Owner:** (responsible person/email)

**Steps:**
1. Go to **EC2** service (or any resource)
2. Select a resource (instance, volume, etc.)
3. Click **Tags** tab
4. Click **Manage tags**
5. Add tags:
   - Key: `Environment`, Value: `production`
   - Key: `Project`, Value: `web-app`
   - Key: `Team`, Value: `engineering`
6. Click **Save**

**📸 Screenshot 10:** Tagged EC2 resource

**📋 Tagging Plan:**
```
Tag 1: Key: _________________, Values: _____________________
Tag 2: Key: _________________, Values: _____________________
Tag 3: Key: _________________, Values: _____________________

How will these tags help with cost management?
___________________________________________________________
___________________________________________________________
```

**Note:** After activating in Cost Allocation Tags settings, they'll appear in Cost Explorer within 24 hours.

---

## Part 6: Create Custom Cost Reports

### Step 11: Save Custom Report

Create a reusable report for monthly reviews.

**Steps:**
1. In Cost Explorer, configure your desired view:
   - Date range: **Last 3 months**
   - Granularity: **Monthly**
   - Group by: **Service**
   - Chart type: **Bar chart**
2. Click **Save as...** (top right)
3. Name: `Monthly Service Cost Report`
4. Click **Save report**
5. Access saved reports: Left menu → **Reports**

**📸 Screenshot 11:** Saved custom report

### Step 12: Create Top Services Report

Make a report showing your biggest cost drivers.

**Configure:**
- Date range: **Last month**
- Granularity: **Monthly**
- Group by: **Service**
- Show: **Top 10 services**
- Chart: **Pie chart**

**Save as:** `Top 10 Services by Cost`

**📸 Screenshot 12:** Top services pie chart

### Step 13: Daily Cost Monitoring Report

For daily cost tracking.

**Configure:**
- Date range: **Last 7 days**
- Granularity: **Daily**
- Group by: **Service**
- Filters: Include only services you actively monitor

**Save as:** `Daily Cost Monitor - Last 7 Days`

**📸 Screenshot 13:** Daily monitoring report

---

## Part 7: Cost Anomaly Detection

### Step 14: Enable Cost Anomaly Detection

Get automatic alerts for unusual spending.

**Steps:**
1. In Billing Dashboard, click **Cost Anomaly Detection** (left menu)
2. Click **Create monitor**
3. Configure monitor:
   - **Monitor type:** Choose **AWS Services**
   - **Monitor name:** `All Services Cost Monitor`
4. Click **Next**
5. Set alert preferences:
   - **Alert frequency:** Immediately
   - **Threshold:** $10 (or appropriate for your usage)
   - **SNS topic:** Create new → `cost-anomaly-alerts`
   - **Email:** your-email@example.com
6. Click **Create monitor**
7. **Confirm SNS subscription** in your email

**📸 Screenshot 14:** Cost Anomaly Detection monitor created

### Step 15: Create Service-Specific Monitor

Monitor specific high-cost services.

**Steps:**
1. Click **Create monitor** again
2. Choose **Individual services**
3. Select services: EC2, S3, RDS (or your top services)
4. Name: `High-Cost Services Monitor`
5. Configure same alert settings as Step 14
6. Create monitor

**📸 Screenshot 15:** Service-specific anomaly monitor

---

## Part 8: Identify Optimization Opportunities

### Step 16: Review AWS Cost Optimization Recommendations

Use built-in recommendations.

**Steps:**
1. Go to **Cost Explorer** → **Recommendations** (left menu)
2. Or go to **AWS Compute Optimizer** service
3. Review recommendations for:
   - Right-sizing EC2 instances
   - Deleting unused resources
   - Reserved Instance purchases
   - Savings Plans opportunities

**📸 Screenshot 16:** Cost optimization recommendations

**📋 Top 3 Recommendations:**
1. __________________________________________________________
   Potential savings: $__________/month

2. __________________________________________________________
   Potential savings: $__________/month

3. __________________________________________________________
   Potential savings: $__________/month

### Step 17: Identify Idle Resources

Find resources that aren't being used.

**Manual checks:**

**EC2 Instances:**
```bash
# List all instances with low CPU utilization
# (Check CloudWatch metrics via Console)
```

**EBS Volumes:**
```bash
# List unattached EBS volumes
aws ec2 describe-volumes \
  --filters Name=status,Values=available \
  --query 'Volumes[*].[VolumeId,Size,VolumeType]' \
  --output table
```

**Elastic IPs:**
```bash
# List unassociated Elastic IPs (costs money!)
aws ec2 describe-addresses \
  --query 'Addresses[?AssociationId==null].[PublicIp,AllocationId]' \
  --output table
```

**📋 Idle Resources Found:**
```
Unattached EBS volumes: _____ (Total size: _____ GB)
Unassociated Elastic IPs: _____
Stopped EC2 instances (still incurring EBS costs): _____
```

**📸 Screenshot 17:** Idle resources list

### Step 18: Calculate Reserved Instance Savings

Estimate savings with Reserved Instances.

**Steps:**
1. Review your EC2 usage in Cost Explorer
2. Identify consistently running instances
3. Visit **Reserved Instances** → **Purchase Reserved Instances** (do NOT actually purchase)
4. Compare pricing:
   - On-Demand: $__________/month
   - 1-Year RI (no upfront): $__________/month
   - Savings: __________% 

**📋 RI Opportunity Analysis:**
```
Current On-Demand spend (EC2): $___________/month
Potential with 1-Year RI: $___________/month
Annual savings: $___________
Break-even point: _______ months
```

---

## Part 9: Create Cost Optimization Action Plan

### Step 19: Summarize Findings

Compile your analysis into actionable items.

**📋 Complete in solution file:**

**Current State:**
- Monthly average spend: $__________
- Top 3 cost drivers: __________, __________, __________
- Cost trend: ☐ Increasing ☐ Stable ☐ Decreasing

**Quick Wins (Immediate actions):**
1. __________________________________________________________
2. __________________________________________________________
3. __________________________________________________________

**Short-term (1-3 months):**
1. __________________________________________________________
2. __________________________________________________________
3. __________________________________________________________

**Long-term (3-12 months):**
1. __________________________________________________________
2. __________________________________________________________
3. __________________________________________________________

**Expected Total Savings:**
- Immediate: $______0____/month
- Short-term: $______0____/month
- Long-term: $________0__/month

---

## Part 10: Present Findings

### Step 20: Create Stakeholder Report

Prepare a cost analysis presentation.

**Include:**
1. Executive summary of spending
2. Cost trends (charts)
3. Top cost drivers
4. Optimization opportunities
5. Recommended actions
6. Expected ROI

**📸 Screenshot 18:** Export Cost Explorer report to CSV/PDF

**Export report:**
1. In Cost Explorer, click **Download** (top right)
2. Choose CSV or PNG for charts
3. Compile into presentation/document

---

## Verification Checklist

- [ ] Enabled Cost Explorer
- [ ] Analyzed 6-month cost trends
- [ ] Identified top cost drivers by service
- [ ] Analyzed costs by region
- [ ] Activated cost allocation tags
- [ ] Tagged at least 3 resources
- [ ] Created 3 custom cost reports
- [ ] Set up Cost Anomaly Detection (2 monitors)
- [ ] Reviewed optimization recommendations
- [ ] Identified idle resources
- [ ] Calculated Reserved Instance savings potential
- [ ] Created cost optimization action plan
- [ ] Exported reports for stakeholders

---

## Key Takeaways

✅ **Cost Explorer** provides deep visibility into AWS spending  
✅ **Regular cost reviews** prevent budget surprises  
✅ **Cost allocation tags** enable chargeback and accountability  
✅ **Anomaly Detection** catches unexpected spikes early  
✅ **Right-sizing** and **Reserved Instances** offer significant savings  
✅ **Idle resources** are easy wins for cost reduction  
✅ **Continuous optimization** is essential for cloud cost management  

---



## Next Steps

- Schedule monthly Cost Explorer reviews
- Implement comprehensive tagging strategy across all resources
- Set up automated cost reports (email delivery)
- Explore AWS Savings Plans
- Learn about AWS Budgets Actions (automated responses)
- Study FinOps best practices

**Congratulations!** You've mastered AWS Cost Explorer and optimization strategies!
