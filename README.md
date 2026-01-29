# Overview
During a security assessment of the e-commerce application, I identified a critical low-level logic flaw in the purchase workflow. The application’s handling of item quantities and total price calculations allowed an attacker to trigger an integer overflow, causing high-value purchases to appear at negative or unintended prices. By carefully manipulating the quantity parameter over multiple requests, I was able to place an order far exceeding the intended transaction logic without proper payment. This demonstrates a severe business logic vulnerability with significant financial risk.

# Steps Undertaken

Step 1: Intercepted purchase requests using Burp Suite to analyze quantity and pricing logic.

Step 2: Tested quantity limits and incrementally added items to the cart to probe for overflow conditions.

Step 3: Observed that totals exceeding the 32-bit signed integer limit wrapped into negative values.

Step 4: Manipulated the cart to exploit the overflow and placed a transaction at a price well below the true total.

Step 5: Verified the ability to complete the purchase, confirming the impact of the flaw.

# Conclusion

This assessment confirmed a high-severity business logic vulnerability stemming from integer overflow in the cart calculation system. Remediation requires strict server-side validation, proper bounds checking, and safe numeric handling to prevent financial exploitation. Immediate fixes are essential to protect revenue integrity and maintain trust in transactional processes.
