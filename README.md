# Seattle Airbnb Market & Pricing Analysis

[![Tableau Public](https://img.shields.io/badge/Tableau_Public-View_Dashboard-E97627?style=flat&logo=tableau)](https://public.tableau.com/app/profile/phyo.paing8212/viz/airbnb_analysis_17901513018730/Dashboard1)
[![Google Drive](https://img.shields.io/badge/Google_Drive-Dataset-4285F4?style=flat&logo=googledrive&logoColor=white)](https://drive.google.com/drive/folders/1pmh1SwwtRqr5Ad_hs3j6jdF9WpR8dMIK)

---

## Project Overview

* Live Dashboard: [View on Tableau Public](https://public.tableau.com/app/profile/phyo.paing8212/viz/airbnb_analysis_17901513018730/Dashboard1)
* Dataset: [Access Dataset on Google Drive](https://drive.google.com/drive/folders/1pmh1SwwtRqr5Ad_hs3j6jdF9WpR8dMIK)
* Tools & Technologies: Tableau Desktop, Tableau Public, Microsoft Excel
* Dataset Scope: Seattle Airbnb data (`airbnb_data.xlsx`) with three sheets: 3,818 property listings, 84,849 reviews and 1,048,575 calendar rows covering 4 January 2016 to 2 January 2017.

---

## Business Problem

Short-term rental hosts and property investors struggle to set nightly rates, because prices vary by location and property size and shift through the year. This dashboard puts listing prices, bedroom counts and calendar prices into one Tableau view, so hosts can compare a listing with market benchmarks before setting a price.

---

## Business Questions

Each question is answered by one view on `Dashboard 1`.

| # | Business question | View |
|---|---|---|
| 1 | Which zip codes have the highest and lowest average nightly price? | Price by Zipcode (bar chart) |
| 2 | Where are the higher-priced zip codes located? | Price per Zipcode (map) |
| 3 | How does the average price change with the number of bedrooms? | Average Price per Bedroom (bar chart) |
| 4 | How many listings are there at each bedroom size? | Distinct Count of Bedrooms Listings |
| 5 | How does the listed price of available nights change across 2016? | Revenue for Year (weekly line chart) |

---

## Key Insights

1. **Average price varies widely by zip code.** The highest averages are in 98134 ($206.6), 98119 ($171.1) and 98101 ($166.9). The lowest are in 98125 ($64.7), 98133 ($71.0) and 98106 ($76.9). Some zip codes have few listings, such as 98134 with 5, 98133 with 11 and 98125 with 14, so treat their averages with caution.
2. **Price rises steadily with size.** The average nightly price is $96.2 for one bedroom, $175.4 for two, $249.7 for three, $315.4 for four, $450.0 for five and $584.8 for six.
3. **Supply is concentrated in small units.** There are 1,811 one-bedroom listings, more than all other sizes combined (483 two-bedroom, 206 three-bedroom, 55 four-bedroom, 20 five-bedroom and 5 six-bedroom).
4. **Weekly listed prices climb through the first quarter, then stay in a narrow band.** Weekly totals rise from about 1.0 to 1.6 million in January to about 1.9 million by mid-March, then stay between 1.8 and 2.1 million for the rest of the year. The highest weeks start on 25 December (2.11 million), 19 June (2.07 million) and 18 December (2.06 million).

---

## Recommendations

1. **Use bedroom and zip-code averages as pricing benchmarks.** Compare a new listing with the average for its size and neighbourhood before setting a nightly price.
2. **Review pricing ahead of the late-December and mid-June peaks.** Those weeks carry the highest listed prices of the year.
3. **Explore larger units.** Listings with three or more bedrooms are scarce (286 listings against 1,811 one-bedroom listings) and average between $249.7 and $584.8 per night. Check occupancy data before acting, because this dashboard does not include it.

---

## Dashboard Design

| Tab | View title | Fields used | Filter |
|---|---|---|---|
| Sheet 1 | Price by Zipcode | Average `price` by `zipcode` | Excludes blank zip codes |
| Sheet 2 | Price per Zipcode | Average `price` by `zipcode` on a map | Selected zip codes only |
| Sheet 3 | Revenue for Year | Sum of Calendar `price` by week of `date` | 1 January to 31 December 2016 |
| Sheet 4 | Average Price per Bedroom | Average `price` by `bedrooms` | Excludes blank and 0 bedrooms |
| Sheet 5 | Distinct Count of Bedrooms Listings | Distinct count of listing `id` by `bedrooms` | 1 to 6 bedrooms |

The data source joins `Listings` to `Calendar` on `Listings.id = Calendar.listing_id` (inner join). The `Reviews` sheet is not used in the workbook.

---

## Data Notes

* **The Calendar sheet stops at Excel's row limit.** It covers 2,873 of the 3,818 listings, and the inner join drops the rest from every view. For example, the bedroom count view shows 2,580 listings with 1 to 6 bedrooms, while the `Listings` sheet holds 3,439.
* **Calendar `price` only exists for available nights.** Booked nights have no price, so the `Revenue for Year` view sums the listed price of available nights. It does not show realised revenue or booking activity.
* **One listing has a malformed zip code** (the value "99", a line break, then "98122"). It appears as its own bar in `Price by Zipcode` and is left out of the map.
* **Listings with 0 bedrooms** (372 in the `Listings` sheet) are excluded from the bedroom views.

---

## How to Open

1. Download `airbnb_data.xlsx` from the [Google Drive folder](https://drive.google.com/drive/folders/1pmh1SwwtRqr5Ad_hs3j6jdF9WpR8dMIK) and save it next to `airbnb_analysis.twb`.
2. Open `airbnb_analysis.twb` in Tableau Desktop.
3. The workbook stores the original file path of the data. If Tableau cannot find it, choose Edit Connection on the data source and select your local copy.

---

## Possible Next Steps

* Reload the full calendar data, for example from the original CSV, so all 3,818 listings are included.
* Rename `Revenue for Year` to match what it measures, or add booked nights to estimate revenue.
* Add occupancy and review measures to test whether higher-priced zip codes and larger units also book more often.

---

## Repository Contents

| File | Description |
|---|---|
| `airbnb_analysis.twb` | Tableau workbook with 5 worksheets and 1 dashboard |
| `README.md` | Project documentation |

The dataset (`airbnb_data.xlsx`) is hosted on Google Drive because of its size (about 43 MB).
