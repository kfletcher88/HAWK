# HAWK
Hitting associations with k-mers

## Installation

To install HAWK run (X.Y.Z is the version)

```
tar xf hawk-X.Y.Z-beta.tar
cd hawk-X.Y.Z-beta
make
```

## Prerequisites

JELLYFISH (modified version)
ABYSS 

## Counting k-mers

The first step in the pipeline is to count k-mers in each sample, find 
total number of k-mers per sample, discard k-mers that appear once and sort
the k-mers. The k-mer file contains one line per k-mer present and each 
line contains an integer representing the k-mer and its count separated 
by a space. The integer representation is given by using 0 for 'A', 
1 for 'C', 2 for 'G' and 3 for 'T'.

k-mer counting can be done using a modified version of the tool JELLYFISH
provided in the 'supplements' folder with HAWK. All of the steps mentioned 
above can be performed by installing this version of JELLYFISH and then 
running the script 'countKmers' in supplements with necessary modifications.
This will write the names of sorted k-mer count files in 'sorted_files.txt' 
and total k-mer count in samples in 'total_kmers.txt'.

## Running HAWK

Copy 'sorted_files.txt' and 'total_kmers.txt' corresponding to case samples 
into a folder and rename them 'case_sorted_files.txt' and 'case_total_kmers.txt'.
Similarly, copy 'sorted_files.txt' and 'total_kmers.txt' corresponding to control 
samples into the same folder and rename them 'control_sorted_files.txt' and 
'control_total_kmers.txt'.

Copy the scripts 'runHawk' and 'runAbyss' into the folder and run

```
./runHawk
./runAbyss
```

The k-mers with significant association to case and controls will be in 
'case_out_sig.fasta' and 'control_out_sig.fasta' and the assembled 
sequences will be in 'case_abyss.25_49.fasta' and 'control_abyss.25_49.fasta'
respectively.

## Analysis of sequences

Statistics about a <sequence> can be obtained by running

```
./kmerSummary <sequence>
```

This will output the following averaged over all constituent k-mers.
P-value
Total case count for k-mer
Total control count for k-mer
Number of case samples k-mer is present in
Number of control samples k-mer is present in 
  
'kmerstats.txt' will list the constituent k-mers and total counts in cases and 
controls, p-values and counts in individual samples. 


