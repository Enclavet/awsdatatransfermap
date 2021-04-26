# AWS Data Transfer Map

## Description
HTML5 application that shows data transfer costs on AWS visually on a map. The application allows for changing the region and country (for edge pricing). 

## Discounts
Some customers recieve discounts from AWS and the map can be updated to include those discounts. 

Discounts are defined in the following format:
```
//Discounts
// Format: 
//    discounts[datatype].rate will set the rate across all selectors (region/cloudfront location)
//    discounts[datatype].percentage will give a discount across all selectors (region/cloudfront location).
//    discounts[datatype][selector].percentage will give a discount based on a percentage of public pricing.
//    discounts[datatype][selector].rate will set the rate of the service.
// datatypes: crossAZ,internetOut,albInOut,clbInOut,dcOut,crossRegion,cloudfrontAWS,cloudfrontOut
// selectors: based on the datatype. Either region or cloudfront location.
```

You can include those discounts by either uploading a file with the discounts using the format mentioned above or including the above discounts in the HTML5 source in the empty function setDiscounts().

```
function setDiscounts() {
  // indicates the rate of cloundfrontOut for United States locations is is 10 cents/GB.
  discounts["cloudfrontOut"]["United States"].rate = 0.1; 
  
  // indicates the rate of internetOut for US East (N. Virginia) is 10 cents/GB.
  discounts["internetOut"]["US East (N. Virginia)"].rate = 0.1; 
  
  // indicates a 50% discount for all crossAZ traffic.
  discounts["crossAZ"].percentage = 0.5; 
}
```
