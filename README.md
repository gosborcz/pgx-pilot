# preparing the vcf for pharmcat:

`srun -p plgrid -N 1 -n 2 --time 02:00:00 --pty /bin/bash -l`

`module load plgrid/tools/gatk/4.1.3.0`


## Produce vcf with emit all sites:

`gatk HaplotypeCaller -R Homo_sapiens_assembly38.fa -I /net/archive/groups/plggneuromol/WES-pilot/wes_preliminary/SIJA_WES_output/cromwell-executions/target_seq/71127dc5-02f1-490d-86e4-8b4197797b55/call-alignment/alignment_module.alignment/047ba924-74c7-4a12-a1a0-5e7f9dc0a519/call-bam_concat_recalib/execution/SIJA_recalibrated-markdup.bam -O SIJA_for_pharmcat.vcf -L pharmcat.intervals --output-mode EMIT_ALL_SITES true --force-active true --all-site-pls true`


other try:
`gatk GenotypeGVCFs -R Homo_sapiens_assembly38.fa -I SIJA.g.vcf -O SIJA_for_pharmcat.vcf -L pharmcat.intervals --include-non-variant-sites true`

     
note: *all run with GATK 4.1.3.0*
