## Problem Statement
At Ames Realty, we want to maximize our revenues. How can we use the Ames housing data to best do that?

This project aims to explore two vectors on which to improve profitability:
1) what factors contribute to increasing home sale price?
2) can we build a model to accurately predict home sale price so our agents neither undersell a home nor scare away prospective buyers with overly aggressive asking prices? If so, what does that model look like?

## Data Dictionary
### All data is from the Ames Housing data set. 
Additional details, in particular, keys for understanding object data, can be found [jse.amstat.org](http://jse.amstat.org/v19n3/decock/DataDocumentation.txt). Descriptions of data is taken from this site.

|Feature|Type|Description|
|---|---|---|
|id|int|observation number|
|pid|int|Parcel identification number  - can be used with city web site for parcel review.|
|ms_subclass|int|Identifies the type of dwelling involved in the sale.|Identifies the general zoning classification of the sale.|
|ms_zoning|object|Identifies the general zoning classification of the sale.|
|lot_frontage|float|Linear feet of street connected to property.|
|lot_area|int|Lot size in square feet.|
|street|object|Type of road access to property.|
|alley|object|Type of alley access to property.|
|lot_shape|object|General shape of property.|
|land_contour|object|Flatness of the property.|
|utilities|object|Type of utilities available.|
|lot_config|object|Lot configuration.|
|land_slope|object|Slope of property.|
|neighborhood|object|Physical locations within Ames city limits (map available).|
|condition_1|object|Proximity to various conditions.|
|condition_2|object|Proximity to various conditions (if more than one is present).|
|bldg_type|object|Type of dwelling.|
|house_style|object|Style of dwelling.|
|overall_qual|int|Rates the overall material and finish of the house.|
|overall_cond|int|Rates the overall condition of the house.|
|year_built|int|Original construction date.|
|year_remod/add|int|Remodel date (same as construction date if no remodeling or additions).|
|roof_style|object|Type of roof.|
|roof_matl|object|Roof material.|
|exterior_1st|object|Exterior covering on house.|
|exterior_2nd|object|Exterior covering on house (if more than one material).|
|mas_vnr_type|object|Masonry veneer type.|
|mas_vnr_area|float|Masonry veneer area in square feet.|
|exter_qual|object|Evaluates the quality of the material on the exterior.|
|exter_cond|object|Evaluates the present condition of the material on the exterior.|
|foundation|object|Type of foundation.|
|bsmt_qual|object|Evaluates the height of the basement.|
|bsmt_cond|object|Evaluates the general condition of the basement.|
|bsmt_exposure|object|Refers to walkout or garden level walls.|
|bsmtfin_type_1|object|Rating of basement finished area.|
|bsmtfin_sf_1|float|Type 1 finished square feet.|
|bsmtfin_type_2|object|Rating of basement finished area (if multiple types).|
|bsmtfin_sf_2|float|Type 2 finished square feet.|
|bsmt_unf_sf|float|nfinished square feet of basement area.|
|total_bsmt_sf|float|Total square feet of basement area.|
|heating|object|Type of heating.|
|heating_qc|object|Heating quality and condition.|
|central_air|object|entral air conditioning.|
|electrical|object|Electrical system.|
|1st_flr_sf|int|First Floor square feet.|
|2nd_flr_sf|int|Second floor square feet.|
|low_qual_fin_sf|int|Low quality finished square feet (all floors).|
|gr_liv_area|int|Above grade (ground) living area square feet.|
|bsmt_full_bath|float|Basement full bathrooms.|
|bsmt_half_bath|float|Basement half bathrooms.|
|full_bath|int|Full bathrooms above grade.|
|half_bath|int|Half baths above grade.|
|bedroom_abvgr|int|Bedrooms above grade (does NOT include basement bedrooms).|
|kitchen_abvgr|int|Kitchens above grade.|
|kitchen_qual|object|Kitchen quality.|
|totrms_abvgrd|int|Total rooms above grade (does not include bathrooms).|
|functional|object|Home functionality (Assume typical unless deductions are warranted).|
|fireplaces|int|Number of fireplaces.|
|fireplace_qu|object|Fireplace quality.|
|garage_type|object|Garage location.|
|garage_yr_blt|object|Year garage was built.|
|garage_finish|object|Interior finish of the garage.|
|garage_cars|object|Size of garage in car capacity.|
|garage_area|object|Size of garage in square feet.|
|garage_qual|object|Garage quality.|
|garage_cond|object|Garage condition.|
|paved_drive|object|Paved driveway.|
|wood_deck_sf|int|Wood deck area in square feet.|
|open_porch_sf|int|Open porch area in square feet.|
|enclosed_porch|int|Enclosed porch area in square feet.|
|3ssn_porch|int|Three season porch area in square feet.|
|screen_porch|int|Screen porch area in square feet.|
|pool_area|int|Pool area in square feet.|
|pool_qc|object|Pool quality.|
|fence|object|Fence quality.|
|misc_feature|object|Miscellaneous feature not covered in other categories.|
|misc_val|int|$\Value of miscellaneous feature.|
|mo_sold|int|Month Sold (MM).|
|yr_sold|int|Year Sold (YYYY).|
|sale_type|object|Type of sale.|
|saleprice|int|Sale price $\$\.|

## Brief Summary of Analysis

The data was cleaned, dealing with null values. To see if the simple presence of a feature played a meaningful role, a number of 'has_(FEATURE)' columns were made based on data from other columns. Ratings were converted to numerical scales to aid in analysis. A heatmap of correlations helped to identify which numerical values show the highest correlation to the sale price.

At that point, the data scientist used an iterative process, starting with the several selections of the highest correlated numerical values, then adding interaction terms (features engineered by multiplying other terms or squaring existing terms). After that, categorical features we're added to the model in multiple combinations. Finally, ridge and LASSO models were applied to the features that had proven to produce the best model.

## Conclusions and Recommendations:
The Ames Realty Company can increase revenue through concrete recommendations to homeowners preparing to sell and by providing sales agents with access to a sale price estimator powered by Model 4 (Ridge Model). In addition, further data should be collected.

### Recommendations to Homeowners Preparing to Sell
The following factors were found to affect the price of the home, based on Model 1. All else held equal, one unit increase of each of the following will provide approximately these dollar increases in the sale price of a home. 

Please note that some items appear out of the homeowner's hand (for example, the year a home was built can't be changed), though even these suggest that a homeowner who's interested in selling will likely benefit from selling sooner, while the house is newer. The benefit of other items may not be worth the: for example, the cost of adding an additional full-bathroom to a house will far exceed the marginal benefit to the sale price, all else held equal, of approximately $1179.58.

