# Analysis of the natal population structure by origin known 48 samples 

Based on the genotyping data of each individual, the [populations module](https://catchenlab.life.illinois.edu/stacks/comp/populations.php) in Stacks was run to compile them into a genepop format file according to the parameters for population structure analysis. The minimum allele frequency threshold was set at 0.05, the proportion of shared SNPs among individuals in a population (-r option) was set at 0.8 (80%), and the minimum number of populations with a locus (-p option) was set at two.


```
populations -P /path/to/stacks_files/ -M /path/to/origin_known_48samples_3regions_map.txt \
            -O /path/to/output/  --min_maf 0.05 -r 0.8 -p 2 --fstats --genepop --vcf
```            

The structure was analyzed and visualized using the genepop format file and the discriminant analysis principal component (DAPC) in adgenet 2.1.8 package for R version 4.2.2. accroding to the [tutorial](https://adegenet.r-forge.r-project.org/files/tutorial-dapc.pdf).

Then, a whiltelist was made to extract 1,767 SNPs from origin unknown samples for the subsequent group assignment.

`head -n 2 populations.snps.genepop | grep -v "#" | sed -e 's/,/\n/g' | sed -e 's/_/\t/g' > whitelist`


