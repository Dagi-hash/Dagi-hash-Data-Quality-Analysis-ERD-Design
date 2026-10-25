# Short Note: Task 4 Answers

The `customers` table contains both `customer_id` and `customer_unique_id`: `customer_id` is an order-scoped surrogate key generated per transaction/order, whereas `customer_unique_id` identifies the actual individual human customer; therefore, `customer_unique_id` must be used to count distinct underlying customers. 

The `order_items` table acts as a junction table that resolves the many-to-many ($M:N$) relationship between `orders` and `products`, while also attributing each line item to its respective supplier in `sellers`. 

In terms of data constraints versus diagram design:
- **Stricter in data:** The child relationship from `order_items` to `orders` (and `products`/`sellers`) is stricter in the data because there are 0 orphan records (every line item strictly references valid parents).
- **Justified circle ($0..N$):** The optional circle on the parent side of `orders` $\rightarrow$ `order_items` is justified by the data because 775 orders contain zero items (resulting from orders canceled or marked unavailable before fulfillment).s