# preparing the vcf for pharmcat:

The files need to be prepared according to this scheme:

`java -jar /net/software/local/gatk/3.7/GenomeAnalysisTK.jar -T HaplotypeCaller -R Homo_sapiens_assembly38.fa -I /net/archive/groups/plggneuromol/WES-pilot/wes_preliminary/SIJA_WES_output/cromwell-executions/target_seq/71127dc5-02f1-490d-86e4-8b4197797b55/call-variant_calling/variant_calling_module.variant_calling/755d9bd1-5e45-4c3e-afc4-6e5ab93a0237/call-bam_concat/execution/SIJA_realigned-haplotypecaller.bam -o SIJA_for_pharmcat.vcf -L pharmcat.intervals --output_mode EMIT_ALL_SITES`
     
  run with GATK 3.7
   
   
   i tried preparing vcf file according to pharmcat:
   
    Not a VCF file: no ##fileformat line
