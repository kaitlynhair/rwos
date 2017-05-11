# R interface with Web of Science Web Services API

[![Travis-CI Build Status](https://travis-ci.org/juba/rwos.svg?branch=master)](https://travis-ci.org/juba/rwos)
[![CRAN_Status_Badge](http://www.r-pkg.org/badges/version/rwos)](http://cran.r-project.org/package=rwos)

**Note :** Only the Lite version of the API is accessible for now.

## Installation

Not on CRAN, install directly from GitHub :

```r
install.packages("devtools")  # if required
devtools::install_github("juba/questionr")
```
    
## Usage

First, you need to authenticate against the service and get a session identifier. Username and password are not required as the Lite API is freely available.

```r
library(rwos)
sid <- wos_authenticate()
```
  
You can the use this session id to run search queries with `wos_search` :

```r
res <- wos_search(sid, "AU=Wickham Hadley")
```

This will display the number of results found. You can then retrieve all records from this search results with `wor_retrieve_all` :

```r
pubs <- wos_retrieve_all(res)
```

Or just a fraction of them with `wos_retrieve` :

```r
pubs <- wos_retrieve(res, first = 10, count = 15)
```

The result is a tibble (a data frame) with the different records fields as columns. 
    
## API

Only the Lite version of the API is accessible for now, which means :

- Access without authentication
- Limited set of returned data
- Records retrieving limited to batches of 100

## Links

Lite API technical documentation : http://ipscience-help.thomsonreuters.com/wosWebServicesLite/WebServicesLiteOverviewGroup/Introduction.html

General API FAQ : http://ip-science.interest.thomsonreuters.com/data-integration

Sample data : http://ip-science.interest.thomsonreuters.com/sample-data/?elqTrackId=4face30b453a4df981d9135a688b4868&elqaid=3746&elqat=2