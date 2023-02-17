## Extract SNPs for group assignments


Genotyping data of all samples were extracted for the subsequent natal origin estimation of origin unknown samples.
In this process, the *populations* module of Stacks were run using whitelist option (-W) to extract the same SNPs analyzed the natal population structure.
The whitelist was created in [the previous section](https://github.com/tmkhmbt/foraging_turtle_group_assignment/blob/main/Population%20structure.md).

The natal origin estimations were independently performed on the samples with common Japanese haplotypes (n = 49), and on samples with widespread and orphan haplotypes (n = 43), so the genepop files were created following two ways.


1. SNPs extraction of 49 turtles with common Japanese haplotypes and Japanese (Ryukyus and Ogasawara) turtles.

     The map format file of this analysis (commonJapanese_Ryukyus_Ogasawara_81samples_map.txt) is [here](https://github.com/tmkhmbt/foraging_turtle_group_assignment/blob/main/files/commonJapanese_Ryukyus_Ogasawara_81samples_map.txt).

```
populations -P /path/to/Stacks_files/ \
            -M /path/to/commonJapanese_Ryukyus_Ogasawara_81samples_map.txt \
            -O /path/to/output/ \
            -W /path/to/whitelist --genepop
```

2. SNPs extraction of 43 turtles with widespread or orphan haplotypes and all origin known turtles (southern, Ryukyus and Ogasawara) .
     The map format file of this analysis (widespread_orhan_originknown_91samples_map.txt) is [here](https://github.com/tmkhmbt/foraging_turtle_group_assignment/blob/main/files/widespread_orhan_originknown_91samples_map.txt).
```
populations -P /path/to/Stacks_files/ \
            -M /path/to/widespread_orhan_originknown_91samples_map.txt \
            -O /path/to/output/ \
            -W /path/to/whitelist --genepop
```

Then, the natal origins were estimated by the group assignments using *find.clusters* function in [adgenet](https://adegenet.r-forge.r-project.org/files/tutorial-dapc.pdf).
