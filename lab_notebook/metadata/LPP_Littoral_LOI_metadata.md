# Metadata for the AFDM for Littoral LPP

## Files

"LPP_Littoral_LOI.csv"

## Metadata

* Collected by: KF and JH

* Collected on: 13 July 2016

* Affiliation: Longwood University

* Location: Lancer Park Pond

### Description

These data are on the AFDM of leaf litter collected from the littoral zone of the pond. Briefly, a Hess sampler was placed adjacent to shore and all of the leaf litter was removed down to the sediment surface.  

The litter was then dried in a pre-weighed paper bag and weiged to determine the dry mass of the litter. Once the dry mass was determined, the litter was ground and distributed into ceramic crucibles to determine LOI to get AFDM. Since there was so much litter, it had to be distributed into lots of crucibles and this proved impracticle. Futhermore, errors in the lab meant that some of the dry mass of the leaf matter in the crucibles was not measured before ashing.

As a result these data are not useful and are not being used

More details are in the lab notes:

[https://github.com/KennyPeanuts/pond_surveys/blob/master/lab_notebook/lab_notes/Lancer_Pk_Pond_Sampling_13July2016.md](https://github.com/KennyPeanuts/pond_surveys/blob/master/lab_notebook/lab_notes/Lancer_Pk_Pond_Sampling_13July2016.md)


## Variables

* Pond = the abbreviation for the pond name
  * LPP = Lancer Park Pond
  
* Date = the date the field sampling was completed (YYYY-MM-DD)

* Site = the area that the sample was taken from - also denoted the bag name
  * A = along the N shore of the pond
  * B = along the E shore of the pond adjacent to the flood plain


* CrucNum = the number crucible that was used for the sample

* CrucMass = the weight of the crucible (g)

* CrucLeafMass = the weight of the crucible and CPOM dry mass (g)

* CrucAshMass = the weight of the crucible and ash mass (g)

* AshMass = the mass of the material remaining in the crucible after ashing for 5 h at 550 d (g)

* LeafDryMass = the dry mass of the leaf litter (g)

* AFDM = the mass of the material that was combusted during ashing for 5 h at 550 d. Determined by subtraction (g).

* LeafPropOM = the proportion of OM in the leaf litter.

## Data Entry
### Littoral LOI Data

    Pond <- rep("LPP", 31)
    Date <- as.POSIXct(rep("2016-07-11", 31)) 
    Site <- c(rep("B", 25), rep("A", 5), "B") 
    CrucNum <- c(4, 5, 7, 8, 10, 13, 14, 16, 17, 18, 20, 21, 22, 23, 24, 1, 2, 3, 4, 5, 6, 7, 4, 5, 7, 8, 10, 13, 14, 16, 17)
    CrucMass <- c(27.4900, 30.3834, 28.2014, 28.9698, 29.7535, 29.7296, 28.2211, 28.8758, 30.5173, 28.4395, 29.1412, 31.0051, 26.9362, 28.8192, 29.4000, 13.1364, 12.6381, 13.0677, 12.2478, 12.9971, 11.9924, 12.1990, 27.4875, 30.3807, 28.1987, 28.9676, 29.7508, 29.7271, 28.2197, 28.8735, 30.5133)
    CrucLeafMass <- c(31.8199, 34.6580, 32.0216, 33.1995, 34.1784, 34.0580, 32.1470, 32.8211, 34.8318, 34.5559, 34.0488, 34.7896, 30.9552, 32.5275, 33.5114, 14.4639, 13.9267, 14.8125, 13.6951, 14.7055, 13.5050, 13.9722, 32.6030, 35.3172, 32.7287, 35.0303, 36.4493, 33.1966, 32.0517, 31.2261, 34.3366)
     CrucAshMass <- c(28.2539, 31.1895, 29.0069, 29.8700, 30.5266, 30.6305, 28.8489, 29.4933, 31.3303, 30.3750, 30.0717, 31.7181, 27.7027, 29.5850, 30.1050, 13.4140, 12.5426, 13.4649, 12.8499, 13.3413, 12.2720, 12.5757, 28.5902, 31.4720, 29.1238, 32.1094, 33.6306, 30.6785, 29.9771, 28.9992, 31.2840)
     LeafDryMass <- CrucLeafMass - CrucMass
     AshMass <- CrucAshMass - CrucMass
     AFDM <- LeafDryMass - AshMass      
     LeafPropOM <- AFDM / LeafDryMass     
     
#### Create LOI data.frame and file
     
     LPPLittoralLOI <- data.frame(Pond, Site, Date, CrucNum, CrucMass, CrucLeafMass, CrucAshMass, LeafDryMass, AshMass, AFDM, LeafPropOM)
     
     write.table(LPPLittoralLOI, file = "./data/LPP_Littoral_LOI.csv", quote = F, row.names = F, sep = ",")
     