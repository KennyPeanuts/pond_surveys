# Metadata for data used to determine the LOI of the CPOM for Campus Pond

## File

`CP_CPOM_LOI.csv`

## Metadata

* Collected by: KF and JH

* Collected on: 2016-07-11

* Affiliation: Longwood University

* Location: Campus Pond

### Description

The data used to determine the LOI for the CPOM collected from Campus Pond. The detailed sampling notes can be found in [https://github.com/KennyPeanuts/pond_surveys/blob/master/lab_notebook/lab_notes/Campus_Pond_Sampling_11July2016.md](https://github.com/KennyPeanuts/pond_surveys/blob/master/lab_notebook/lab_notes/Campus_Pond_Sampling_11July2016.md)

Briefly:

Cores (4.7 cm diam.) were collected from the center of the pond with a KP corer at three sites. The cores were extruded upwards in 1 cm (0 - 4 cm) increments or 2 cm (4 -8 cm) increments and then sliced into a 1 mm sieve. Any material that was retained by the sieve was considered CPOM and was transferred to a 20 ml glass scintillation vial and then dried at 50 dC. The sediment that passed through the sieve was collected in another 20 ml glass scintillation vial and dried at 50 dC. 

Following the determination of dry mass, the sediments and CPOM were ashed for 5 h at 550 dC and AFDM was determined as the difference between the mass of the dry sample and the mass of the ash.

NOTE: Only the open CPOM data are recorded in this file. The sediment data are found in [

## Issue with the raw data
### Description of the issue with Vial "I6"
  
In the field notebook the notes indicated that there was no CPOM sample taken from the 0-1 cm depth of Open Core A. The first CPOM sample was taken at 1-2 cm and this was placed in Vial "I1".  The field notebook also indicated that no sample was placed into Vial "I6" and that the first CPOM sample from Open Core B (0-1 cm) was placed into Vial "I7". 

In the lab notebook the is a sample recorded for Vial "I6" and it is recorded in the order of the vials (i.e., ...I5, I6, I7...), so that it is not clear what the correct order of the samples should be.

#### Investigation of the data

The dry mass of sample in Vial "I6" was 0.0009 g, which is an order of magnitude lower than the next lowest sample ("I7" = 0.0021 g). Furthermore, the ash mass of the sample in "I6" was greater than the dry mass of the sample, resulting in an AFDM of -0.0007 g. Finally, the pattern of the data indicates that the mass of sample "I7" would be appropriate for the 0-1 cm sample in core 2. 

#### Action taken for the issue with I6

Given the irregularities in the mass values in Vial "I6" and the fact that Vial "I6" was not supposed to exist, I have removed the Vial "I6" sample from the data set.

### Description of the issue with Vial "H4"

The Vial mass for Vial "H4" was recorded as 12.3945 g.  This is 1 g lower than any other vial and results in an unreasonable value for the CPOM masses in the sample.

#### Action taken for the issue

I entered the Vial mass for "H4" as 13.3945 g, which is consistent with the other vials.

## Variables

* Pond = the abbreviation for the pond name
  * CP = Campus Pond
  
* Date = the date the field sampling was completed (YYYY-MM-DD)

* CPOMType = the type of site the core was taken from
  * O = Open water
  
* CPOMCore = the letter that was assigned to the core sample 

* Z = how much was sampled from the core (cm)

* SedDepth = the starting depth of the core that was sampled (cm) 

* VialNum = the number vial that was used for the sample

* VialMass = the weight of the vial (g)

* VialDryCPOM = the weight of the vial and CPOM dry mass (g)

* VialAM = the weight of the vial and ash mass (g)

* CoreDiam = the diameter of the core (cm)

* CPOMDryMass = the mass of the dry CPOM from the core (g)

* CPOMAshMass = the mass of the ash after 5 h at 550 dC (g)

* CPOMAFDM = the AFDM of the CPOM from the core (g)

* CoreArea = the area of the core (cm2)

* CPOMAFDMStandingStock = the standing stock of the CPOM (g AFDM / m2)

## Data Entry
### Entered Variables 
    
    Pond <- rep("CP", 18)
    Date <- rep("2016-07-11", 18)
    CPOMType <- rep("O", 18)
    CPOMCore <- c(rep("A", 6), rep("B", 6), rep("C", 6))
    Z <- rep(c(1, 1, 1, 1, 2, 2), 3)
    SedDepth <- rep(c(0, 1, 2, 3, 4, 6), 3) 
    VialNum <- c(NA, "I1", "I2", "I3", "I4", "I5", "I7", "I8", "I9", "I10", "H1", "H2", "H3", "H4", "H5", "H6", "H7", "H8")
    VialMass <- c(NA, 13.2450, 13.3085, 13.0982, 13.1722, 13.3487, 13.1921, 13.3382, 13.2517, 13.3030, 13.4048, 13.3808, 13.1076, 13.3945, 13.1713, 13.2380, 13.4421, 13.2276)
    VialDryCPOM <- c(NA, 13.3181, 13.3776, 13.2608, 13.4532, 13.6597, 13.1942, 13.5257, 13.4134, 13.5109, 13.6437, 13.5499, 13.1106, 13.3969, 13.1770, 13.2989, 13.6063, 13.9549)
    VialAM <- c(NA, 13.2812, 13.3242, 13.1689, 13.2347, 13.4289, 13.1932, 13.3799, 13.2947, 13.3746, 13.4547, 13.4101, 13.1096, 13.3956, 13.1693, 13.2545, 13.4754, 13.3541)
    CoreDiam <- 4.7
   
### Calculated Variables 

    CPOMDryMass <- VialDryCPOM - VialMass
    CPOMAshMass <- VialAM - VialMass
    CPOMAFDM <- CPOMDryMass - CPOMAshMass
    CoreArea <- pi * ((CoreDiam * 0.5)^2) 
    CPOMAFDMStandingStock <- (CPOMAFDM / CoreArea) * 10000 # multiplication by 10000 coverts from cm-2 to m-2
    
### Create Data Frame
    
    litter <- data.frame(Pond, Date, CPOMType, CPOMCore, Z, SedDepth, VialNum, VialMass, VialDryCPOM, VialAM, CPOMDryMass, CPOMAshMass, CPOMAFDM, CPOMAFDMStandingStock, CoreDiam, CoreArea)
    
## Make Data File
    
    write.table(litter, "./data/CP_CPOM_LOI.csv", quote = F, row.names = F, sep = ",")
    