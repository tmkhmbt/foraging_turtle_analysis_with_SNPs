## Extract SNPs for group assignments


Prior to the estimation of the natal origins of origin unknown samples, genotyping data of all samples were conducted.
To extract the same SNPs analyzed the natal population structure, the populations module of Stacks were run using whitelist option (-W).

The natal origin estimations  were independently performed on the samples with common Japanese haplotypes (n = 49), and on samples with widespread and orphan haplotypes (n = 43). whitelist was created in [the previous section](https://github.com/tmkhmbt/foraging_turtle_group_assignment/blob/main/Population%20structure.md).

1. SNPs extraction of 49 turtles with common Japanese haplotypes and Japanese (Ryukyus and Ogasawara) turtles.

```
populations -P /path/to/Stacks_files/ -M /path/to/commonJapanese_Ryukyus_Ogasawara_81samples_map.txt \
            -O /path/to/output/  -W /path/to/whitelist --genepop
```

2. SNPs extraction of 43 turtles with widespread or orphan haplotypes and all origin known turtles (southern, Ryukyus and Ogasawara) .

```
populations -P /path/to/Stacks_files/ -M /path/to/widespread_orhan_originknown_91samples_map.txt \
            -O /path/to/output/  -W /path/to/whitelist --genepop
```


Estimation of the natal origins were performed group assignment using find.clusters function in [adgenet](https://adegenet.r-forge.r-project.org/files/tutorial-dapc.pdf).
