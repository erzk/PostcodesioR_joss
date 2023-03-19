---
# Example from https://joss.readthedocs.io/en/latest/submitting.html
title: 'PostcodesioR: An R package for UK geocoding'
tags:
  - R
  - geocoding
  - postcodes
  - UK
authors:
  - name: Eryk J. Walczak
    orcid: 0000-0001-8724-462X
    affiliation: "1" # (Multiple affiliations must be quoted)
affiliations:
 - name: University College London
   index: 1
citation_author: Walczak
date: 19 March 2023
year: 2023
bibliography: paper.bib
output: rticles::joss_article
csl: apa.csl
journal: JOSS
---

# Summary

``PostcodesioR`` is an API wrapper around ``postcodes.io``, free UK postcode look-up and geocoder. This package helps to find and transform information about UK administrative geography like postcodes, LSOA, MSOA, constituencies, counties, wards, districts, CCG or NUTS. Here, we present a new geocoding package designed specifically for the UK context, which addresses these challenges and provides accurate and reliable geocoding results for a wide range of applications.

# Statement of need

Geocoding is the process of converting location-based information such as addresses into corresponding geographic coordinates. It is a crucial step in many analytic tasks involving geographic data. However, matching UK administrative borders with corresponding postcodes has long been a challenge for researchers and practitioners alike due to the complex and ever-changing nature of the UK's administrative geography. 

The package is based exclusively on open data provided by ``postcodes.io`` using open ONS data. ``PostcodesioR`` can be used by data scientists or social scientists working with geocoded UK data. A common task when working with such data is aggregating geocoded data on different administrative levels, e.g. turning postcode-level data into counties or regions. This package can help in achieving this and in many other cases when changing the aggregation of geographic data is required.

<!-- ``Gala`` is an Astropy-affiliated Python package for galactic dynamics. Python -->
<!-- enables wrapping low-level languages (e.g., C) for speed without losing -->
<!-- flexibility or ease-of-use in the user-interface. The API for ``Gala`` was -->
<!-- designed to provide a class-based and user-friendly interface to fast (C or -->
<!-- Cython-optimized) implementations of common operations such as gravitational -->
<!-- potential and force evaluation, orbit integration, dynamical transformations, -->
<!-- and chaos indicators for nonlinear dynamics. ``Gala`` also relies heavily on and -->
<!-- interfaces well with the implementations of physical units and astronomical -->
<!-- coordinate systems in the ``Astropy`` package [@astropy] (``astropy.units`` and -->
<!-- ``astropy.coordinates``). -->

<!-- ``Gala`` was designed to be used by both astronomical researchers and by -->
<!-- students in courses on gravitational dynamics or astronomy. It has already been -->
<!-- used in a number of scientific publications [@Pearson:2017] and has also been -->
<!-- used in graduate courses on Galactic dynamics to, e.g., provide interactive -->
<!-- visualizations of textbook material [@Binney:2008]. The combination of speed, -->
<!-- design, and support for Astropy functionality in ``Gala`` will enable exciting -->
<!-- scientific explorations of forthcoming data releases from the *Gaia* mission -->
<!-- [@gaia] by students and experts alike. -->

# Examples

## Installation

This package can be installed from GitHub (developmental version) or CRAN (stable version).

In order to install ``PostcodesioR`` use one of the following commands:


```r
# stable version
install.packages("PostcodesioR")
```

or


```r
# developmental version
if(!require("devtools")) {
  install.packages("devtools")
}
devtools::install_github("ropensci/PostcodesioR")
```

## Loading

Load the package by typing


```r
library(PostcodesioR)
```

## Geocoding

Where possible, I tried to return a data frame. Unfortunately, a lot of API calls return more complex data and in those cases it is safer to use lists. The API limits the number of returned calls. Check functions' documentation for more details.

For additional information about the returned data and the function calls see the original [documentation](https://postcodes.io/docs).

The main function of this package provides information related to a given postcode


```r
lookup_result <- postcode_lookup("EC1Y8LX")

#overview
names(lookup_result)
```

```
##  [1] "postcode"                        "quality"                        
##  [3] "eastings"                        "northings"                      
##  [5] "country"                         "nhs_ha"                         
##  [7] "longitude"                       "latitude"                       
##  [9] "european_electoral_region"       "primary_care_trust"             
## [11] "region"                          "lsoa"                           
## [13] "msoa"                            "incode"                         
## [15] "outcode"                         "parliamentary_constituency"     
## [17] "admin_district"                  "parish"                         
## [19] "admin_county"                    "date_of_introduction"           
## [21] "admin_ward"                      "ced"                            
## [23] "ccg"                             "nuts"                           
## [25] "pfa"                             "admin_district_code"            
## [27] "admin_county_code"               "admin_ward_code"                
## [29] "parish_code"                     "parliamentary_constituency_code"
## [31] "ccg_code"                        "ccg_id_code"                    
## [33] "ced_code"                        "nuts_code"                      
## [35] "lsoa_code"                       "msoa_code"                      
## [37] "lau2_code"                       "pfa_code"
```

Read the package's [vignette](https://docs.ropensci.org/PostcodesioR/articles/Introduction.html) to extensive documentation of all functions used in the package.

The remaining functions are

* `bulk_postcode_lookup()`	# Bulk postcode lookup
* bulk_reverse_geocoding	# Bulk reverse geocoding
nearest_outcode	# Find the nearest outcode
nearest_outcode_lonlat # Find the nearest outcodes given longitude and latitude
nearest_postcode # Find the nearest postcode
outcode_reverse_geocoding	# Outcode reverse geocoding
outward_code_lookup	# Outward code lookup
place_lookup	# Place lookup
place_query	# Place query
postcode_autocomplete	# Postcode autocomplete
postcode_lookup	# Postcode lookup
postcode_query	# Postcode query
postcode_validation	# Postcode validation
random_place	# Generate a random place
random_postcode	# Generate a random postcode
reverse_geocoding	# Reverse geocoding
scottish_postcode_lookup	# Scottish postcode lookup
terminated_postcode	# Terminated postcode lookup


<!-- Single dollars ($) are required for inline mathematics e.g. $f(x) = e^{\pi/x}$ -->

<!-- Double dollars make self-standing equations: -->

<!-- $$\Theta(x) = \left\{\begin{array}{l} -->
<!-- 0\textrm{ if } x < 0\cr -->
<!-- 1\textrm{ else} -->
<!-- \end{array}\right.$$ -->


<!-- # Citations -->

<!-- Citations to entries in paper.bib should be in -->
<!-- [rMarkdown](http://rmarkdown.rstudio.com/authoring_bibliographies_and_citations.html) -->
<!-- format. -->

<!-- For a quick reference, the following citation commands can be used: -->
<!-- - `@author:2001`  ->  "Author et al. (2001)" -->
<!-- - `[@author:2001]` -> "(Author et al., 2001)" -->
<!-- - `[@author1:2001; @author2:2001]` -> "(Author1 et al., 2001; Author2 et al., 2002)" -->

<!-- # Rendered R Figures -->

<!-- Figures can be plotted like so: -->

<!-- ```{r} -->
<!-- plot(1:10) -->
<!-- ``` -->

# Acknowledgements

We acknowledge rOpenSci reviewers and package contributors (listed on the package's GitHub page).

# References