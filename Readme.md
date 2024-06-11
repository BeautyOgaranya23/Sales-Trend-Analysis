
# Project Overview

 In today's dynamic market landscape, understanding trends and performance metrics is paramount for the success of any business, including the pizza industry. This project aims to analyze various aspects of a Pizza Company's operations to uncover actionable insights that drive growth, enhance customer satisfaction, and optimize operational efficiency.

 ## Key Questions 💡

 1. What is the monthly total revenue breakdown?
 2. During which time of day do we observe the highest pizza sales?
 3. Which month exhibits the highest sales performance?
 4. Which pizza variety demonstrates the strongest sales performance?
 5. Which pizza size is the top-selling option?
 6. What is the monthly quantity of pizzas sold?
 7. What is the total revenue generated over the course of the year?

# Methodology

For this analysis, we utilized Azure Data Studio for data preprocessing, querying, and transformation tasks. Power BI was employed for data visualization to create informative and interactive dashboards that provide clear insights into key metrics.

## 🔍 Findings and Insights

* Trend Analysis: This analysis visualizes daily sales over time, allowing us to identify peak hours and trends in customer purchasing behavior. This insight is crucial for optimizing staffing schedules and inventory management.

 -- Query to calculate the peak hours

    SELECT DATEPART(HOUR, [time]) AS HourOfDay, SUM([amount_of_quantity_ordered_monthly]) AS totalSales
    FROM #orderinfo
    GROUP BY DATEPART(HOUR, [time])
    ORDER BY HourOfDay


![image](https://github.com/BeautyOgaranya23/Sales-Trend-Analysis/assets/170759416/902a40ee-4022-4a54-bacd-9112c0e3d108)


* Pizza Size Revenue Distribution: The pie chart showcases the revenue generated by different pizza sizes, providing insights into popular choices among customers. This information can guide menu optimization and pricing strategies.

--- Revenue generated by each the different sizes of pizzas at the end of the year

    SELECT [size], [year], SUM([monthly_sales]) as total_revenue_per_pizza 
    from #pizzasale
    group by [year], [size]
    order by SUM([monthly_sales]) desc

![image](https://github.com/BeautyOgaranya23/Sales-Trend-Analysis/assets/170759416/24a5965d-19ed-4b98-ab0e-49deb5b0fab9)


* Day of the Week Sales Comparison: The chart compares sales performance across different days of the week. Understanding which days yield the highest sales volume enables targeted marketing efforts and resource allocation.

-- The day of the week with the highest order quantity

    SELECT SUM([number_of_pizza_orders]) AS dailyorder, DATEPART(WEEKDAY, [date]) AS DayOfWeek
    FROM [dbo].[Pizza_sales_data] as S
    inner join #orderinfo as I
    on S.pizza_id = I.pizza_id
    GROUP BY DATEPART(WEEKDAY, [date])

![image](https://github.com/BeautyOgaranya23/Sales-Trend-Analysis/assets/170759416/24c69f35-d32f-4939-896d-1ca7ff55cc68)


* Monthly Revenue Distribution: The line graph illustrates the distribution of monthly revenue, highlighting any seasonal trends or fluctuations. This insight aids in forecasting and budgeting for future periods.

--this gives total monthly sales 

    select SUM([amount_of_quantity_ordered_monthly] * [price]) as monthly_sales,[month]
    FROM [dbo].[Pizzas_details] as P
    inner join [dbo].[Order_3] as O
    on P.pizza_id = O.pizza_id
    Group by [month]

![image](https://github.com/BeautyOgaranya23/Sales-Trend-Analysis/assets/170759416/11ba7478-a972-4b5b-b6d5-70235ba8f611)


* Total Revenue Distribution by Pizza type: The bar chart displays the total revenue generated by each pizza type, providing insights into the popularity and profitability of different pizzas. This information helps in identifying top-selling pizzas, guiding menu optimization and marketing strategies.
  
-- Revenue generated by each pizza type at the end of the year

    SELECT [pizza_type], [year], SUM([monthly_sales]) as total_revenue_per_pizza 
    from #pizzasale
    group by [pizza_type], [year]
    order by SUM([monthly_sales]) desc

![image](https://github.com/BeautyOgaranya23/Sales-Trend-Analysis/assets/170759416/d8fe4a79-f280-4fc4-85c4-be9581889fba)


# Key Business Insights
Detailed analysis of the pizza sales data has uncovered critical insights that can drive operational efficiency and strategic growth. These findings are essential for understanding customer behavior, optimizing resources, and enhancing marketing efforts. Here are the key insights from this analysis:

*  Peak sales hours are typically within the afternoon, between 12 PM and 1 PM. This aligns with typical lunch breaks, where many customers, including office groups and families, prefer ordering pizzas as a convenient and satisfying lunch option. 
* Large-sized pizzas contribute significantly to overall revenue, suggesting a preference for larger portions among customers.
* The highest number of pizza orders occur on weekdays, specifically from Mondays to Wednesdays. This can be attributed to workplace lunch orders, routine-driven convenience, and midweek promotions or discounts.
* Monthly revenue distribution exhibits seasonal variations, with higher revenue during certain months, possibly influenced by holidays or special events.

## 📄 Detailed Report

For a detailed view of the PowerBI visuals, you can download the full report in PDF format [Download Picture](trend_insights.jpeg)

# Recommendation and Conclusion

* Adjust staffing schedules and ensure sufficient inventory levels during weekdays, particularly from Mondays to Wednesdays, to meet increased demand and enhance operational efficiency.

* Tailor marketing campaigns to promote popular pizza varieties and offer promotions during peak sales hours in the afternoon to drive additional sales.

* Optimize pizza menu by introducing new pizza varieties aligned with customer preferences and removing less popular items to streamline operations and improve efficiency.

* Capitalize on seasonal trends in monthly revenue distribution by offering themed promotions and limited-time specials to attract customers and boost sales during peak months.

* Implement loyalty programs and customer engagement initiatives to incentivize repeat purchases, foster customer loyalty, and drive long-term profitability.

* Establish a process for ongoing monitoring and analysis of sales data to track performance metrics, identify trends, and adapt strategies in response to market dynamics.

In conclusion, exploring customer segmentation, menu innovation, digital integration, market expansion, and supply chain optimization presents exciting opportunities for the pizza company to sustain growth and competitiveness in the dynamic food industry landscape. By leveraging these potential avenues, the company can position itself for long-term success and continued excellence in meeting customer needs and preferences.

## Contact Information

For inquiries or further discussion, please contact:
- Email: [ogaobeauty@gmail.com](ogaobeauty@gmail.com)
- LinkedIn: [https://www.linkedin.com/in/ogaranyab]






