This is the location for code used in Ancestral Risk Score (ARS) generation in Barrie et al. 2022 (in prep): "Genetic risk for Multiple Sclerosis originated in Pastoralist Steppe populations"

Authors: William Barrie (wb275@cam.ac.uk)
Licence: MIT


Usage example:

bash run_PRS_calculator_v4.sh imputed ordered_all_pop_ids_mapped output_files variants_for_v4.csv False False 

Where: 
imputed/ is a directory containing chromopainter local ancestry output file named in the form temp.$anc.$chr.master_all_copyprobsperlocus.txt.gz. NB chromopainter reverses column names for SNPs so care needed. This file is specific to a single ancestry/donor population. File should be SNP positions as columns, with first column "ID" containing individual IDs, one haplotype per row (i.e. two rows per diploid individual). E.g.:
ID,100,250,350
UKB1,9,9,0
UKB1,0,2,4
UKB2,0,0,8

ordered_all_pop_ids_mapped: this file contains an ordered list of all individuals in temp.$anc.$chr.master_all_copyprobsperlocus.txt.gz, and the population assignment. The third column is not used. E.g.:
UKBB1 UKBB 1
UKBB2 UKBB 1
UKBB3 UKBB 1

output_files/: this is a directory containing files named in the form $rsid.hom.0.samples and $rsid.hom.1.samples. Each of these is in turn a file containing individuals who are homozygous for 0 and homozygous for 1 respectively, one per row. 

variants_for_v4.csv: these are pruned variants used to calculate the PRS score. Columns are space separated: SNP CHR BP other_allele effect_allele effect_allele_frequency P OR

bootstrap option here is for bootstrapping individuals (n=1000)
reverse_cols option is whether to reverse the columns labels in temp.$anc.$chr.master_all_copyprobsperlocus.txt.gz. If they are ordered correctly, no need to reverse. 
