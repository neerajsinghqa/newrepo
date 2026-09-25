# Test Cases for US01 - Add Available Product to Cart

## Markdown Table

| Test ID | Type | Scenario | Preconditions | Steps | Expected Result |
|---|---|---|---|---|---|
| TC-01 | Positive | Registered user adds an available product | User is registered and logged in; product is in stock and visible on product detail page | 1. Open product detail page. 2. Click “Add to Cart.” | Product is added to cart; success message is displayed; cart count increases by 1 |
| TC-02 | Positive | Add to cart from product detail page | User is logged in; product is available | 1. Navigate to product detail page. 2. Click “Add to Cart.” | Product is added to cart and remains on current page |
| TC-03 | Positive | Default quantity is 1 | User is logged in; product is available; no quantity selected | 1. Open product detail page. 2. Click “Add to Cart.” | Cart entry for product shows quantity = 1 |
| TC-04 | Positive | Duplicate product quantity increments | Product already exists in cart | 1. Open product page. 2. Click “Add to Cart.” | Quantity of existing product increases by 1; no duplicate cart row is created |
| TC-05 | Positive | Add product with valid selected variant | Product has variants (e.g., size/color); variant is in stock | 1. Select valid size/color. 2. Click “Add to Cart.” | Selected variant is the one added to cart |
| TC-06 | Positive | Confirmation message appears after successful add | User logged in; product available | 1. Click “Add to Cart.” | “Product added to cart” message appears; cart count updates |
| TC-07 | Positive | User remains on current page after add | User is on product detail page | 1. Add item to cart. 2. Observe page state | User stays on current page and can continue browsing |
| TC-08 | Positive | Cart persists after logout/login | Logged-in user already added product | 1. Log out. 2. Log back in. 3. Open cart | Previously added product remains in cart |
| TC-09 | Positive | Add product with no manual quantity specified | User is logged in; product available; quantity field empty | 1. Go to product page. 2. Click “Add to Cart.” | Cart reflects 1 unit automatically |
| TC-10 | Positive | User adds product and continues checkout flow | User logged in; cart contains product | 1. Add product to cart. 2. Open cart. 3. Proceed to checkout | Item is visible in cart and available for checkout |
| TC-11 | Negative | Unauthenticated user cannot add to cart | User is not logged in | 1. Open product page. 2. Click “Add to Cart.” | Action is blocked; user is redirected to login or prompted to authenticate |
| TC-12 | Negative | Out-of-stock product cannot be added | Product is marked out of stock | 1. Open product detail page. 2. Click “Add to Cart.” | Action is prevented; message “This product is currently unavailable” is shown |
| TC-13 | Negative | Unavailable product cannot be added | Product is unavailable due to inventory or status | 1. Open unavailable product page. 2. Click “Add to Cart.” | Product is not added; error/unavailable message is displayed |
| TC-14 | Negative | Invalid product variant cannot be added | Product has variants; selected variant is invalid/not available | 1. Pick invalid variant. 2. Click “Add to Cart.” | Product is not added; user sees validation message |
| TC-15 | Negative | Server error during add to cart | User is logged in; product available; backend fails | 1. Click “Add to Cart.” 2. Server returns error | Product is not added; error message explains failure; cart count does not increase |
| TC-16 | Negative | Connectivity issue prevents add to cart | User is logged in; network connectivity fails during request | 1. Click “Add to Cart.” 2. Connection is interrupted | Cart is unchanged; user sees connectivity/server error message |
| TC-17 | Negative | Invalid quantity is rejected | Product available; user enters quantity 0 or negative value | 1. Enter quantity 0 or -1. 2. Click “Add to Cart.” | Product is not added; quantity validation error is shown |
| TC-18 | Negative | Product not added when cart update fails | User logged in; product is available; cart service error occurs | 1. Add to cart. 2. Cart service fails | Product is absent from cart; user is notified of failure |
| TC-19 | Negative | Duplicate product different variant is not mistaken as same item | Product has variants; different variant already in cart | 1. Select different valid variant. 2. Add to cart. | System treats as separate variant entry or blocks if business rules require unique variant tracking |
| TC-20 | Negative | Cart count and success message do not update on failed add | User logged in; service error or unavailable product | 1. Attempt add to cart. 2. Observe page state | No success message is shown; cart count remains unchanged; failed transaction is not reflected as added |

