# Quality filtering of raw reads obtained my MIG-seq

This is the first section to start the 

```
#quality filtering of raw reads and trimming of reads including adapter sequence
#fastq_file_list.txt include the sample name in each line

ADAPTER=/path/to/MIGadapter.fasta

cd /path/to/raw_read_files/

cat fastq_file_list.txt | while read line
do
  col1=`echo ${line} | cut -d '_' -f 1`
  col2=`echo ${line} | cut -d '_' -f 2`
java -Xmx8g -jar /path/to/Trimmomatic-0.35/trimmomatic-0.35.jar \
     PE \
     -threads 28 \
     -phred33 \
     ${col1}\_${col2}\_L001_R1_001.fastq.gz ${col1}\_${col2}\_L001_R2_001.fastq.gz ${col1}\_pair_R1.fastq ${col1}\_unpair_R1.fastq ${col1}\_pair_R2.fastq ${col1}\_unpair_R2.fastq \
     ILLUMINACLIP:$ADAPTER:2:30:10 \
     SLIDINGWINDOW:4:15 \
     CROP:77 \
     HEADCROP:6 \
     MINLEN:71
done
```
