# Phylogenomic analysis of 14 *Xcc* isolates used in manuscript by Greer et al. (2025)

Here we document the methods used to generate the phylogenomic tree seen in Figure 2 of the manuscript submitted to *Plant Pathology* by Greer and colleagues.

## Genome assemblies included in the analysis
The set of genomes included in the analysis is specified in [01_genome_assemblies/genomes.txt](01_genome_assemblies/genomes.txt), plus an additional reference genome sequence specified in [02_ref/genomes.txt](02_ref/genomes.txt).

## Downloading the genome assemblies
To obtain the genome sequences, you first need to execute the command in [01_genome_assemblies/commands.sh](01_genome_assemblies/commands.sh). This will download each of the genome assemblies listed in file [01_genome_assemblies/assembly_accessions.txt](01_genome_assemblies/assembly_accessions.txt) and then it will rename the downloaded FASTA files, using the labels for each genome that are specified in [01_genome_assemblies/genomes.txt](01_genome_assemblies/genomes.txt). That renaming is acheived by [01_genome_assemblies/commands.sh](01_genome_assemblies/commands.sh) calling the script [01_genome_assemblies/rename_files.pl](01_genome_assemblies/rename_files.pl).

