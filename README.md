# APOBEC mutagenesis in SARS-CoV-2

Hier we studied the impact of APOBEC proteins on SARS-CoV-2.

We used SARS-CoV-2 genome NC_045512.2 and available RNA-seq data from Covid-19 patients (GEO: GSE145926, GSE154244, GSE150316). We mapped reads to SARS-CoV-2 genome using bwa 0.7.17. We filtered human sequences with samtools-1.19.2. Then we used Variant Caller Pisces 5.3.0.0 to detect differences in the positions of reads and the reference genome. We excluded positions in which the mutation rate was equal to 100% (this means that these reads were obtained from a specific strain of coronavirus). So the command was:

```
Pisces -bam file.bam -g <path_to_the_genome> -o <path_for_output> -t 32 -gVCF false -MinVF 0.0000000001 -MinVariantQScore 0 -c 1 -MaxVQ 10000
```

An example of output file can be found in the folder /data

Then we wrote a python program for visualization .vcf received files (vcf_plots.ipynb). We calculated number of reads and allele frequency depending on the 5' and 3' nucleotides for all mutation types.