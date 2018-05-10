# Metadata for the AFDM for Littoral LPP

## File

`LPP_Litt_AFDM.csv`

## Metadata

* Collected by: KF and JH

* Collected on: 13 July 2016

* Affiliation: Longwood University

* Location: Lancer Park Pond

### Description

These data are on the mass of leaf litter collected from the littoral zone of the pond. Briefly, a Hess sampler was placed adjacent to shore and all of the leaf litter was removed down to the sediment surface.  

The litter was then dried in a paper bag and once dry distributed into ceramic crucibles to determine LOI to get AFDM

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

* CrucNum = the number crucible that was used for the sample

* CrucMass = the weight of the crucible (g)

* CrucLeafDM = the weight of the crucible and CPOM dry mass (g)

* CrucAM = the weight of the crucible and ash mass (g)

## Data Entry

    Pond <- 
    Date <- 
    Site <- c(rep("A", 26), rep("B", 26))
    CrucNum <- c(4, 5, 7, 8, 10, 13, 14, 16, 17, 18, 26, 21, 22, 23, 24, 1, 2, 3, 4, 5, 6, 7, 10, 13, 14, 16, 4, 5, 7, 8, 10, 13, 14, 16, 17, 18, 20, 21, 22, 23, 24, 1, 2, 3, 4, 5, 6, 7, 4, 5, 7, 17)
