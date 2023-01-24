# BWA mapping and bam file creation code

#reference genome used

```
REF=/path/to/GCF_015237465.2_rCheMyd1.pri.v2_genomic.fna

cd /path/to/all_quality_filtered_fastq_files/

while read line
do
bwa mem -t 8 -M $REF $line\_pair_R1.fastq $line\_pair_R2.fastq |\
samtools view -b -q 20  -f 0x0002  -F 0x0004  -F 0x0008  -T $REF - | \
samtools sort -T $NAME\.tmp - > /path/to/bams/$line\.bam
done < sample_list.txt

gstacks -I /path/to/bams/ -M /path/to/all_samples_map.txt --rm-pcr-duplicates -O /path/to/output/ -t 8

```
