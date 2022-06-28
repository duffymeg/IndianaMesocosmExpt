# IndianaMesocosmExpt
Data and code for 2019 mesocosm expt in Indiana led by Laura Lopez

Citation: A healthy but depleted herd: predators decrease prey disease and density

Authors: Laura K. Lopez 1, Michael H. Cortez 2, Turner DeBlieux 3, Ilona A. Menel 4, Bruce O’Brien 1, Carla E. Cáceres 4, Spencer R. Hall 3, and Meghan A. Duffy 1*
        1 Department of Ecology & Evolutionary Biology, University of Michigan, Ann Arbor, MI 48109, USA
        2 Department of Biological Science, Florida State University, Tallahassee, FL 32306, USA
        3 Department of Biology, Indiana University, Bloomington, IN 47405 USA
        4 School of Integrative Biology, University of Illinois Urbana-Champaign, Urbana, IL 61801 

Contact: * Author responsible for writing code related to empirical analyses: duffymeg@umich.edu
         
Date: June 2022

Note: Analyses are all done in R, using Rmd and using the "here" package to keep things organized

_______________________________________________________________________________________________________________

DATA
evoldata2samplesizeswithzeroes.csv: this data file was initially created using the R code with a goal of summarizing the sample sizes for the 
genotyping work. MAD pulled it out of R to manually add predation and parasitism treatments, as well as 0 as the sample sizes for weeks that were 
missing data. Tank = the individual mesocosm, week = week of the experiment (in this file, all the weeks are off by one compared to the presentation
in the paper, so weeks 1, 5, and 8 are really weeks 2, 6, and 9; this was done to make the numbering system consistent across the different data sheets
and analyses, using the week numbering given in the manuscript (0 = Daphnia added, 1 = spores and predators added, 2 = first week of sampling for infection
prevalence, etc.) meanhosts is the number of hosts/prey genotyped in that tank on that week. pred = predation treatment (0, 0.1, 0.5, or 1) and para = parasitism
treatment (metsch or no metsch).

genotype.frequencies_MHC_converted.csv: this data file has the proportion of the 9 different genotype in each tank at the start of the experiment (when
there were equal abundances of the 9 genotypes in all tanks, based on our stocking of the tanks) and in the three weeks during which we sampled. As in the previous
data sheet, the weeks in this spreadsheet are all off by one compared to the week numbering system used in the manuscript; this change was made to avoid having
a week -1 in the figures/analyses. Columns G through 0 give the frequencies of the 9 genotypes, with each column corresponding to one genotype. For weeks other than
week -1/week 0, the abundances were determined by microsatellite analysis, with a sample size given in column F.

indianadatano22.csv: the main data sheet used to generate figure 1a-e. This has data from the scans of the samples collected each week ('time'). Weeks 1-8 in this sheet are weeks 2-9
in the manuscript. Columns G-N give the counts of infected adults (G), uninfected adults (H), infected juveniles (I), and uninfected juveniles (J). The next four
columns are the 'adjusted' versions of those; these are adjusted to take into account differences in sampling effort between week 1 in the data sheet (week 2
in the manuscript) and the following weeks. totaldensity sums the adjusted densities. lndensity is the natural log of the density, but where ln(0) was set to be 0.
Because that's not ideal, we created the "logone" column which is the LN of (totaldensity + 1). 

indychlorono22.csv: chlorophyll data for the experiment. This has data for each week ('time') and each tank. Dates in this file are in the dd/mm/yy format.
This file gives the chlorophyll a value (column F), the LN of that (column I) and the log10 chlorophyll (column J).

raweggdata_6_22_22.csv: This has the data for all of the individuals examined for egg ratio during the experiment; all of these animals are adult females.
This data has multiple rows for each time (week) x tank combination, with each row being a different animal. Size is the length of the animal, infection indicates
if she was infected (I) or not infected (NI), and eggs gives the number of embryoes in her brood chamber. "chaoborus_notes" transferred some notes that had
been on the data sheets that related to Choaborus encounted while sampling.

raweggsummary.csv: This was created in R from the raweggdata_6_22_22 file, but then exported as a kludge-y workaround for getting the treatment info added;
it then gets called in R.

traits2.csv: The estimates of predation susceptibility (alpha) and infection susceptibility (beta, which is the product of fS and p) for the 9 genotypes used 
in this experiment. Notably, the 'inf.susc' column is beta times 10^7. The values of alpha, fS, and p can be found in Table S2.

_______________________________________________________________________________________________________________

CODE: 
