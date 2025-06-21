# Phylogenomic analysis of fourteen *Xcc* isolates used in manuscript by Greer et al. (2025)

Here we document the methods used to generate the phylogenomic tree seen in Figure 2 of the manuscript submitted to *Plant Pathology* by Greer and colleagues.

## Genome assemblies included in the analysis
The set of genomes included in the analysis is specified in [01_genome_assemblies/genomes.txt](01_genome_assemblies/genomes.txt), plus an additional reference genome sequence specified in [02_ref/genomes.txt](02_ref/genomes.txt).

## Download the genome assemblies
**Enter directory 01_genome_assemblies**. To obtain the genome sequences, you first need to execute the command in [01_genome_assemblies/commands.sh](01_genome_assemblies/commands.sh). This will download each of the genome assemblies listed in file [01_genome_assemblies/assembly_accessions.txt](01_genome_assemblies/assembly_accessions.txt) and then it will rename the downloaded FASTA files, using the labels for each genome that are specified in [01_genome_assemblies/genomes.txt](01_genome_assemblies/genomes.txt). That renaming is acheived by [01_genome_assemblies/commands.sh](01_genome_assemblies/commands.sh) calling the script [01_genome_assemblies/rename_files.pl](01_genome_assemblies/rename_files.pl).

## Download the reference genome assembly
**Enter directory 02_ref**. To download the reference genome sequence, specified in [02_ref/assembly_accessions.txt](02_ref/assembly_accessions.txt), execute the commands in [02_ref/commands.sh](02_ref/commands.sh). This renames the downloaded file according to the specification in [02_ref/genomes.txt](02_ref/genomes.txt).

## Set-up the PhaME working directory
**Enter directory 03_workdir**. Execute the command in [03_workdir/commands.sh](03_workdir/commands.sh). This will make symbolic links in directory 03_workdir to the relevant FASTA files in directory 01_genome_assemblies.

## Execute PhaME
**Enter directory 04_phame**. Here you will find the PhaME configuration file [04_phame/phame.fasttree.ctl](04_phame/phame.fasttree.ctl), which specifies the various options and settings for the PhaME pipeline. It is assumed that you already installed PhaME in a Conda environment called phame_env and that this environment has been activated (by executing ```conda activate phame_env```). The package versions in this Conda environment have been dumped into [04_phame/phame_env_packages.txt](04_phame/phame_env_packages.txt).
