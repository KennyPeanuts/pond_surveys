# Metadata for the data to determine the mass of the littoral CPOM in Daulton Pond

## File

`DP_Litt_CPOM_LeafMass.csv`

## Metadata

* Collected by: KF and JH

* Collected on: 22 June 2016

* Affiliation: Longwood University

* Location: Dalton Pond

### Description

These samples were collected to determine the LOI of CPOM in the littoral portions of Daulton Pond. The sampling notes can be found in [https://github.com/KennyPeanuts/pond_surveys/blob/master/lab_notebook/lab_notes/Daulton_Pond_Sampling_22Jun2016.md](https://github.com/KennyPeanuts/pond_surveys/blob/master/lab_notebook/lab_notes/Daulton_Pond_Sampling_22Jun2016.md).

Briefly:

In three littoral locations around the pond the organic matter of the littoral zone was sampled by placing a Hess Sampler (32.5 cm diam.) into the benthos of the littoral zone approximately 2 m from the shore, taking care to work between the vegetation.

Once the sampler was in place, we removed all the CPOM on the surface of the sediments down to the sediment layer or down approximately 10 cm if the sediment layer was not obvious. 

The removed CPOM was placed into a resealable plastic bag and returned to the lab on ice where it was placed in the refrigerator for 48 h prior to sorting and sampling. The samples were then gently rinsed and sorted into "terrestrial litter", "reed litter", or "typha litter" and then dried in a pre-weighed paper bag at 50 dC for >48 h. Once dry the litter was ground and placed into pre-weighed ceramic crucibles and ashed at 550 dC for >4 h to determine LOI.

NOTE: These data are only for the standing stock determination. The litter LOI data can be found [https://github.com/KennyPeanuts/pond_surveys/blob/master/lab_notebook/data/DP_Litt_CPOM_LOI.csv](https://github.com/KennyPeanuts/pond_surveys/blob/master/lab_notebook/data/DP_Litt_CPOM_LOI.csv).

## Variables

* Pond = the abbreviation for the pond name
  * DP = Daulton Pond
  
* Date = the date the field sampling was completed (YYYY-MM-DD)

* Site = the area that the sample was taken from
  * A = Cattails
  * B = Open
  * C = Reed
  
* OM.Type = type of OM that was found in the sample
  * T = Terrestrial 
  * R = Reed
  * C = Cattail

* BagNum = the number paper bag that was used for the sample

* BagMass = the weight of the empty paper bag (g)

* BagLeafDM = the weight of the bag and CPOM dry mass (g)

* HessDiam = the diameter of the Hess Sampler (cm)

* HessArea = the surface area of the inside of the Hess Sampler (cm2)

* LeafStandingStock = the mass of CPOM per m2 (g/m2)

## Data Entry
### Entered variables

    Pond <- rep("DP", 8)  
    Date <- rep("2016-06-22", 8)
    Site <- c("B", "B", "B", "C", "C", "A", "A", "A")
    OM.Type <- c("T", "C", "R", "T", "R", "T", "R", "C")
    BagNum <- 1:8
    BagMass <- c(7.3365, 7.3180, 7.3700, 7.4796, 7.4610, 7.4787, 7.4915, 7.4505)
    BagLeafDM <- c(113.4, 7.2972, 7.3889, 10.1897, 31.8626, 7.5438, 7.5273, 32.9637)
    HessDiam <- 32.5
    
### Calculated variables
    
    LeafMass <- BagLeafDM - BagMass
    HessArea <- pi * ((HessDiam * 0.5)^2)
    LeafStandingStock <- (LeafMass / HessArea) * 10000 # multiplication by 10000 converts from cm-2 to m-2 with 10000 cm2 per m2

### Create data.frame
    
    leaf <- data.frame(Pond, Date, Site, OM.Type, BagNum, BagMass, BagLeafDM, LeafMass, HessDiam, HessArea, LeafStandingStock)

## Write Data File
    
    write.table(leaf, "./data/DP_Litt_CPOM_LeafMass.csv", row.names = F, quote = F, sep = ",")
    