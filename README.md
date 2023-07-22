# mmm_econometrics

The following repository contains several scripts for customised Marketin Mix Modelling tool largely based on the Robyn, MMM tool created by Meta. The aim of the tool is to provide tailored solution to evaluate the impact of large TV campaigns and other offline channels. 

**Problem context:**
Big share of the marketing budget is allocated to Media advertising: general advertising as a brand or product, without the specifics of individual ads. Furthermore, approximately 70% of the media budget is allocated to TV advertising. Obviously, conventional campaign analysis methods (such as user-level attribution) won't be suitable. It's necessary to apply the Top-Down method, tracking uplifts in the target metric and decomposing them into the contribution of each channel.

**Problem statement:**
Build an econometrics model (Media Mix Modelling) to decompose the target metric into explanatory factors, specifically evaluating the contributions of TV and digital media advertising.

**Stack:**
The chosen analytical toolkit for this project includes R (specifically, the Robyn library), Python (Pandas, Vertica, Plotly).

R with the Robyn library is an open-source toolkit specifically designed for creating Media Mix Modelling and optimizing budget allocation. The preprocessing of data takes place in a Python notebook, where data is prepared and cleaned using libraries like Pandas and Vertica. The actual model evaluation is conducted in R Studio, which is installed on a server. Finally, the results and insights are visualized using Plotly.


**Results and Interpretation of the Model:**

*Single Campaign Evaluation:*

- The evaluation of the model output is a a table displaying the absolute contribution of each factor to the target metric for each assessed day within the econometrics window. Apart from the quality factors mentioned in the guide (NRMSE, business sense, consistency), a visual analysis can be conducted, and the MAPE metric can be calculated, which can be easily described and interpreted for the business. Below is an example of the decomposition of the Buyers metric (HTML file with the graph).

![IMAGE_DESCRIPTION](https://imgtr.ee/images/2023/07/22/7bb2714bd1170c5b34bed004c6baab9d.png)

- The black line represents the sum of actual sales for the week, while the colored line shows the overall contribution of the model's factors. It is also evident that during the periods of January to March and June to August 2022, the model underestimates the actual level of sales. This could be due to the current model not considering external factors specific to each sales line, such as product changes, competitors' influence, and market external conditions. Nevertheless, the model achieves an MAPE (Mean Absolute Percentage Error) of 4.7% and an R2 (Coefficient of Determination) of 0.94 on the training period. For the test period, the R2 is 0.85. 

*Cross-effect evaluation and Total ROI:*

Cross-effect evaluation and Total ROI are crucial in understanding the impact of Factor A on Metric B and the cross-effect of media channels between verticals. To achieve this, we need to include media investment factors from all five verticals in each customer acquisition model.

For example, a marketing campaign in the "Jobs" vertical with a 100 million budget incrementally attracted 700K customers, generating 35 million in revenue. Additionally, it attracted 900K customers in other verticals, resulting in 38 million in revenue. The total revenue from the campaign was 73 million, with 35 million attributed to the target effect and 38 million to the cross-effect. Therefore, the target ROI for this campaign would be 35%, while the total ROI would be 73%.

Econometric modeling allows evaluating not only the target effect but also the total effect of media investments, significantly increasing ROI and the potential of the marketing campaign.

*Budget allocation and future campaigns recommendation:*

Lastly, the tool provides valuable insights for future campaings' media parameters such as: length of the campaign, budget of the campaign per week, best season for the campaign etc. This is achieved through the so-called response curves which actually represent the relationship between the budget of the TV campaign spent, impresions received and, as a result, sales made optimising for ROI metrics. 
In particular, usage of these response curves allows us to test the following hypotheses:

- Optimal budget allocation between channels: By analyzing the response curve for TV and digital channels, we can determine the optimal budget split. For example, if the response curve suggests that the optimal budget for TV is around 10 million per week, and for digital is 15 million per week, reallocating 10 million from TV to digital may be a rational decision.
- Optimal campaign duration: Using the optimal weekly budget and total budget constraints for the TV campaign, we can recommend the distribution of the total budget among weeks. For instance, if the total budget is 80 million and the optimal weekly investment is 10 million, the optimal campaign duration would be 8 weeks.
- Enhanced forecasting for upcoming campaigns: By applying the hypotheses above, we can provide more accurate forecasts for future campaigns based on the total channel budget and campaign duration.
