*DIRECTORIES*

ASFR
- urban and rural subnational age specific fertility rates (ASFRs)
- Excel spreadsheet for each country, each containing separate sheets for urban and rural data
- Region names in first row, age bands in first column
- Data obtained from Andy Tatem, via email
- Need to ensure region names match with DHS polygons (see dhsBoundaries.gdb)

GRUMP2010-global
- GRUMP population distribution raster
- Data obtained from Andy Tatem, via Google Drive
- LZW compression applied to TIFF file to reduce file size

ne_10m_populated_places
- shapefile giving point locations of towns and cities
- Natural Earth 1:10m data
- downloaded from: http://www.naturalearthdata.com/downloads/10m-cultural-vectors/10m-populated-places/

urban
- GRUMP urban extents
- obtained from Andy Tatem, via Google Drive
- polygons for South Sudan and Papua New Guinea added later, obtained from Andy Tatem via email

WorldPop
- WorldPop population distribution rasters
- available from: http://www.worldpop.org.uk/data/
- data extracted from archives using 7-zip
- LZW compression applied to TIFF files to reduce file size
- script used to apply compression: code/compress_tiffs.py
- data sorted into directories by country, directory name is the 3 letter ISO code

Zanzibar
- Shapefile defining boundary of Zanzibar
- obtained from Andy Tatem, via email


*DATABASES*

adminBoundaries.gdb
- Global Administrative Unit Layers (GAUL), produced by the UN Food and Agriculture Organisation (FAO)
- downloaded from: http://fenixapps2.fao.org/GAUL/GAUL2014_Level_2/g2014_2010_2.zip
- dataset created in 2014
- represents admin level 2 boundaries from 2010
- 3 letter ISO codes added by joining to a table of country codes used by UN FAO, downloaded from: http://data.fao.org/places
- Some ISO codes had to be added manually, as there was no match in the join table
- dissolved by ISO code to create feature class of country boundaries

adminBoundaries.sqlite
- adminBoundaries.gdb converted to SpatiaLite format

asfr.gdb
 - Age Specific Fertility Rates imported from Excel spreadsheet to file geodatabase using code/import_asfr_data.py
 - Stripped leading and trailing whitespace from region names
 - Added REG_ID from dhsBoundaries.gdb/subnational_boundaries by Joining on region name, level rank and iso code
 - Some REG_ID codes had to be manually added

asfr_template.gdb
- contains an empty file geodatabase table, used as a template for converting ASFR spreadsheets to file geodatabase tables

dhsBoundaries.gdb
- District Household Survey boundaries
- downloaded from: http://spatialdata.measuredhs.com/boundaries.html
- merged into a single feature class
- added additional (made up) REG_ID codes where they were missing

GrowthRates.gdb
- UN estimates of urban and rural growth rates by country
- data obtained from Andy Tatem, via Google Drive, in Excel format
- excel spreadsheets converted to file geodatabase tables
- added 2 letter ISO codes by joining with countryCodes.csv
- Some ISO codes had to be added manually, as there was no match in the join table

lsib-wvs.gdb
- US Office of the Geographer’s Large Scale International Boundary Lines and World Vector Shorelines (LSIB-WVS) datasets combined to form boundary polygons
- shapefiles downloaded from: https://hiu.state.gov/data/data.aspx
- merged into single FGDB feature class

popByAgeGroup.gdb
- proportion of each countries population in 5-year age bands
- only data for Africa is currently available
- data obtained from Andy Tatem, via Google Drive
- converted from shapefile to file geodatabase feature class


*FILES*

All-countries-births-by-year.xls
- UN estimates of numbers of births for each individual year 2010-2035 by country
- obtained from Andy Tatem, via email
- added 3 letter ISO codes, by joining with countryCodes.csv
- Some ISO codes had to be added manually, as there was no match in the join table

asfr_lookup.csv
- defines the location of the ASFR data for each country
- contains 2 letter ISO code for each country (iso2),
  filename of the ASFR spreadsheet (asfr_xlsx_filename),
  and level of admin boundaries to use (levelrnk)

Births-to-pregnancies-multipliers.xlsx
- Multipliers used to convert estimated number of births to estimated numbers of pregnancies
- obtained from Andy Tatem, via email
- added 3 letter ISO codes, by joining with countryCodes.csv
- Some ISO codes had to be added manually, as there was no match in the join table
- Blank value for South Sudan replaced with value for Sudan
- Added value for Timor Leste, copied from Indonesia
- Added value for Uzbekistan, copied from Turkmenistan

countryCodes.csv
- lookup table of country names and associated ISO codes
- data taken from: http://download.geonames.org/export/dump/countryInfo.txt

POPULATION_BY_AGE_FEMALE.xls
- UN estimates of numbers of women of childbearing age by 5-yr age group per country
- obtained from Andy Tatem, via Google Drive

WPP2012_DB02_POPULATIONS_ANNUAL.CSV
- UN estimates of population by country
- data downloaded from: http://esa.un.org/wpp/ASCII-Data/DISK_NAVIGATION_ASCII.htm

WPP2012_DB04_POPULATION_BY_SEX_ANNUAL.CSV
- UN estimates of population by country, broken down by sex and 5-year age bands
- data downloaded from: http://esa.un.org/wpp/ASCII-Data/DISK_NAVIGATION_ASCII.htm

WPP2012_POP_F02_POPULATION_GROWTH_RATE.XLS
- UN estimates of population growth rates by country
- data downloaded from: http://esa.un.org/unpd/wpp/Excel-Data/population.htm