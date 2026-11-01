# Power-BI-Projects
This repo consist of Power BI project, data visualisation and dashboard
India Mainboard IPOs 2025: What Signals Mattered?

A beginner-friendly Power BI project analysing 103 Mainboard IPOs in India in 2025 (about ₹1.76 lakh crore raised) to see which simple, public signals matched better outcomes for investors.

 Tools: Power BI, DAX, Excel/CSV

Business problem

Before an IPO opens, investors ask: "Should I apply?" Many decide on hype or tips. This project checks, using 2025 data, whether two simple signals (subscription level and issue size) lined up with good listing-day and post-listing outcomes. It also shows when and in which sectors money was raised.

Who can use it: retail investors, finance students, analysts, and anyone who wants a data-based view of IPO activity.

Objectives and key findings
1. Does higher subscription mean a better listing day?
Subscription	IPOs	Avg listing gain	% that gained on listing
Below 5x	32	-4.1%	34%
5x to 20x	21	+5.6%	62%
20x to 50x	23	+12.1%	83%
Above 50x	27	+26.2%	96%

Finding: the more oversubscribed an IPO, the better its listing day, and the pattern is steady. After listing, only IPOs above 50x had a clear edge (59% were above issue price, against 39-44% for the rest).

2. Do bigger IPOs perform better after listing?
Size	IPOs	Avg return since issue	Median	% above issue price
Small (< ₹250 Cr)	18	-14.6%	-20.8%	22%
Medium (₹250-1,000 Cr)	50	+16.1%	-15.7%	46%
Large (> ₹1,000 Cr)	35	+36.3%	+10.0%	60%

Finding: large IPOs did best and small IPOs did worst. The pattern holds in the average, the median and the share above issue price, so it is the most reliable result here.

3. When and in which sectors was money raised?
October raised the most (₹45,188 Cr, about 26% of the year). There were no IPOs in March.
September had the most IPOs (25) but a weak average listing gain (+0.7%).
NBFCs led all sectors by amount raised (₹28,266 Cr), followed by asset management companies (₹11,929 Cr).
Dashboard

3 pages, interactive (click any bar or use the slicers):

Page	What it shows
1. Subscription vs Listing Day	Avg listing gain and % above issue price by subscription group, with a month slicer
2. Size vs Returns	Avg return, median return and % above issue price by issue size, with a subscription slicer
3. Months and Sectors	Money raised and IPO count by month, and top 10 sectors by amount raised

 KPI cards for Total IPOs, Total Raised (₹ Cr) and Avg Listing Gain %.

Source: Reports on 2025 Mainboard IPOs in India are taken from (https://www.ipomatrix.com/)

Note on the model: IPO_Data and Sector have no common column, so they are not linked. Each table feeds its own visuals.

DAX measures

Total IPOs = COUNTROWS ( IPO_Data )
Total Raised Cr = SUM ( IPO_Data[Issue_Amount_Cr] )
Avg Listing Gain % = AVERAGE ( IPO_Data[Listing_Gain_Pct] )
Avg Return Since Issue % = AVERAGE ( IPO_Data[Return_Since_Issue_Pct] )
Median Return Since Issue % = MEDIAN ( IPO_Data[Return_Since_Issue_Pct] )

% Listing Gain =
DIVIDE (
    CALCULATE ( COUNTROWS ( IPO_Data ), IPO_Data[Listing_Result] = "Gain" ),
    [Total IPOs]
)

% Above Issue Price =
DIVIDE (
    CALCULATE ( COUNTROWS ( IPO_Data ), IPO_Data[Current_Result] = "Above Issue Price" ),
    [Total IPOs]
)

Limitations
Returns since issue use one price snapshot, not a fixed holding period, so IPOs listed later in the year had less time.
The average return is lifted by a few big winners, which is why the median is shown too.
Some groups are small (for example, individual months), so treat month-level results as description, not prediction.
This is one year of data. It describes 2025; it does not predict future IPOs.
This is an educational project, not investment advice.
