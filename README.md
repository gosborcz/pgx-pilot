# preparing the vcf for pharmcat:

The files need to be prepared according to this scheme:

`java -jar GenomeAnalysisTK.jar -T HaplotypeCaller  \
     -R grc38.reference.fasta -I input.bam -o output.vcf \
     -L pharmcat_intervals.txt -glm BOTH --output_mode EMIT_ALL_SITES`
   
