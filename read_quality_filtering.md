# Quality filtering of raw reads

Low-quality reads were filtered from the samples using [Trimmomatic](https://github.com/usadellab/Trimmomatic). 
The fastq_file_list.txt contains the filename of the sample on each line. The filenames contain more than just the sample names, so that only the necessary parts can be output.

Files used in the script　below.
- [MIGadapter.fasta](https://github.com/tmkhmbt/foraging_turtle_group_assignment/blob/main/files/MIGadapter.fasta)
- [fastq_file_list.txt](https://github.com/tmkhmbt/foraging_turtle_group_assignment/blob/main/files/fastq_file_list.txt)

```
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
