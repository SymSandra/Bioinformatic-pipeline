# _Macrosteles_ project
In this repository, we introduce our approaches to describe the genetic and microbial variation of _Macrosteles_ leafhoppers across various populations. 
The repository is divided into two distinctive sections:
## 1. [Laboratory procedures](https://github.com/SymSandra/Macrosteles-project-Bioinformatic-pipeline/blob/main/Laboratory%20procedures)
Where we describe protocols used for:
### [Homogenization](https://github.com/SymSandra/Macrosteles-project-Bioinformatic-pipeline/blob/main/Homogenization)
### [DNA extraction](https://github.com/SymSandra/Macrosteles-project-Bioinformatic-pipeline/blob/main/DNA%20extraction)
### [PCR and library preparation](https://github.com/SymSandra/Macrosteles-project-Bioinformatic-pipeline/blob/main/PCR%20and%20library%20preparation)
## 2. Bioinformatics
Where we provide detailed information about custom bioinformatic approaches for amplicon data analysis.
### [Amplicon processing](https://github.com/SymSandra/Macrosteles-project-Bioinformatic-pipeline/blob/main/Amplicon%20processing) (used for both COI and 16S data):
- Analyses each library (sample) separately,
- Merges R1 and R2 reads, passes only high-quality reads,
- Converts fastq to fasta files,
- Dereplicates and denoises samples,
- Assigns taxonomy affiliation to reads,
- Produces zOTU/OTU tables used by other scripts.

This is the core amplicon analysis workflow. 
This script joins F and R (R1 and R2) reads, passing only high-quality ones. 
Next it converts fastq to fasta file, dereplicate and denoise sequences in each library seperately.
Joins all the libraries into one table and assigns all the sequences to taxonomy.
**This is a first step of analysis of bacterial 16S and COI data!**


### [Picking Insect Barcode](https://github.com/SymSandra/Macrosteles-project-Bioinformatic-pipeline/blob/main/Picking%20Insect%20Barcode):
- Uses COI zotu table (produced by Amplicon processing) as an input,
- creates:
  - table with info about most abundand COI barcode, taxonomy and bacteria presence,
  - fasta file, containing most abundand Eucaryotic COI barcode per each library/sample,
  - table containing information about Eucaryotic COI sequences that represents at least 5% of total Eucaryotic reads per sample,
  - table containing information about bacterial COI sequences.  

### [Decontamination](https://github.com/SymSandra/Macrosteles-project-Bioinformatic-pipeline/blob/main/Decontamination):
- Uses as an input:
  - 16S zotu table (produced by Amplicon processing),
  - otus.tax (produced by Amplicon processing),
  - list of blanks,
- Decontaminates 16S data based on negative controls,
- Creates:
  - Table with zotus assigned as: symbiont or contaminants,
  - Decontaminated zotu and otu tables,
  - Statistics table.
