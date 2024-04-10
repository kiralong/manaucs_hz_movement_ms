# _Manacus_ hybrid zone movement manuscript

> Long _et al._ (2024) **Ongoing introgression of a secondary sexual plumage trait in a stable avian hybrid zone**. _bioRxiv_ <https://www.biorxiv.org/content/10.1101/2023.03.30.535000v2>

Repository describing the bioinformatic code used for the analysis of population structure and movement of the _Manacus_ hybrid zone in western Panama.

## Stacks pipeline

Analysis of RADseq data using the *Stacks* [(Rochette et al. 2019)](https://catchenlab.life.illinois.edu/stacks/) software.

Main Pipeline Steps:
1. `process_radtags.sh`: Process the raw RADseq reads to clean data, demultiplex, and remove adapters.
2. `bwa_alignment.sh`: Aligns reads to a reference genome with `bwa` and indexes with `samtools`.
3. `run_gstacks.sh`: Assemble and genotype aligned reads and remove pcr duplicates with *Stacks* `gstacks`.
4. `run_populations.sh`: Filter genotypes, calculate genome-wide statistics, export various file formats with *Stacks* `populations`

Other:
* `sumstats_to_whitelist.py`: Filter a SUMSTATS file from *Stacks* `populations` to generate a whitelist containing the catalog ID of a target set of SNPs.

For a more tutorialized version of this RADseq pipeline see the following repository: <https://github.com/kiralong/RADseq_pipeline>

## Population structure analysis

PCA, admixture, etc.

## Hybrid simulations

1. `make_diagnostic_snp_whitlist.py`: Generate a whitelist of a set of parental diagnostic SNPs filtered from a user-defined set of parameters. Takes a SUMSTATS and FSTATS output from *Stacks* `populations`.
2. `sim_hybrids_from_parents_vcf.py`: Take a VCF containing genotypes from two parental populations and simulate the genotypes across several hybrid crosses.

The original source for these RADseq-based hybrid simulations can be found in the following repository: <https://github.com/arcolon14/rad_hybrid_sims>.

## GGhybrid analysis

Stacks -> gghybrid format, hybrid index, etc.

## Hybrid classification

1. `format_vcf_to_introgress.py`: Format a VCF file generated by *Stacks* `populations` into the loci and genotypes tables used as input for  `introgress` [Gompert & Buerkle 2010](https://doi.org/10.1111/j.1755-0998.2009.02733.x).
2. `calc_intersp_het.R`: Calculate interspecies heterozygosity using the `introgress` R package.

## Geographic cline analysis (genetic data)

Stacks -> hzar format, hzar parallel script, hzar formatting and filtering

## Geographic cline analysis (phenotype data)

hzar phenotype scripts

## Data availability

Raw RAD-seq reads can be found on NCBI under BioProject [PRJNA893627](https://www.ncbi.nlm.nih.gov/bioproject/PRJNA893627).

## Notes

### 2024-04-04

ARC created a local copy of the hybrid simulation scripts from <https://github.com/arcolon14/rad_hybrid_sims>.

### 2024-03-22

Started migration of the code from other repositories, e.g., <https://github.com/kiralong/RADseq_pipeline>, into a single, manuscript-specific repo.

## Authors

Kira M. Long  
Angel G. Rivera-Colon

