# Phylogenomic analysis of fourteen *Xcc* isolates used in manuscript by Greer et al. (2025)

Here we document the methods used to generate the phylogenomic tree seen in Figure 2 of the manuscript submitted to *Plant Pathology* by Greer and colleagues. It uses the PhaME pipeline that is describe in this paper:
- Shakya M, Ahmed SA, Davenport KW, Flynn MC, Lo CC, Chain PSG. Standardized phylogenetic and molecular evolutionary analysis applied to species across the microbial tree of life. Sci Rep. 2020 Feb 3;10(1):1723. 

PhaME can use several different tree-building engines. Here we use FastTree 2:
- Price MN, Dehal PS, Arkin AP. FastTree 2 – Approximately Maximum-Likelihood Trees for Large Alignments. Poon AFY, editor. PLoS ONE. 2010 Mar 10;5(3):e9490. 

## Genome assemblies included in the analysis
The set of genomes included in the analysis is specified in [01_genome_assemblies/genomes.txt](01_genome_assemblies/genomes.txt), plus an additional reference genome sequence specified in [02_ref/genomes.txt](02_ref/genomes.txt). This includes genome sequences described by the following publications:
- Alkhateeb RS, Vorhölter F jörg, Rückert C, Mentz A, Wibberg D, Hublik G, et al. Genome wide transcription start sites analysis of the Xanthomonas campestris pv. campestris B100 with insights into the gum gene cluster directing the biosynthesis of the exopolysaccharide xanthan. J Biotechnol. 2016 Mar;1–36. 
- Bellenot C, Carrère S, Gris C, Noël LD, Arlat M. Genome Sequences of 17 Strains from Eight Races of Xanthomonas campestris pv. campestris. Baltrus DA, editor. Microbiol Resour Announc. 2022 Jun 13;2(7):e0027922. 
- Bolot S, Roux B, Carrere S, Jiang BL, Tang JL, Arlat M, et al. Genome Sequences of Three Atypical Xanthomonas campestris pv. campestris Strains, CN14, CN15, and CN16. Genome Announc. 2013 Jul 11;1(4):e00465-13. 
- Bolot S, Cerutti A, Carrère S, Arlat M, Fischer-Le Saux M, Portier P, et al. Genome Sequences of the Race 1 and Race 4 Xanthomonas campestris pv. campestris Strains CFBP 1869 and CFBP 5817. Genome Announc. 2015 Oct 29;3(5):e01023-15. 
- da Silva ACR, Ferro JA, Reinach FC, Farah CS, Furlan LR, Quaggio RB, et al. Comparison of the genomes of two Xanthomonas pathogens with differing host specificities. Nature. 2002 May 23;417(6887):459–63. 
- Guy E, Genissel A, Hajri A, Chabannes M, David P, Carrere S, et al. Natural genetic variation of Xanthomonas campestris pv. campestris pathogenicity on arabidopsis revealed by association and reverse genetics. Guttman D, Ausubel FM, editors. mBio. 2013 Jan 4;4(3):e00538-12. 
- Qian W. Comparative and functional genomic analyses of the pathogenicity of phytopathogen Xanthomonas campestris pv. campestris. Genome Res. 2005 May 17;15(6):757–67. 

## Download the genome assemblies
**Enter directory 01_genome_assemblies**. To obtain the genome sequences, you first need to execute the command in [01_genome_assemblies/commands.sh](01_genome_assemblies/commands.sh). This will download each of the genome assemblies listed in file [01_genome_assemblies/assembly_accessions.txt](01_genome_assemblies/assembly_accessions.txt) and then it will rename the downloaded FASTA files, using the labels for each genome that are specified in [01_genome_assemblies/genomes.txt](01_genome_assemblies/genomes.txt). That renaming is acheived by [01_genome_assemblies/commands.sh](01_genome_assemblies/commands.sh) calling the script [01_genome_assemblies/rename_files.pl](01_genome_assemblies/rename_files.pl).

## Download the reference genome assembly
**Enter directory 02_ref**. To download the reference genome sequence, specified in [02_ref/assembly_accessions.txt](02_ref/assembly_accessions.txt), execute the commands in [02_ref/commands.sh](02_ref/commands.sh). This renames the downloaded file according to the specification in [02_ref/genomes.txt](02_ref/genomes.txt). Here we use strain NCPPB 1946, which is the pathotype strain for *Xanthomonas campestris* pv. *raphani*.

## Set-up the PhaME working directory
**Enter directory 03_workdir**. Execute the command in [03_workdir/commands.sh](03_workdir/commands.sh). This will make symbolic links in directory 03_workdir to the relevant FASTA files in directory 01_genome_assemblies.

## Execute PhaME
**Enter directory 04_phame**. Here you will find the PhaME configuration file [04_phame/phame.fasttree.ctl](04_phame/phame.fasttree.ctl), which specifies the various options and settings for the PhaME pipeline. It is assumed that you already installed PhaME in a Conda environment called phame_env and that this environment has been activated (by executing ```conda activate phame_env```). The package versions in this Conda environment have been dumped into [04_phame/phame_env_packages.txt](04_phame/phame_env_packages.txt). Running [04_phame/commands.sh](04_phame/commands.sh) will execute the command ```phame ./phame.fasttree.ctl```, which launches the PhAME pipeline, using FastTree 2 as the tree-building engine.

## Execute PhaME results
The results of the PhaME pipeline can be found in [03_workdir/results](03_workdir/results). This includes log files [03_workdir/results/xcc_fastree.error](03_workdir/results/xcc_fastree.error) and [03_workdir/results/xcc_fastree.log](03_workdir/results/xcc_fastree.log). Most importantly, it includes the final Newick tree file [03_workdir/results/trees/xcc_fastree_all.fasttree](03_workdir/results/trees/xcc_fastree_all.fasttree).
