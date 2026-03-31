# 🛍 Shopify Flow: Bulk Discount Sender

## 📌 Overview
This project uses Shopify Flow to automatically send discount codes to customers based on their order value.

- Only high-value customers (>$200) receive discounts  
- Each customer gets the reward only once  
- Fully automated (no custom app required)  

---

## ⚙️ Workflow Trigger

**Event:** Order Created  

The flow starts whenever a new order is placed.

---

## ✅ Conditions

The workflow runs only if:

- Order total is greater than **200**  
- Customer does NOT have tag `reward_sent`  

---

## 🔄 Workflow Steps

### 1. Generate Discount Code
A unique discount code is generated dynamically.

---

### 2. Save Discount to Metafield

**Metafield:**
```

Namespace: custom
Key: generated_discount_code

````

**Value:**
```liquid
{{ discount.code }}
````

---

### 3. Send Marketing Email


Hi {{ customer.first_name }},

Thank you for your recent order! 🎉

Here is your exclusive discount code:

👉 {{ customer.metafields.custom.generated_discount_code }}

Use this on your next purchase.

Happy shopping 💙

---

### 4. Add Customer Tag


reward_sent


This prevents duplicate rewards.

---

## 🧠 Workflow Logic

ON Order Created:

IF order.total_price > 200
AND customer.tags NOT CONTAINS "reward_sent"

THEN:
    discount = generate_discount()

    customer.metafield.custom.generated_discount_code = discount.code

    send_email(customer.email, discount.code)

    add_tag(customer, "reward_sent")

---

## 🎯 Use Case

* Reward loyal customers
* Increase repeat purchases
* Fully automated marketing
* No third-party app needed

---

## 🚀 Requirements

* Shopify Flow enabled
* Marketing email setup

---

## 📂 Project Structure


shopify-flow-discount/
│── README.md
│── flow.png

---

## 🔧 What I fixed
- Closed all ``` code blocks properly  
- Fixed headings (`#`, `##`, `###`)  
- Separated email + metafield sections  
- Cleaned spacing for GitHub readability  
- Removed broken mixed content  

---

If you want next level:
- I can add **badges (GitHub style)**
- Or make **diagram image for repo**
- Or write **LinkedIn/CV project description 🔥**

Just tell me 👍