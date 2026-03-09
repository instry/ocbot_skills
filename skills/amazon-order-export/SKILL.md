---
name: amazon-order-export
description: Exports your Amazon order history to a downloadable spreadsheet. Use this when the user wants to extract order data including item names, prices, dates, and delivery status for record keeping, expense tracking, or returns management.
triggerPhrases:
  - export amazon orders
  - download amazon order history
  - amazon订单导出
  - 导出亚马逊订单
  - amazon order spreadsheet
startUrl: "https://www.amazon.com/gp/css/order-history"
urlPattern: "amazon.com"
categories:
  - e-commerce
  - data-export
parameters:
  - name: year
    type: select
    description: "Order year to export, selecting from the year dropdown on the order history page"
    required: false
    default: "2025"
    options: ["2025", "2024", "2023"]
  - name: max_pages
    type: number
    description: "Maximum number of order history pages to scrape before stopping (each page contains ~10 orders)"
    required: false
    default: 5
preconditions:
  - type: url_contains
    value: "amazon.com"
    description: "Browser must be on Amazon domain with active login session"
---

# Amazon Order Export

## Workflow
1. Navigate to https://www.amazon.com/gp/css/order-history (Amazon "Your Orders" page).
2. Select the target year from the "Orders placed in" dropdown if {{year}} differs from the current selection.
3. For each order on the page, extract: order date, order ID, item name, item price, delivery status.
4. If more pages exist and current page count < {{max_pages}}, click the "Next" pagination button and repeat step 3.
5. Compile all extracted data into a CSV table and trigger a browser download.

## Preconditions
- User must be logged into their Amazon account (active session).
- Browser must be on the Amazon domain (amazon.com) to ensure session cookies are available.

## Success Criteria
- A CSV file is downloaded containing columns: Order Date, Order ID, Item Name, Price, Status.
- All visible orders across the scraped pages are included in the export.

## Notes
- If an order contains multiple items, each item is exported as a separate row with the same Order ID.
- Digital orders and physical orders are both included.
- Cancelled orders may appear with a "Cancelled" status in the export.
