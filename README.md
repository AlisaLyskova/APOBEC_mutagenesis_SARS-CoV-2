# APOBEC mutagenesis in SARS-CoV-2

Here we studied the impact of APOBEC proteins on SARS-CoV-2.

We used SARS-CoV-2 genome NC_045512.2 and available RNA-seq data from Covid-19 patients (GEO: GSE145926, GSE154244, GSE150316, GSE147507). We mapped reads to SARS-CoV-2 genome using bwa 0.7.17. We filtered human sequences with samtools-1.19.2. Then we used Variant Caller Pisces 5.3.0.0 to detect differences in the positions of reads and the reference genome. The command was:

```
Pisces -bam file.bam -g <path_to_the_genome> -o <path_for_output> -t 32 -gVCF false -MinVF 0.0000000001 -MinVariantQScore 0 -c 1 -MaxVQ 10000
```

Then we wrote a python program to visualize .vcf received files (SARS-CoV-2_genome_variants.ipynb). We calculated number of reads and allele frequency depending on the 5' and 3' nucleotides for all mutation types. We excluded positions in which the variant frequency was equal to 1 (this means that these reads were probably obtained from a specific strain of coronavirus). We excluded also positions with VF<0.001.

We also studied mutation C→T in the context of SARS-CoV-2 secondary structure. We wrote a program to visualize variant frequencies for positions with a C→T mutation and marked positions that located in loops (APOBEC_mutagenesis_SARS-CoV-2.ipynb).

Examples of output files can be found in the folder /data.