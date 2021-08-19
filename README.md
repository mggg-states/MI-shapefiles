# Michigan Election Shapefile
This shapefile was obtained from the Michigan Department of State and processed by members of the Metric Geometry and Gerrymandering Group (MGGG).

## Sources
The precinct and congressional district shapefiles  come from the Michigan Department of State through the [State of Michigan GIS Open Data Portal](http://gis-michigan.opendata.arcgis.com/datasets/2016-voting-precincts). Demographic data at the block level are from [IPUMS NHGIS](https://www.nhgis.org). Shapefiles for Michigan’s state house and senate districts were downloaded from the US Census Bureau’s [TIGER/Line Program](https://www.census.gov/cgi-bin/geo/shapefiles/index.php). Precinct level election data for 2016 were obtained from the [MIT Elections Data and Science Lab](https://electionlab.mit.edu). Precinct level election data for 2018 were obtained from the Michigan Department of State.

## Processing
Election data from the MIT Elections Data and Science Lab was cleaned by MGGG staff in order to join it to the 2016 precinct shapefile. Demographic data were aggregated from the block level to precincts using [MGGG’s proration software](https://github.com/mggg/maup). Congressional, house, and senate district IDs were assigned to precincts also using this package.

## Metadata
* `VTD2016_x`:  Precinct ID
* `ShapeSTLen`: Precinct perimeter in meters
* `CountyFips`: County FIPS code
* `Jurisdicti`: Jurisdiction FIPS code
* `ElectionYe`: Election year 
* `Label`: Jurisdiction name
* `VTD`: Precinct ID
* `county_nam`: County name
* `county_fip`: County FIPS code with state FIPS code
* `county_lat`: County internal point of latitude
* `county_lon`: County internal point of longitude
* `jurisdic_1`: Jurisdiction name
* `precinct`: Precinct name
* `PRES16D`: Number of votes for 2016 Democratic presidential candidate
* `PRES16R`: Number of votes for 2016 Republican presidential candidate
* `PRES16L`: Number of votes for 2016 Libertarian presidential candidate
* `PRES16G`: Number of votes for 2016 Green Party presidential candidate
* `GOV18D`: Number of votes for 2018 Democratic Governor candidate
* `GOV18R`: Number of votes for 2018 Republican Governor candidate
* `SEN18D`: Number of votes for 2018 Democratic Senate candidate
* `SEN18R`: Number of votes for 2018 Republican Senate candidate
* `SOS18D`: Number of votes for 2018 Democratic Secretary of State candidate
* `SOS18R`: Number of votes for 2018 Republican Secretary of State candidate
* `AG18D`: Number of votes for 2018 Democratic Attorney General candidate
* `AG18R`: Number of votes for 2018 Republican Attorney General candidate
* `TOTPOP`: Total population 
* `NH_WHITE`: White, non-hispanic, population
* `NH_BLACK`: Black, non-hispanic, population
* `NH_AMIN`: American Indian and Alaska Native, non-hispanic, population
* `NH_ASIAN`: Asian, non-hispanic, population
* `NH_NHPI`: Native Hawaiian and Pacific Islander, non-hispanic, population
* `NH_OTHER`: Other race, non-hispanic, population
* `NH_2MORE`:Two or more races, non-hispanic, population
* `HISP`: Hispanic population
* `H_WHITE`: White, hispanic, population
* `H_BLACK`: Black, hispanic, population
* `H_AMIN`: American Indian and Alaska Native, hispanic, population
* `H_ASIAN`: Asian, hispanic, population
* `H_NHPI`: Native Hawaiian and Pacific Islander, hispanic, population
* `H_OTHER`: Other race, hispanic, population
* `H_2MORE`:Two or more races, hispanic, population
* `VAP`: Total voting age population
* `HVAP`: Hispanic voting age population
* `WVAP`: White, non-hispanic, voting age population
* `BVAP`: Black, non-hispanic, voting age population
* `AMINVAP`: American Indian and Alaska Native, non-hispanic, voting age population
* `ASIANVAP`: Asian, non-hispanic, voting age population
* `NHPIVAP`: Native Hawaiian and Pacific Islander, non-hispanic, voting age population
* `OTHERVAP`: Other race, non-hispanic, voting age population
* `2MOREVAP`: Two or more races, non-hispanic, voting age population
* `CD`: 2011 enacted US congressional district ID
* `HDIST`: 2011 enacted state house district ID
* `SENDIST`: 2011 enacted state senate district ID

## Projection
This shapefile uses a Lambert Conformal Conic/State Plane projection centered on central Michigan (EPSG:6493).

## Rating
We give this shapefile an A rating. All data were obtained from the state government and were processed by MGGG staff.

# Michigan Dual Graph
A properly connected dual graph used for running GerryChain can be found in the file `michigan_dualgraph.json`. It follows the state guidlines that island precincts be considered contiguous to their county on the mainland. This dual graph differs from a dual graph that GerryChain builds from this repository's shapefile in the following ways (see below for exact edges deleted):
- an extraneous edge between Grosse Ile and Soo Township has been removed (Detroit area should not be connected to Upper Peninsula)
- an edge connecting Grosse Ile to Wayne County has been replaced with edges that correctly run along bridges off the island

If planning to run GerryChain on this shapefile, we suggest loading this graph via `Graph.load_json()` instead of creating a graph from `Graph.from_file()` and saving that graph locally for further use.

### Changed edges by `VTD`
- (P0337462000001, P1633542000002) removed
- (P1633542000005, P1631122000008) removed
- (P1633542000002, P1638042000001) added
- (P1633542000002, P1636888000001) added
