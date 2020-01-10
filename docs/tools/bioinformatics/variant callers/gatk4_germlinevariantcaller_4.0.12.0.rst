:orphan:

GATK4 Germline Variant Caller
===========================================================

1 contributor · 2 versions

:ID: ``GATK4_GermlineVariantCaller``
:Python: ``janis_bioinformatics.tools.variantcallers.gatk.gatkgermline_variants_4_0_12 import GatkGermlineVariantCaller_4_0_12``
:Versions: 4.0.12.0, 4.1.3.0
:Authors: Michael Franklin
:Citations: 
:Created: 2019-02-01
:Updated: None
:Required inputs:
   - ``bam: BamPair``

   - ``reference: FastaWithDict``

   - ``snps_dbsnp: CompressedIndexedVCF``

   - ``snps_1000gp: CompressedIndexedVCF``

   - ``knownIndels: CompressedIndexedVCF``

   - ``millsIndels: CompressedIndexedVCF``
:Outputs: 
   - ``out: VCF``

Documentation
-------------

URL: *No URL to the documentation was provided*

This is a VariantCaller based on the GATK Best Practice pipelines. It uses the GATK4 toolkit, specifically 4.0.12.0.

        It has the following steps:

        1. BaseRecalibrator
        2. ApplyBQSR
        3. HaplotypeCaller
        4. SplitMultiAllele

Embedded Tools
***************

=============================================  ==================================
GATK4: Base Recalibrator                       ``Gatk4BaseRecalibrator/4.0.12.0``
GATK4: Apply base quality score recalibration  ``Gatk4ApplyBQSR/4.0.12.0``
GATK4: Haplotype Caller                        ``Gatk4HaplotypeCaller/4.0.12.0``
Split Multiple Alleles                         ``SplitMultiAllele/v0.5772``
=============================================  ==================================

------

Additional configuration (inputs)
---------------------------------

===========  ====================  ===================================================================================================================================================
name         type                  documentation
===========  ====================  ===================================================================================================================================================
bam          BamPair
reference    FastaWithDict
snps_dbsnp   CompressedIndexedVCF
snps_1000gp  CompressedIndexedVCF
knownIndels  CompressedIndexedVCF
millsIndels  CompressedIndexedVCF
intervals    Optional<bed>         This optional interval supports processing by regions. If this input resolves to null, then GATK will process the whole genome per each tool's spec
===========  ====================  ===================================================================================================================================================

.
