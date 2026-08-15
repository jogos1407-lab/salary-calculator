def calculate_pay(hours_worked, hourly_rate):
    """Calculate regular pay, overtime pay, and total gross pay."""
    
    regular_hours = min(hours_worked, 40)
    overtime_hours = max(0, hours_worked - 40)

    regular_pay = regular_hours * hourly_rate
    overtime_pay = overtime_hours * (hourly_rate * 1.5)
    gross_pay = regular_pay + overtime_pay

    return regular_pay, overtime_pay, gross_pay


def calculate_yearly_salary(biweekly_income=None, hourly_rate=None):
    """Calculate yearly salary from biweekly income or hourly rate."""
    
    if biweekly_income:
        return biweekly_income * 26  # 26 pay periods per year
    
    if hourly_rate:
        return hourly_rate * 40 * 52  # 40 hrs × 52 weeks
    
    return None


def calculate_after_taxes(gross_pay, tax_rate=0.20):
    """Calculate net pay after taxes."""
    return gross_pay * (1 - tax_rate)


def main():
    print("=== Salary & Pay Calculator ===")

    hours = float(input("Enter hours worked this week: "))
    rate = float(input("Enter hourly rate: "))
    tax_rate = float(input("Enter tax rate (example: 0.20 for 20%): "))

    regular, overtime, gross = calculate_pay(hours, rate)
    net_pay = calculate_after_taxes(gross, tax_rate)

    print("\n--- Weekly Summary ---")
    print(f"Regular Pay: ${regular:.2f}")
    print(f"Overtime Pay: ${overtime:.2f}")
    print(f"Gross Pay: ${gross:.2f}")
    print(f"Net Pay (after taxes): ${net_pay:.2f}")

    print("\n--- Yearly Salary Options ---")
    biweekly = float(input("Enter biweekly income (or 0 to skip): "))
    
    if biweekly > 0:
        yearly = calculate_yearly_salary(biweekly_income=biweekly)
    else:
        yearly = calculate_yearly_salary(hourly_rate=rate)

    print(f"Estimated Yearly Salary: ${yearly:.2f}")


if __name__ == "__main__":
    main()
