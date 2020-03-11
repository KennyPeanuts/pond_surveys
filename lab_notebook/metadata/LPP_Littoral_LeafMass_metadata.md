# Metadata for the Leaf Mass for Littoral LPP

## Files

"LPP_Littoral_LeafMass.csv"

## Metadata

* Collected by: KF and JH

* Collected on: 13 July 2016

* Affiliation: Longwood University

* Location: Lancer Park Pond

### Description

These data are on the mass of leaf litter collected from the littoral zone of the pond. Briefly, a Hess sampler was placed adjacent to shore and all of the leaf litter was removed down to the sediment surface.  

The litter was then dried in a pre-weighed paper bag and weiged to determine the dry mass of the litter. Once the dry mass was determined, the litter was ground and distributed into ceramic crucibles to determine LOI to get AFDM. Since there was so much litter, it had to be distributed into lots of crucibles and this proved impracticle. Futhermore, errors in the lab meant that some of the dry mass of the leaf matter in the crucibles was not measured before ashing.

To deal with this issue, I used the litter that was collected for ergosterol AFDM measurements to determine the % OM of the samples from that site, this value was then applied to the dry mass of the bulk litter to estimate the AFDM.

To get the AFDM samples, 5 representative leaves were removed from the sample at each site and a #5 leaf disc was punched from each leaf. The 5 leaf discs were then placed into pre-weighed crucibles and %OM was determined via LOI for 5 h at 550 dC.

More details are in the lab notes:

[https://github.com/KennyPeanuts/pond_surveys/blob/master/lab_notebook/lab_notes/Lancer_Pk_Pond_Sampling_13July2016.md](https://github.com/KennyPeanuts/pond_surveys/blob/master/lab_notebook/lab_notes/Lancer_Pk_Pond_Sampling_13July2016.md)


## Variables

* Pond = the abbreviation for the pond name
  * LPP = Lancer Park Pond
  
* Date = the date the field sampling was completed (YYYY-MM-DD)

* Site = the area that the sample was taken from - also denoted the bag name
  * A = along the N shore of the pond
  * B = along the E shore of the pond adjacent to the flood plain
  * C = along the S shore of the pond

* BagNum = the number of the bag used to dry the litter

* BagMass = the mass of the dry and empty bag (g)

* BagLeafMass = the mass of the bag plus the dried litter (g)

* LeafDryMass = the dry mass of the leaf litter (g)

* CrucNum = the number of the crucible that was used for the LOI measurement.

* CrucMass = the mass of the crucible that was used for the LOI measurement (g).

* CrucLeafMass = the mass of the crucible and leaf discs after drying for 48 h at 50 dC (g).

* CrucAshMass = the mass of the crucible and the material remaining after ashing for 5 h at 550 dC (g).

* LOIDryMass = the dry mass of the leaf discs in the crucible (g).

* LOIAshMass = the mass of the ash in the crucible (g).

* LOIAFDM = the mass of the leaf discs minus ash (g).

* propOM = the proportion of organic matter in the leaf sample.

## Data Entry
### Littoral LOI Data

    Pond <- rep("LPP", 4)
    Date <- as.POSIXct(rep("2016-07-11", 4)) 
    Site <- c("A", "B", "B", "C")
    BagNum <- c(12, 13, 14, 15)
    BagMass <- c(7.0058, 7.3515, 7.3624, 7.3997)
    BagLeafMass <- c(123.5000, 52.0744, 52.8338, 29.9218)
    LeafDryMass <- BagLeafMass - BagMass
    CrucNum <- c(9, 11, NA, 12)
    CrucMass <- c(11.6691, 11.8900, NA, 11.7840)
    CrucLeafMass <- c(11.6886, 11.9086, NA, 11.8044)
    CrucAshMass <- c(11.6714, 11.8933, NA, 11.7855)
    LOIDryMass <- CrucLeafMass - CrucMass
    LOIAshMass <- CrucAshMass - CrucMass
    LOIAFDM <- LOIDryMass - LOIAshMass
    propOM <- LOIAFDM / LOIDryMass
     
#### Create LOI data.frame and file
     
     LPPLittoralLeafMass <- data.frame(Pond, Site, Date, BagNum, BagMass, BagLeafMass, LeafDryMass, CrucNum, CrucMass, CrucLeafMass, CrucAshMass, LOIDryMass, LOIAshMass, LOIAFDM, propOM)
     
     write.table(LPPLittoralLeafMass, file = "./data/LPP_Littoral_LeafMass.csv", quote = F, row.names = F, sep = ",")
     