|Feature|Increase in $ (2010) per 1 unit of improvement in feature (all else held equal)|Notes|
|---|---|---|
|Exterior Quality|$14867.19|Rating of the quality of the materials used on the exterior, 5 point scale|
|Overall Quality|$12652.20|Rating of the overall material and finishes, 10 point scale|
|Kitchen Quality|$12561.85|Rating of the quality of the kitchen, 5 point scale|
|Garage No. of Cars|$6713.47|Number of cars the garage can fit|
|Has Fireplace|$6616.07|If the house has a fireplace or not|
|Fireplaces|$5467.41|The number of fireplaces|
|Total Rooms Above Ground|$2530.01|The total number of rooms above ground|
|Heating Quality|$2321.84|Rating of the quality of the heating, 5 point scale|
|Full Bath|$551.46|The number of full bathrooms|
|Year of last Remodel or Addition|$171.21|
|Year Built|$117.98|The year the home was built|
|Masonry Veneer Area|$34.58|Square footage of masonry veneer|
|Above Ground Living Area|$29.20|Square footage of living area above ground|
|Garage Area|$21.76|Total area of garage, sq. ft.|
|Area of Main Finished Basement Type|$15.73|Square footage of the primary type of finished basement space|
|First Floor Area|$10.33|Square footage of the first floor|
|Total Basement Area|$9.46|Square footage of the basement|
|Garage Year Built|8.47|Year garage was built|

### Recommendations for Sales Agents
The Ames Realty Company should build a calculator for its sales agents to estimate the sale price of homes using the above factors. This calculator should be powered by Model 4 (Ridge), which produced strong predictions by several metrics, including the best Root Mean Squared Error (RMSE) of all the models. This model's RMSE of 21354.80 dollars beat the baseline RMSE of $\75922.17 by $54,567., a significant improvement. In other words, roughly speaking, Model 4 (Ridge) was on average about $54,000 more accurate than the baseline, which was calculated from the mean of the home prices.

It's worth noting that the model appears to be more accurate under the $300,000 mark, perhaps because it has more data for houses under that price range.

### Collect Additional Data
The data set we worked from was pre-2010. Undoubtedly, the market has changed and we should collect updated data.

Even if collecting everything from the dataset isn't feasible, collecting the above data on the homes Ames Realty sells would be helpful, too, to update the valuation of the change in prices to be expected from those improvements. 

In addition, it would be valuable to collect the estimates of expert sales agents to see how they compare to the model. Does the model outperform the expert sales agents or are the expert sales agents able to outperform the model? The example of art experts detecting a forged Greek sculpture that had defeated more "scientific" methods shared in Malcolm Gladwell's "Blink" comes to mind ([summary here](https://www.gradesaver.com/blink/study-guide/summary-introduction-the-statue-that-didnt-look-right)). If the experts outperform the model, can we use their guidance to further improve the model?