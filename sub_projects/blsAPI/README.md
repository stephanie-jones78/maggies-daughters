# Acquiring Data Using the BLS API
*From the [developer page](https://www.bls.gov/developers/home.htm)*<br>
## About the Bureau of Labor Statistics API
The Bureau of Labor Statistics' (BLS) Public Data Application Programming Interface (API) gives the public access to economic data from all BLS programs. 
<details>
  <summary>More</summary>The BLS Public Data API is currently available in two versions. Version 2.0 requires
  <a href='https://data.bls.gov/registrationEngine/'>registration</a>
   and allows users to access more data more frequently. Users may add calculations and annual averages to requests, and series description information is available for many BLS surveys. Version 1.0 is a more limited API that does not require registration and is open for public use.
 </details>
<br>

## Using the BLS API
 Using BLS API Signatures, developers and programmers can retrieve published historical timeseries data in JSON data-interchange or XLSX format. 
 <details>
    <summary>More</summary>
 The BLS Public API utilizes two HTTP request-response mechanisms to retrieve data: GET and POST. 
 <ul>
    <li>GET requests data from a specified source. <li>POST submits data to a specified resource to be processed. 
</ul>
The BLS Public Data API uses GET to request a single piece of information and POST for all other requests.
 </details>
 <br>

 *from the [Data API](https://www.bls.gov/bls/api_features.htm) and [BLS Data API Signatures](https://www.bls.gov/developers/api_signature_v2.htm#latest) pages*

 ## API Signature
 Using Public Data API signatures, users can consume and manipulate raw data from any of the BLS’s surveys to create a wide range of applications. All signatues must include:
Signature Element | Example | Optional
:-- | :-- | :--
HTTP Type | GET or POST
RESTful URL | (*json output*) https://api.bls.gov/publicAPI/v2/timeseries/data/ (*Excel output*) https://api.bls.gov/publicAPI/v2/timeseries/data/.xlsx
Series ID (*payload*) | `LAUCN040010000000005`| at least x1 

Sample json response
```
{"status": "REQUEST_SUCCEEDED", 
    "responseTime": 16,
    "message": [
        ],
    "Results": [
        {
        "series": [
            {
          "seriesID": "LAUCN040010000000005",
          "data": [
            {
              "year": "2013",
              "period": "M11",
              "periodName": "November",
              "value": "16393",
              ...
}
```
Breaking down the response . . .
Keyword | Data Type | Description
:-- | :-- | :--
*json response* | Dictionary | json response
**status** | str | *response key*, request status
**responseTime** | int | *response key*, request time
**message** | list | *response key*
**Results** | list with a dictionary | *response key*, list of with a dictionary (*series is the dictionary key*)
series | list of seriesID dictionaries | *Results key*
seriesID | key | *series key*
data | list of dictionaries | series data

<hr>
You can also include parameters in the passed URL query string.

```
#######################################
# Example URL Query String with Parameters
#######################################

https://api.bls.gov/publicAPI/v2/timeseries/data/
?registrationkey=000f4e000f204473bb565256e8eee73e
&catalog=true
&startyear=2010
&endyear=2014
&calculations=true 
&annualaverage=true
&aspects=true
```

<details>
 <summary>Query Parameters</summary>

Parameter | Description | Optional
 :-- | :-- | :--
`registrationkey` | 
`startyear` | 
`endyear` | 
`calculations` | 
`annualaverage` | 
`catalog` | 
`aspects` | 

 </details>

- [Sample Python Code](https://www.bls.gov/developers/api_python.htm#python2) 
- [Freq Asked Questions](https://www.bls.gov/developers/api_faqs.htm#signatures1)
- [Series Keyword Search](https://beta.bls.gov/dataQuery/find?st=0&r=20&s=popularity%3AD&more=0)
- [**seriesID prefix links**](https://download.bls.gov/pub/time.series/) *and* [***seriesID prefix meanings***](https://download.bls.gov/pub/time.series/overview.txt)

<details>
    <summary>seriesID Link Directory Structure</summary>

*xX = seriesID prefix*

fileName | Description
:-- | :--
`xX.series` | series-level data
`xX.data.0-n` | observational data
`xX.map` | survey-specific specific mapping files, which relate codes to meaningful names ((i.e. xX.industry, xX.area, etc...))
`xX.text` *or* `xX.doc`| Documentation for individual surveys, including a survey description, the table structure, information on data partitioning, and definitions of data elements. Documentation includes the following:
1. **Survey Description:** *Description of survey and data available*
2. **Summary of Data:** *Description of available data elements and their characteristics*
3. **Freq of Observation:** *The frequency of various data series available for that particular survey (quarterly, monthly, etc.*
4. **Data Characteristics:** *Value of various data series for that particular survey*
5. Updating Schedule: *Freq new data available on LABSTAT*
6. **File Structure and Format:** *List of files available and what they contain*
7. **Element Defintions:** *Defined list of the elements for each survey*

</details>

