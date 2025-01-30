# Video-Game Analysis

### PROJECT OVERVIEW

The video game industry has evolved significantly over the decades, with shifts in popular genres, regional preferences, and platform dominance. This project aims to analyze global video game sales data from 1971 to 2024, covering 64,016 titles across various platforms, genres, and regions. By uncovering key trends and insights, we seek to understand the industry's trajectory and answer critical questions such as:
1. Which titles achieved the highest worldwide sales?
2. Which year recorded the highest sales, and has the industry grown over time?
3. Do any gaming consoles specialize in specific genres?
4. What games are popular in one region but underperform in another?

### PROBLEM STATEMENT

The gaming industry is highly dynamic, with sales patterns influenced by platform exclusivity, regional preferences, and changing consumer interests. This analysis aims to:
1. Identify the best-selling games globally.
2. Assess industry growth trends over time.
3. Examine whether certain consoles specialize in specific genres.
4. Compare regional preferences to determine which games thrive in one market but fail in another.


### DATA SOURCE AND STRUCTURE
- Source: Kaggle (via ASANICZKA)
- File Type: CSV
- Data Structure: Single table
- Number of Records: 62,884
- Number of Fields: 37
-  Date Added: 06/10/2024

### TOOLS USED
- Excel: Data cleaning, preparation, and preliminary analysis.
- Power BI: Visualization of trends and insights.

###  PROCESS OF ANALYSIS
#### 1. Data Cleaning and Preparation
- Identified missing or incomplete entries in key columns (total_sales, genre, console, release_date).
- Handled missing data by filling in feasible values or removing records with excessive gaps.
- Removed duplicate entries for games with redundant records.
- Converted data types where necessary (e.g., numeric values for sales, datetime for release dates).

 ####  2.Specific Analyses
#### Top-Performing Titles
- Ranked games based on worldwide sales to determine the best-selling titles.
- Analyzed patterns in their release years, genres, and regional performance using bar charts.
#### Industry Growth Analysis
- Aggregated total sales per year and plotted trends to assess industry growth.
- Identified peak sales years and correlated findings with major industry events or console releases.
#### Console Specialization
- Grouped sales data by console and genre.
- Calculated the proportion of each genre's sales within a console's total sales using the DAX function:

``` DAX
GenreSales = SUM('vg_data'[total_sales])
ConsoleTotalSales = CALCULATE(SUM('vg_data'[total_sales]), ALLEXCEPT('vg_data', 'vg_data'[console]))
GenreProportion = [GenreSales] / [ConsoleTotalSales]
```
- Analyzed patterns in their release years, genres, and regional performance using bar charts.
#### Regional Popularity Trends
- Compared sales across regions (e.g., na_sales vs. jp_sales) to identify games with contrasting regional performance using:

``` Excel Function 
=IF(AND(I2>1,J2<0.1),"NA Popular, JP Flop",
  IF(AND(J2>1,I2<0.1),"JP Popular, NA Flop",
   IF(AND(I2>1,K2<0.1),"NA Popular, PAL Flop",
   IF(AND(K2>1,J2<0.1),"PAL Popular, NA Flop","No Significant Difference"))))
```
- Compared total sales by region to analyze geographical trends.

 ###  KEY INSIGHTS AND FINDINGS
- Best-Selling Game: Grand Theft Auto V recorded the highest sales at 64 million copies.
- Peak Sales Year: The highest industry-wide sales occurred in 2008, reaching 538 million copies. However, overall sales have declined in recent years.
- Regional Performance:
   - Some games performed exceptionally well in North America but flopped in Japan, such as Sonic Advance, ChuChu Rocket, Assassin’s Creed, Dance Central, and Command & Conquer.
   - Conversely, certain games thrived in Japan but underperformed in North America, including Dance Dance Revolution (Japan), Derby Stallion 96, and Devil Dice.
   - Games like Doom (2016), Far Cry, and FIFA 07 performed better in the PAL region but struggled in Japan.
- Regional Sales Distribution:
   - North America had the highest sales: 3.35 million (56.22%).
   - PAL region followed with 1.92 million (32.22%).
   - Japan had the lowest sales: 0.69 million (11.56%).
- Console-Genre Specialization:
   - Game Gear (GG): Specializes in Platform games.
   - PC-FX: Specializes in Role-Playing Games (RPGs).
   - Mac OS X: Dominates the Strategy genre.
   - WW (WonderSwan Color): Focuses on Miscellaneous games.
