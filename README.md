# FINE3300-Mortgage-Payments
Calculate mortgage payments for different payment frequencies
def mortgage_payments(principal, rate, amortization):
    """
    Calculate mortgage payments for different payment frequencies.
    
    :param principal: Loan principal amount
    :param rate: Quoted annual interest rate (as percentage)
    :param amortization: Loan amortization period in years
    :return: Tuple of (monthly, semi-monthly, bi-weekly, weekly) payments
    """
    # Convert quoted rate to decimal and compute monthly interest rate
    r = (1 + rate / 200) ** (2 / 12) - 1
    n = amortization * 12  # Total number of monthly payments
    
    # Compute annuity factor
    annuity_factor = (1 - (1 + r) ** -n) / r
    
    # Calculate monthly payment
    monthly = principal / annuity_factor
    
    # Compute other payment frequencies
    semi_monthly = monthly / 2
    bi_weekly = monthly * 12 / 26
    weekly = monthly * 12 / 52
    
    # Corrected indentation for return statement
    return round(monthly, 2), round(semi_monthly, 2), round(bi_weekly, 2), round(weekly, 2)

# Fixed values
principal = 500000
rate = 5.5
amortization = 25

# Compute payments
payments = mortgage_payments(principal, rate, amortization)

# Display results
print("\nMortgage Payments:")
print(f"Monthly Payment:  ${payments[0]:,.2f}")
print(f"Semi-monthly Payment:  ${payments[1]:,.2f}")
print(f"Bi-weekly Payment:  ${payments[2]:,.2f}")
print(f"Weekly Payment:  ${payments[3]:,.2f}")
