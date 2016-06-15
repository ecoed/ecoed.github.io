# Genome annotation using Prokka

## Background

In this section we will use a software tool called Prokka to annotate the draft genome sequence produced in the previous [tutorial](../spades/index.md). Prokka is a “wrapper”; it collects together several pieces of software (from various authors), and so avoids “re-inventing the wheel”.

Prokka finds and annotates features (both protein coding regions and RNA genes, i.e. tRNA, rRNA) present on on a sequence. Note, Prokka uses a two-step process for the annotation of protein coding regions: first, protein coding regions on the genome are identified using [Prodigal](http://prodigal.ornl.gov/); second, the *function* of the encoded protein is predicted by similarity to proteins in one of many protein or protein domain databases. Prokka is a software tool that can be used to annotate bacterial, archaeal and viral genomes quickly, generating standard output files in GenBank, EMBL and gff formats. More information about Prokka can be found [here](https://github.com/tseemann/prokka).

## Learning objectives

At the end of this tutorial you should be able to:

1. input files into Prokka,
2. run Prokka, and
3. examine the annotated genome using JBrowse.

## Input data

- You will need the assembled contigs from the previous workshop ([Assembly with Spades](../spades/index.md)): <fn>SPAdes_contigs.fasta</fn>
- If you are continuing on from that tutorial, this file will be in your current history and there is no need to find/import it.

## Run Prokka

- In Galaxy, go to <ss>Tools &rarr; NGS Analysis &rarr; NGS: Annotation &rarr; Prokka</ss>  
- Set the following parameters (leave everything else unchanged):
    - <ss>Contigs to annotate</ss>: <fn>SPAdes contigs (fasta)</fn>  
    - <ss>Locus tag prefix (--locustag)</ss>: P
    - <ss>Force GenBank/ENA/DDJB compliance (--compliant)</ss>: *No*
    - <ss>Sequencing Centre ID (--centre)</ss>: V
    - <ss>Genus Name</ss>: *Staphylococcus*  
    - <ss>Species Name</ss>: *aureus*  
    - <ss>Use genus-specific BLAST database</ss> *No*  

Your tool interface should look like this:

![prokka interface](images/interface.png)

- Click <ss>Execute</ss>  

## Examine the output

First, enable "Scratchbook" in Galaxy - this allows you to view several windows simultaneously. Click on the squares:

![scratchbook icon](images/scratchbook.png)


Once Prokka has finished, examine each of its output files.

- The GFF and GBK files contain all of the information about the features annotated (in different formats.)
- The txt file contains a summary of the number of features annotated.
- The faa file contains the protein sequences of the genes annotated.
- The ffn file contains the nucleotide sequences of the genes annotated.

## View annotated features in JBrowse
Now that we have annotated the draft genome sequence, we would like to view the sequence in the JBrowse genome viewer.

- Go to <ss>Statistics and Visualisation &rarr; Graph/Display Data &rarr; JBrowse</ss>

- Under <ss>Fasta Sequence(s)</ss> choose <fn>Prokka on data XX:fna</fn>. This sequence will be the reference against which annotations are displayed.

- For <ss>Produce a Standalone Instance</ss> select *Yes*.

- For <ss>Genetic Code</ss> choose *11: The Bacterial, Archaeal and Plant Plastid Code*.

- Click <ss>Insert Track Group</ss>

- Click <ss>Insert Annotation Track</ss>

- For <ss>Track Type</ss> choose *GFF/GFF3/BED/GBK Features*

- For <ss>GFF/GFF3/BED Track Data</ss> select <fn>Prokka on data XX:gff</fn>  [Note: not wildtype.gff]

Your tool interface should look like this:

![JBrowse interface](images/jbrowse.png)

- Click <ss>Execute</ss>

- A new file will be created, called <fn>JBrowse on data XX and data XX - Complete</fn>. Click on the eye icon next to the file name. The JBrowse window will appear in the centre Galaxy panel.

- Under <ss>Available Tracks</ss> on the left, tick the box for <fn>Prokka on data XX:gff</fn>.

- Select contig 6 in the drop down box. You can only see one contig displayed at a time.

![JBrowse](images/jbrowse2.png)

- Use the plus and minus buttons to zoom in and out, and the arrows to move left or right (or click and drag within the window to move left or right).

Zoomed out view:

![JBrowse](images/jbrowse3.png)

Zoom in to see the reference sequence at the top. JBrowse displays the sequence and a 6-frame amino acid translation.

Zoomed in view:

![JBrowse](images/jbrowse4.png)

- Click on a gene/feature annotation (the bars on the annotation track) to see more information.
    - gene name
    - product name
    - you can download the FASTA sequence by clicking on the disk icon.

## What next?

- Identify genome variants (nucletotide changes) using [Snippy](../snippy/index.md).