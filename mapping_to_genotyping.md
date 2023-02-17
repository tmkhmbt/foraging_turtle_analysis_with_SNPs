# Mapping and genotyping

In this section, three softwares of [BWA](https://github.com/lh3/bwa), [Samtools](http://www.htslib.org/), and [Stacks](https://catchenlab.life.illinois.edu/stacks/) were used.

- Versions of the softwares:
  - BWA 0.7.13
  - Samtools 1.9
  - Stacks 2.3


```
REF=/path/to/GCF_015237465.2_rCheMyd1.pri.v2_genomic.fna

cd /path/to/all_quality_filtered_fastq_files/

while read line
do
bwa mem -t 8 -M $REF $line\_pair_R1.fastq $line\_pair_R2.fastq |\
samtools view -b -q 20  -f 0x0002  -F 0x0004  -F 0x0008  -T $REF - | \
samtools sort -T $NAME\.tmp - > /path/to/bams/$line\.bam
done < sample_list.txt
```

Then, run [gstacks](https://catchenlab.life.illinois.edu/stacks/comp/gstacks.php) module to genotype each individual at each identified SNP.

`gstacks -I /path/to/bams/ -M /path/to/all_samples_map.txt --rm-pcr-duplicates -O /path/to/output/ -t 8`