## CSV Format

```csv
Test ID,Type,Scenario,Preconditions,Steps,Expected Result
TC-01,Positive,"Registered user adds an available product","User is registered and logged in; product is in stock and visible on product detail page","1. Open product detail page. 2. Click ""Add to Cart.""","Product is added to cart; success message is displayed; cart count increases by 1"
TC-02,Positive,"Add to cart from product detail page","User is logged in; product is available","1. Navigate to product detail page. 2. Click ""Add to Cart.""","Product is added to cart and remains on current page"
TC-03,Positive,"Default quantity is 1","User is logged in; product is available; no quantity selected","1. Open product detail page. 2. Click ""Add to Cart.""","Cart entry for product shows quantity = 1"
TC-04,Positive,"Duplicate product quantity increments","Product already exists in cart","1. Open product page. 2. Click ""Add to Cart.""","Quantity of existing product increases by 1; no duplicate cart row is created"
TC-05,Positive,"Add product with valid selected variant","Product has variants (e.g., size/color); variant is in stock","1. Select valid size/color. 2. Click ""Add to Cart.""","Selected variant is the one added to cart"
TC-06,Positive,"Confirmation message appears after successful add","User logged in; product available","1. Click ""Add to Cart.""","""Product added to cart"" message appears; cart count updates"
TC-07,Positive,"User remains on current page after add","User is on product detail page","1. Add item to cart. 2. Observe page state","User stays on current page and can continue browsing"
TC-08,Positive,"Cart persists after logout/login","Logged-in user already added product","1. Log out. 2. Log back in. 3. Open cart","Previously added product remains in cart"
TC-09,Positive,"Add product with no manual quantity specified","User is logged in; product available; quantity field empty","1. Go to product page. 2. Click ""Add to Cart.""","Cart reflects 1 unit automatically"
TC-10,Positive,"User adds product and continues checkout flow","User logged in; cart contains product","1. Add product to cart. 2. Open cart. 3. Proceed to checkout","Item is visible in cart and available for checkout"
TC-11,Negative,"Unauthenticated user cannot add to cart","User is not logged in","1. Open product page. 2. Click ""Add to Cart.""","Action is blocked; user is redirected to login or prompted to authenticate"
TC-12,Negative,"Out-of-stock product cannot be added","Product is marked out of stock","1. Open product detail page. 2. Click ""Add to Cart.""","Action is prevented; message ""This product is currently unavailable"" is shown"
TC-13,Negative,"Unavailable product cannot be added","Product is unavailable due to inventory or status","1. Open unavailable product page. 2. Click ""Add to Cart.""","Product is not added; error/unavailable message is displayed"
TC-14,Negative,"Invalid product variant cannot be added","Product has variants; selected variant is invalid/not available","1. Pick invalid variant. 2. Click ""Add to Cart.""","Product is not added; user sees validation message"
TC-15,Negative,"Server error during add to cart","User is logged in; product available; backend fails","1. Click ""Add to Cart."" 2. Server returns error","Product is not added; error message explains failure; cart count does not increase"
TC-16,Negative,"Connectivity issue prevents add to cart","User is logged in; network connectivity fails during request","1. Click ""Add to Cart."" 2. Connection is interrupted","Cart is unchanged; user sees connectivity/server error message"
TC-17,Negative,"Invalid quantity is rejected","Product available; user enters quantity 0 or negative value","1. Enter quantity 0 or -1. 2. Click ""Add to Cart.""","Product is not added; quantity validation error is shown"
TC-18,Negative,"Product not added when cart update fails","User logged in; product is available; cart service error occurs","1. Add to cart. 2. Cart service fails","Product is absent from cart; user is notified of failure"
TC-19,Negative,"Duplicate product different variant is not mistaken as same item","Product has variants; different variant already in cart","1. Select different valid variant. 2. Add to cart.","System treats as separate variant entry or blocks if business rules require unique variant tracking"
TC-20,Negative,"Cart count and success message do not update on failed add","User logged in; service error or unavailable product","1. Attempt add to cart. 2. Observe page state","No success message is shown; cart count remains unchanged; failed transaction is not reflected as added"
```
