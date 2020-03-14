# Metadata for data used to determine the LOI of the CPOM for Campus Pond

## File

`CP_Sed_LOI.csv`

## Metadata

* Collected by: KF and JH

* Collected on: 2016-07-11

* Affiliation: Longwood University

* Location: Campus Pond

### Description

The data used to determine the LOI for the sediment collected from Campus Pond. The detailed sampling notes can be found in [https://github.com/KennyPeanuts/pond_surveys/blob/master/lab_notebook/lab_notes/Campus_Pond_Sampling_11July2016.md](https://github.com/KennyPeanuts/pond_surveys/blob/master/lab_notebook/lab_notes/Campus_Pond_Sampling_11July2016.md)

Briefly:

Cores (4.7 cm diam.) were collected from the center of the pond with a KP corer at three sites. The cores were extruded upwards in 1 cm (0 - 4 cm) increments or 2 cm (4 -8 cm) increments and then sliced into a 1 mm sieve. Any material that was retained by the sieve was considered CPOM and was transferred to a 20 ml glass scintillation vial and then dried at 50 dC. The sediment that passed through the sieve was collected in another 20 ml glass scintillation vial and dried at 50 dC. 

Following the determination of dry mass, the sediments and CPOM were ashed for 5 h at 550 dC and AFDM was determined as the difference between the mass of the dry sample and the mass of the ash.

NOTE: Only the open sediment data are recorded in this file. The CPOM data are found in [https://github.com/KennyPeanuts/pond_surveys/blob/master/lab_notebook/data/CP_CPOM_LOI.csv](https://github.com/KennyPeanuts/pond_surveys/blob/master/lab_notebook/data/CP_CPOM_LOI.csv)

## Issue with the raw data
### Description of the issue with Vial "E2"

In the field notebook the 1-2 cm sediment sample from Open Core B is indicated to go into vial "E2" and Vial "E1" is missing.  However in the lab notebook, Vial "E1" has data and it is in order in the data set.

#### Investigation of the data

When looking at the data, the data from Vial "E1" seems to be in the correct place. Since the 4-6 cm and 6-8 cm samples were 2 cm deep, we would expect to see approximately 2X the mass of sediment in the sample.  If we count down from the first sample in Vial "D4", 4-6 cm and 6-8 cm samples for core A should be in vials "D8" and "D9".  The data shows that these 2 samples have 0.4702 g and 0.4543 g of dry sediment, which is greater than the prior 4 samples.

If we do the same for core B assuming that the 0-1 sample was collected in vial "E1", then the 4-6 cm and 6-8 cm samples should be in vials "E4" and "E5".  Vials "E3", "E4", and "E5" all show elevated sediment mass but vial "E6" drops back down to 0.1821 g, which suggests that this is the 0-1 cm sample from Core C.  Counting down the Core C samples with this assumption shows an increase in sed mass at vial "E10", which would correspond to the 4-6 cm sample.  Vials "E10", "F1", and "F2" all show sediment masses consistent with a 2 cm sample.

So, the "extra" samples seem to be either at the end of core B or at the end of core C.  There is no way to determine where the error came from or which is the "extra" sample. 

#### Action Taken

Since there is no way to distinguish between presumed extra samples, I have removed the sample from vial "F2" from the data.  This would be consistent with an error in recording the data in the field notebook.  The implications for the estimates of sediment mass seem small because this sample is similar in magnitude to the other deep samples.

## Variables

* Pond = the abbreviation for the pond name
  * CP = Campus Pond
  
* Date = the date the field sampling was completed (YYYY-MM-DD)

* SampleType = the type of site the core was taken from
  * O = Open water
  
* Core = the letter that was assigned to the core sample 

* Z = how much was sampled from the core (cm)

* SedDepth = the starting depth of the core that was sampled (cm) 

* VialNum = the number vial that was used for the sample

* VialMass = the weight of the vial (g)

* VialDrySed = the weight of the vial and sediment dry mass (g)

* VialAM = the weight of the vial and ash mass (g)

* CoreDiam = the diameter of the core (cm)

* SedDryMass = the mass of the dry sediment from the core (g)

* SedAshMass = the mass of the ash after 5 h at 550 dC (g)

* SedAFDM = the AFDM of the sediment from the core (g)

* CoreArea = the area of the core (cm2)

* SedAFDMStandingStock = the standing stock of the CPOM (g AFDM / m2)

## Data Entry
### Entered Variables 
    
    Pond <- rep("CP", 18)
    Date <- rep("2016-07-11", 18)
    SampType <- rep("O", 18)
    Core <- c(rep("A", 6), rep("B", 6), rep("C", 6))
    Z <- rep(c(1, 1, 1, 1, 2, 2), 3)
    SedDepth <- rep(c(0, 1, 2, 3, 4, 6), 3) 
    VialNum <- c("D4", "D5", "D6", "D7", "D8", "D9", "D10", "E1", "E2", "E3", "E4", "E5", "E6", "E7", "E8", "E9", "E10", "F1")
    VialMass <- c(13.3134, 13.3345, 13.3024, 13.4151, 13.0908, 13.3320, 13.3844, 13.2417, 13.3396, 13.4060, 13.2192, 13.2214, 13.1694, 13.4460, 13.3465, 13.1670, 13.2412, 13.1938)
    VialDrySed <- c(13.5036, 13.5544, 13.4939, 13.7326, 13.5610, 13.7863, 13.5639, 13.4315, 13.5236, 13.8082, 13.5577, 13.8219, 13.3515, 13.5851, 13.6037, 13.4203, 13.7380, 13.7846)
    VialAM <- c(13.4803, 13.5270, 13.4730, 13.7006, 13.5168, 13.7275, 13.5387, 13.4054, 13.5037, 13.7704, 13.5287, 13.7527, 13.3295, 13.5663, 13.5731, 13.3906, 13.6933, 13.7343)
    CoreDiam <- 4.7
   
### Calculated Variables 

    SedDryMass <- VialDrySed - VialMass
    SedAshMass <- VialAM - VialMass
    SedAFDM <- SedDryMass - SedAshMass
    CoreArea <- pi * ((CoreDiam * 0.5)^2) 
    SedAFDMStandingStock <- (SedAFDM / CoreArea) * 10000 # multiplication by 10000 coverts from cm-2 to m-2
    propOM <- SedAFDM / SedDryMass
    
### Create Data Frame
    
    litter <- data.frame(Pond, Date, SampType, Core, Z, SedDepth, VialNum, VialMass, VialDrySed, VialAM, SedDryMass, SedAshMass, SedAFDM, SedAFDMStandingStock, propOM, CoreDiam, CoreArea)
    
    
## Make Data File
    
    write.table(litter, "./data/CP_Sed_LOI.csv", quote = F, row.names = F, sep = ",")
    