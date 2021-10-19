# Fill these in
LOAN_START = 3000000 # Loan size in any currency
YEARS_TO_PAY = 50 # How many years it takes to pay off your loan with your current payment plan
LOAN_INTEREST = 0.0114 # 1.0 = 100% and 0.01 = 1%

# Fill these in if you want
INSTALMENTS_IN_INDEX = 1 # How many installments you plan on putting in index funds
EXTRA_INSTALMENT = 0 # How many extra installments you plan on making every month

# Interest Deduction, set this to 1.0 if your government doesn't have this
INTEREST_DEDUCTION = 0.7

# Average index fund return (over the past 140 years the average S&P 500 has been 9.2% when averaged over any set of 10 years)
AVERAGE_INDEX_PERCENTAGE = 0.07


"""
# No need to look beyond this point
"""
MONTHS_TO_PAY = YEARS_TO_PAY * 12
BASE_INSTALMENT_MONTH = int(LOAN_START / MONTHS_TO_PAY)
INSTALMENT_MONTH = LOAN_START / MONTHS_TO_PAY * (1 + EXTRA_INSTALMENT)
ACTUAL_YEARS = MONTHS_TO_PAY / (1 + EXTRA_INSTALMENT) / 12
MONTHS_TO_PAY = int(MONTHS_TO_PAY / (1 + EXTRA_INSTALMENT))
INSTALMENT_PER_MONTH = INSTALMENT_MONTH * INSTALMENTS_IN_INDEX

loan_current = LOAN_START

TOTAL_COST = 0
AVERAGE_INDEX_INCREASE = 0

printed = r"""
The total cost of %(LOAN_START)s is %(TOTAL_COST)s
A total increase of %(INCREASE)s (%(LOAN_PERCENT_INCREASE)s%%)
Actual years counting extra installments %(ACTUAL_YEARS)s
Average interest paid per year %(AVERAGE_YEAR)s and month %(AVERAGE_MONTH)s
Amount paid off per year %(INSTALLMENT_YEAR)s and month %(INSTALMENT_MONTH)s
A total of %(YEAR_INSTALLMENT_RENT)s per year and a total of %(MONTH_INSTALLMENT_RENT)s per month
Your total amount invested is %(INVESTED)s a total of %(INVEST_PER_MONTH)s per month
Your total amount gained is %(AVERAGE_INDEX_INCREASE)s (%(INDEX_PERCENT_INCREASE)s%%)"""

def calc_interest_month(current_loan_amount):
    return current_loan_amount * LOAN_INTEREST / 12

def prettify_number(ugly_number):
    return "{:,}".format(int(ugly_number))

for month in range(0, MONTHS_TO_PAY):
    TOTAL_COST = TOTAL_COST + INSTALMENT_MONTH
    TOTAL_COST = TOTAL_COST + calc_interest_month(loan_current) * INTEREST_DEDUCTION
    loan_current = loan_current - INSTALMENT_MONTH
    AVERAGE_INDEX_INCREASE = (AVERAGE_INDEX_INCREASE + (AVERAGE_INDEX_INCREASE * (AVERAGE_INDEX_PERCENTAGE / 12))) + INSTALMENT_PER_MONTH


INCREASE = TOTAL_COST - LOAN_START
INDEX_PERCENT_INCREASE = prettify_number(AVERAGE_INDEX_INCREASE / (INSTALMENT_PER_MONTH * ACTUAL_YEARS * 12) * 100)
LOAN_PERCENT_INCREASE = prettify_number(INCREASE/LOAN_START*100)
INVESTED = prettify_number(INSTALMENT_PER_MONTH * ACTUAL_YEARS * 12)
AVERAGE_INDEX_INCREASE = prettify_number(AVERAGE_INDEX_INCREASE)
MONTH_INSTALLMENT_RENT = prettify_number(INCREASE / ACTUAL_YEARS / 12 + INSTALMENT_MONTH)
YEAR_INSTALLMENT_RENT = prettify_number(INCREASE / ACTUAL_YEARS + INSTALMENT_MONTH * 12)
AVERAGE_YEAR = prettify_number(INCREASE / ACTUAL_YEARS)
AVERAGE_MONTH = prettify_number(INCREASE / ACTUAL_YEARS / 12)
TOTAL_COST = prettify_number(TOTAL_COST)
INCREASE = prettify_number(INCREASE)
LOAN_START = prettify_number(LOAN_START)
ACTUAL_YEARS = prettify_number(ACTUAL_YEARS)
INSTALLMENT_YEAR = prettify_number(INSTALMENT_MONTH * 12)
INSTALMENT_MONTH = prettify_number(INSTALMENT_MONTH)
INVEST_PER_MONTH = prettify_number(INSTALMENT_PER_MONTH)

print(printed % {
    "LOAN_START": LOAN_START,
    "INCREASE": INCREASE,
    "INSTALMENT_MONTH": INSTALMENT_MONTH,
    "INSTALLMENT_YEAR": INSTALLMENT_YEAR,
    "INVEST_PER_MONTH": INVEST_PER_MONTH,
    "LOAN_PERCENT_INCREASE": LOAN_PERCENT_INCREASE,
    "YEAR_INSTALLMENT_RENT": YEAR_INSTALLMENT_RENT,
    "MONTH_INSTALLMENT_RENT": MONTH_INSTALLMENT_RENT,
    "INDEX_PERCENT_INCREASE": INDEX_PERCENT_INCREASE,
    "TOTAL_COST": TOTAL_COST,
    "AVERAGE_YEAR": AVERAGE_YEAR,
    "AVERAGE_YEAR": AVERAGE_YEAR,
    "AVERAGE_MONTH": AVERAGE_MONTH,
    "ACTUAL_YEARS": ACTUAL_YEARS,
    "AVERAGE_INDEX_INCREASE": AVERAGE_INDEX_INCREASE,
    "INVESTED": INVESTED
})
