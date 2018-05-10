


## Import Data

    dp_cpom <- read.table("./data/DP_CPOM.csv", header = T, sep = ",")

## Calculate Variables
    
    dp_dry_mass <- dp_cpom$VialDryCPOM - dp_cpom$VialMass
    dp_ash_mass <- dp_cpom$VialAM - dp_cpom$VialMass    
    dp_AFDM <- dp_dry_mass - dp_ash_mass
    

## Data Visualization
    
    plot(dp_AFDM , dp_cpom$SedDepth, ylim = c(7, 0), type = "p")
    boxplot(dp_AFDM[dp_cpom$CPOM.Type == "O"] * 1000, dp_AFDM[dp_cpom$CPOM.Type == "NL"] * 1000) 
    