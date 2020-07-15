# GA_Superstore_Analysis
You’re working for a client who wishes to invest in an Airbnb property in Washington, D.C.
Before your client decides to invest, they’d like clean data about Airbnb performance in D.C.’s
neighborhoods that supports a clear recommendation for an investment in a specific market.

## Data Set
You’ve been provided with scraped data captured by a web program with listing information
from the Airbnb website. This data may contain unformatted data points with duplicate entries.
You’ll want to clean and format the data prior to performing exploratory analysis — this will
help you better understand the available data and build some business context.

## Main prompt
Should our investor invest in an Airbnb hotel in Washington, D.C.? If so, in which neighborhood should they invest?

## Sub-prompt
Host revenue — How much revenue do successful hosts generate?

● Estimate revenue per listing (each row is considered a listing).
    ○ Use the following assumptions:
        - Each booking always has two guests, unless the listing only
accommodates one.
        - The booking is always for the minimum number of days allowed.
        - Only half of the bookings generate a review.
    ○ Columns you’ll use to do this include:
        - Column BD, “price:” The price for a one-night stay.
        - Column BI, “guests_included:” This is how many guests are included in
the price.
        - Column BJ, “extra_people:” The extra cost per person if you go above the
number of “guests_included” in column BI.
        - Column AW, “accommodates:” How many people the property can
accommodate.

● Step 1: Calculate a proxy number of stays for each listing by assuming that 50
percent of customers who stayed left a review (use the data in the
“number_of_reviews” column). If 10 customers leave a review, you can assume
the listing had 20 stays in total (create a new column with a number that’s an
estimate for how many stays each listing has received).

● Step 2: Calculate estimated daily revenue for two guests, unless the
accommodation explicitly accepts only one. Use the following logic to create a
nested IF statement:
    ○ Determine if “guests_included &gt; 1” (i.e., whether the price quoted already
includes two or more people). This price represents daily revenue under
the assumptions.
    ○ If “guest_included = 1” and “accommodates = 1,” then the listing is only
for one person. This price represents daily revenue under the
assumptions.
    ○ If “guest_included = 1” but “accommodates &gt; 1”, then the price listed is
only for one person but the property can accommodate two or more, so
you need to add in the additional price for another person to get the daily
revenue for two people. This additional price is contained in column BL.

● Step 3: Multiply the estimated daily revenue by the minimum number of nights
to get a estimated revenue per booking.

● Step 4: Calculate an estimated total revenue for each listing by multiplying the
estimated revenue per booking by the estimated number of stays.

● Format: Have a column that calculates daily revenue — account for number of
guests accommodated, number of guests included in the price, and extra charge
for additional people using nested IF statements. Another column would then
calculate the revenue per booking. Finally, multiply that by the number of total
stays for the listings.

● Build several PivotTables in order to quickly explore the data at a high-level:
    ○ PivotTables should contain the host name, total revenue, and number of listings
(make sure to exclude listings with no bookings).
    ○ Additional PivotTables are welcome and useful for gaining a better
understanding of the data.
    ○ Format: Currency/thousands separators should be used where appropriate.
    
● Visualize insightful data for easier comprehension in support of your argument.

● Summarize relevant statistics for various data points.
    
● Finally, discuss your overall recommendation. Review the original prompt: “Should our investor invest in an Airbnb hotel in Washington, D.C.? If so, in which neighborhood should they invest?”
Create a final recommendation to the investor based on pertinent data from your analysis.
Keep in mind that the client wishes to understand the local market and its potential to host a profitable Airbnb property — demand is key, as is the price point.
