import pandas as pd
customers = pd.read_csv("customers.csv")
products = pd.read_csv("products.csv")
orders = pd.read_csv("orders.csv")
customers = customers.drop_duplicates()
invalid_orders = orders[
    orders["customer_id"].isin(customers["customer_id"])
]
print("Invalid Orders:")
print(invalid_orders)
valid_orders = orders[
    orders["customer_id"].isin(customers["customer_id"])
]
merged_df = pd.merge(
    valid_orders,
    customers,
    on="customer_id",
    how="inner"
)
merged_df = pd.merge(
    merged_df,
    products,
    on="product_id",
    how="inner"
)
merged_df["total_amount"] = (
    merged_df["quantity"] * merged_df["price"]
)
final_orders = merged_df[
    [
        "order_id",
        "customer_name",
        "city",
        "product_name",
        "quantity",
        "price",
        "status",
        "total_amount"
    ]
]
final_orders.to_csv(
    "final_orders.csv",
    index=False
)
print("\nFinal Orders:")
print(final_orders)