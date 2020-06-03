# preparing the vcf for pharmcat:

The files need to be prepared according to this scheme:

`java -jar /net/software/local/gatk/3.7/GenomeAnalysisTK.jar -T HaplotypeCaller -R Homo_sapiens_assembly38.fa -I /net/archive/groups/plggneuromol/WES-pilot/wes_preliminary/SIJA_WES_output/cromwell-executions/target_seq/71127dc5-02f1-490d-86e4-8b4197797b55/call-alignment/alignment_module.alignment/047ba924-74c7-4a12-a1a0-5e7f9dc0a519/call-bam_concat_recalib/execution/SIJA_recalibrated-markdup.bam -O SIJA_for_pharmcat.vcf -L pharmcat.intervals --output-mode EMIT_ALL_SITES`
     
  run with GATK 4.1.3.0
