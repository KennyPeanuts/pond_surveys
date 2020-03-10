# Code for the analysis of the DP organic matter sampling
## Metadata

* File Created: 2020-03-10 - KF
* Modified:
  

## Import Data

    cpom <- read.table("./data/DP_CPOM.csv", header = T, sep = ",")
    sed.om <- read.table("./data/DP_OM_profile.csv", header = T, sep = ",")

## Calculate Variables
### CPOM from Cores    
    cpom.dry.mass <- cpom$VialDryCPOM - cpom$VialMass
    cpom.ash.mass <- cpom$VialAM - cpom$VialMass    
    cpom.AFDM.core <- cpom.dry.mass - cpom.ash.mass
    
### Sediment OM from Cores
    sed.dry.mass <- sed.om$VialDryOM - sed.om$VialMass
    sed.ash.mass <- sed.om$VialAM - sed.om$VialMass
    sed.AFDM.core <- sed.dry.mass - sed.ash.mass

## Data Visualization
### CPOM from Cores
    plot(cpom.dry.mass ~ SedDepth, data = cpom)    
    plot(cpom.AFDM.core ~ SedDepth, data = cpom, subset = CPOM.Type == "NL", ylim = c(0, 1))
    points(cpom.AFDM.core ~ SedDepth, data = cpom, subset = CPOM.Type == "O", pch = 19)
        
### Sediment OM from Cores
    plot(sed.dry.mass ~ SedDepth, data = sed.om) 
    plot(sed.AFDM.core/sed.dry.mass ~ SedDepth, data = sed.om, subset = OM.Type == "NL", ylim = c(0, 1))
    points(sed.AFDM.core/sed.dry.mass ~ SedDepth, data = sed.om, subset = OM.Type == "O", pch = 19)
    points(sed.AFDM.core/sed.dry.mass ~ SedDepth, data = sed.om, subset = OM.Type == "L", pch = 2)
    
    