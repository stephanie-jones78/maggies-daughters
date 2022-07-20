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
 - 
 
<details>
 <summary>Query Parameters</summary>

Parameter | Description | Optional
 :-- | :-- | :--
`registrationkey` | 
`startyear`
`endyear`
`calculations`
`annualaverage`
`catalog`
`aspects`

 </details>


