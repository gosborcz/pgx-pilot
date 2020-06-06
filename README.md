# preparing the vcf for pharmcat:

`srun -p plgrid -N 1 -n 2 --time 02:00:00 --pty /bin/bash -l`

`module load plgrid/tools/gatk/4.1.3.0`

### Produce vcf with non-variants sites:
`gatk GenotypeGVCFs -R Homo_sapiens_assembly38.fa -V /net/archive/groups/plggneuromol/WES-pilot/wes_preliminary/SIJA_WES_output/cromwell-executions/target_seq/71127dc5-02f1-490d-86e4-8b4197797b55/call-variant_calling/variant_calling_module.variant_calling/755d9bd1-5e45-4c3e-afc4-6e5ab93a0237/call-gvcf_merge/execution/SIJA.g.vcf.gz -O SIJA_for_pharmcat.vcf -L pharmcat.intervals --include-non-variant-sites true`

note: *all run with GATK 4.1.3.0*

### Run pharmcat:
`java -jar <path_to_jar_file> -vcf <sample_file> -o <output_dir>`

-------------------------------------------------------------------------------------------------------------------------
the following steps were not performed and deletions were skipped in the preliminary analysis for now


#### Produce the vcf from pharmcat:

```
module load plgrid/tools/vcftools
module load plgrid/tools/bcftools

java -cp pharmcat-0.7.0-all.jar org.pharmgkb.pharmcat.definition.ExtractPositions -o pgx.vcf
    bgzip pgx.vcf && tabix -p vcf pgx.vcf.gz
    bcftools sort -o pgx_sorted.vcf.gz -O z pgx.vcf.gz && tabix -p vcf pgx_sorted.vcf.gz
```

#### optional script to deal with problematic sites:
```
cat sample.vcf | cut -f 1-10 | grep -v "|" | sed 's/\tInf\t/\t10000\t/' | sed 's/\tK,T/\tT/' | sed 's/\tG,K/\tG/' | sed 's/\tM,C/\tC/' | sed 's/\tG,S/\tG/' | sed 's/\tS,G/\tG/' | sed 's/\tC,S/\tC/' | sed 's/\tS,C/\tC/' | sed 's/\tC,M/\tM/' | sed 's/\tM\t/\tC\t/g' | sed 's/\tK,G/\tG/' | sed 's/INSGGGGCGAAAGGGGCGAAA,AGGGGCGAAA/\./' | grep -v "INSGGGGCGAAAGGGGCGAAA" | sed 's/\tT,K/\t./' | grep -v "rs72549353" | grep -v "\.T" | grep -v "\.AG" | grep -v "\.CT" > samplei.vcf
```

 
