# Natal origin structure examined by origin known 48 samples 

In this section [Stacks](https://catchenlab.life.illinois.edu/stacks/)


```
populations -P /path/to/bams/ -M /path/to/origin_known_48samples_3regions_map.txt \
            -O /path/to/output/  --min_maf 0.05 -r 0.8 -p 2 --fstats --genepop --vcf
            
            
#make whiltelist to extract 1,767 SNPs for group assignment
head -n 2 populations.snps.genepop | grep -v "#" | sed -e 's/,/\n/g' | sed -e 's/_/\t/g' > whitelist

```

