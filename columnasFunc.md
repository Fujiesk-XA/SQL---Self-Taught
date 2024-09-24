DiscountCategory = 

Var DiscountPct = Divide ( Sales[Unit Discount], Sales[Unit Price])

Return

If (
    DiscountPct = 0,
    "FULL PRICE",
    if(
        DiscountPct<= 0.05,
        "LOW",
        IF ( DiscountPct <= 0.1, "MEDIUM", "HIGH") 
    )
)
