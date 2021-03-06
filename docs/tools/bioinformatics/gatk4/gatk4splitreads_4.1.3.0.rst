:orphan:

GATK4: SplitReads
===================================

*0 contributors · 3 versions*

No documentation was provided: `contribute one <https://github.com/PMCC-BioinformaticsCore/janis-bioinformatics>`_


Quickstart
-----------

    .. code-block:: python

       from janis_bioinformatics.tools.gatk4.splitreads.versions import Gatk4SplitReads_4_1_3

       wf = WorkflowBuilder("myworkflow")

       wf.step(
           "gatk4splitreads_step",
           Gatk4SplitReads_4_1_3(
               outputFilename=None,
               bam=None,
           )
       )
       wf.output("out", source=gatk4splitreads_step.out)
    

*OR*

1. `Install Janis </tutorials/tutorial0.html>`_

2. Ensure Janis is configured to work with Docker or Singularity.

3. Ensure all reference files are available:

.. note:: 

   More information about these inputs are available `below <#additional-configuration-inputs>`_.



4. Generate user input files for Gatk4SplitReads:

.. code-block:: bash

   # user inputs
   janis inputs Gatk4SplitReads > inputs.yaml



**inputs.yaml**

.. code-block:: yaml

       bam: bam.bam




5. Run Gatk4SplitReads with:

.. code-block:: bash

   janis run [...run options] \
       --inputs inputs.yaml \
       Gatk4SplitReads





Information
------------


:ID: ``Gatk4SplitReads``
:URL: *No URL to the documentation was provided*
:Versions: 4.1.4.0, 4.1.3.0, 4.1.2.0
:Container: broadinstitute/gatk:4.1.3.0
:Authors: 
:Citations: None
:Created: None
:Updated: None



Outputs
-----------

======  ==========  ===============
name    type        documentation
======  ==========  ===============
out     IndexedBam  Bam
======  ==========  ===============



Additional configuration (inputs)
---------------------------------

===================================  ==========================  =======================================  ==========  ======================================================================================================================================================================================================================================================================================================================================================================================================================================================================================================================================================================================================================================================================================================================================================================================================================================================================================================================================================================================================================================================================================================================================================================================================================================================================================================================================================================================================================================================
name                                 type                        prefix                                     position  documentation
===================================  ==========================  =======================================  ==========  ======================================================================================================================================================================================================================================================================================================================================================================================================================================================================================================================================================================================================================================================================================================================================================================================================================================================================================================================================================================================================================================================================================================================================================================================================================================================================================================================================================================================================================================================
outputFilename                       String                      --output                                             The directory to output SAM/BAM/CRAM files. Default value: '.'
bam                                  IndexedBam                  --input                                           1  (-I:String) BAM/SAM/CRAM file containing reads  This argument must be specified at least once.
intervals                            Optional<bed>               --intervals                                          (-L:String) One or more genomic intervals over which to operate This argument may be specified 0 or more times. Default value: null.
javaOptions                          Optional<Array<String>>
compression_level                    Optional<Integer>                                                                Compression level for all compressed files created (e.g. BAM and VCF). Default value: 2.
addOutputSamProgramRecord            Optional<Boolean>           -add-output-sam-program-record                       (--add-output-sam-program-record)  If true, adds a PG tag to created SAM/BAM/CRAM files.  Default value: true. Possible values: {true, false}
addOutputVcfCommandLine              Optional<Boolean>           -add-output-vcf-command-line                         (--add-output-vcf-command-line)  If true, adds a command line header line to created VCF files.  Default value: true. Possible values: {true, false}
arguments_file                       Optional<File>              --arguments_file:File                                read one or more arguments files and add them to the command line This argument may be specified 0 or more times. Default value: null.
cloudIndexPrefetchBuffer             Optional<String>            --cloud-index-prefetch-buffer                        (-CIPB:Integer)  Size of the cloud-only prefetch buffer (in MB; 0 to disable). Defaults to cloudPrefetchBuffer if unset.  Default value: -1.
cloudPrefetchBuffer                  Optional<String>            --cloud-prefetch-buffer                              (-CPB:Integer)  Size of the cloud-only prefetch buffer (in MB; 0 to disable).  Default value: 40.
createOutputBamIndex                 Optional<String>            --create-output-bam-index                            (-OBI:Boolean)  If true, create a BAM/CRAM index when writing a coordinate-sorted BAM/CRAM file.  Default value: true. Possible values: {true, false}
createOutputBamMd5                   Optional<String>            --create-output-bam-md5                              (-OBM:Boolean)  If true, create a MD5 digest for any BAM/SAM/CRAM file created  Default value: false. Possible values: {true, false}
createOutputVariantIndex             Optional<String>            --create-output-variant-index                        (-OVI:Boolean)  If true, create a VCF index when writing a coordinate-sorted VCF file.  Default value: true. Possible values: {true, false}
createOutputVariantMd5               Optional<String>            --create-output-variant-md5                          (-OVM:Boolean)  If true, create a a MD5 digest any VCF file created.  Default value: false. Possible values: {true, false}
disableBamIndexCaching               Optional<String>            --disable-bam-index-caching                          (-DBIC:Boolean)  If true, don't cache bam indexes, this will reduce memory requirements but may harm performance if many intervals are specified.  Caching is automatically disabled if there are no intervals specified.  Default value: false. Possible values: {true, false}
disableReadFilter                    Optional<String>            --disable-read-filter                                (-DF:String)  Read filters to be disabled before analysis  This argument may be specified 0 or more times. Default value: null. Possible Values: {WellformedReadFilter}
disableSequenceDictionaryValidation  Optional<Boolean>           -disable-sequence-dictionary-validation              (--disable-sequence-dictionary-validation)  If specified, do not check the sequence dictionaries from our inputs for compatibility. Use at your own risk!  Default value: false. Possible values: {true, false}
excludeIntervals                     Optional<String>            --exclude-intervals                                  (-XL:StringOne) This argument may be specified 0 or more times. Default value: null.
gatkConfigFile                       Optional<File>              --gatk-config-file                                   A configuration file to use with the GATK. Default value: null.
gcsRetries                           Optional<Integer>           -gcs-retries                                         (--gcs-max-retries)  If the GCS bucket channel errors out, how many times it will attempt to re-initiate the connection  Default value: 20.
gcsProjectForRequesterPays           Optional<String>            --gcs-project-for-requester-pays                     Project to bill when accessing requester pays  buckets. If unset, these buckets cannot be accessed.  Default value: .
intervalExclusionPadding             Optional<Integer>           --interval-exclusion-padding                         (-ixp:Integer)  Amount of padding (in bp) to add to each interval you are excluding.  Default value: 0.
imr                                  Optional<String>            -imr:IntervalMergingRule                             (--interval-merging-rule)  Interval merging rule for abutting intervals  Default value: ALL. Possible values: {ALL, OVERLAPPING_ONLY}
ip                                   Optional<Integer>           -ip                                                  (--interval-padding) Default value: 0.
isr                                  Optional<String>            -isr:IntervalSetRule                                 (--interval-set-rule)  Set merging approach to use for combining interval inputs  Default value: UNION. Possible values: {UNION, INTERSECTION}
le                                   Optional<Boolean>           --lenient                                            (-LE) Lenient processing of VCF files Default value: false. Possible values: {true, false}
quiet                                Optional<Boolean>           --QUIET                                              Whether to suppress job-summary info on System.err. Default value: false. Possible values: {true, false}
readFilter                           Optional<String>            --read-filter                                        (-RF:String) Read filters to be applied before analysis This argument may be specified 0 or more times. Default value: null. Possible Values: {AlignmentAgreesWithHeaderReadFilter, AllowAllReadsReadFilter, AmbiguousBaseReadFilter, CigarContainsNoNOperator, FirstOfPairReadFilter, FragmentLengthReadFilter, GoodCigarReadFilter, HasReadGroupReadFilter, IntervalOverlapReadFilter, LibraryReadFilter, MappedReadFilter, MappingQualityAvailableReadFilter, MappingQualityNotZeroReadFilter, MappingQualityReadFilter, MatchingBasesAndQualsReadFilter, MateDifferentStrandReadFilter, MateOnSameContigOrNoMappedMateReadFilter, MateUnmappedAndUnmappedReadFilter, MetricsReadFilter, NonChimericOriginalAlignmentReadFilter, NonZeroFragmentLengthReadFilter, NonZeroReferenceLengthAlignmentReadFilter, NotDuplicateReadFilter, NotOpticalDuplicateReadFilter, NotSecondaryAlignmentReadFilter, NotSupplementaryAlignmentReadFilter, OverclippedReadFilter, PairedReadFilter, PassesVendorQualityCheckReadFilter, PlatformReadFilter, PlatformUnitReadFilter, PrimaryLineReadFilter, ProperlyPairedReadFilter, ReadGroupBlackListReadFilter, ReadGroupReadFilter, ReadLengthEqualsCigarLengthReadFilter, ReadLengthReadFilter, ReadNameReadFilter, ReadStrandFilter, SampleReadFilter, SecondOfPairReadFilter, SeqIsStoredReadFilter, SoftClippedReadFilter, ValidAlignmentEndReadFilter, ValidAlignmentStartReadFilter, WellformedReadFilter}
readIndex                            Optional<String>            -read-index                                          (--read-index)  Indices to use for the read inputs. If specified, an index must be provided for every read input and in the same order as the read inputs. If this argument is not specified, the path to the index for each input will be inferred automatically.  This argument may be specified 0 or more times. Default value: null.
readValidationStringency             Optional<String>            --read-validation-stringency                         (-VS:ValidationStringency)  Validation stringency for all SAM/BAM/CRAM/SRA files read by this program.  The default stringency value SILENT can improve performance when processing a BAM file in which variable-length data (read, qualities, tags) do not otherwise need to be decoded.  Default value: SITool returned: 0 LENT. Possible values: {STRICT, LENIENT, SILENT}
reference                            Optional<FastaWithIndexes>  --reference                                          (-R:String) Reference sequence Default value: null.
secondsBetweenProgressUpdates        Optional<Double>            -seconds-between-progress-updates                    (--seconds-between-progress-updates)  Output traversal statistics every time this many seconds elapse  Default value: 10.0.
sequenceDictionary                   Optional<String>            -sequence-dictionary                                 (--sequence-dictionary)  Use the given sequence dictionary as the master/canonical sequence dictionary.  Must be a .dict file.  Default value: null.
sitesOnlyVcfOutput                   Optional<Boolean>           --sites-only-vcf-output:Boolean                      If true, don't emit genotype fields when writing vcf file output.  Default value: false. Possible values: {true, false}
splitLibraryName                     Optional<String>            --split-library-name                                 (-LB)  Split file by library.  Default value: false. Possible values: {true, false}
rg                                   Optional<String>            --split-read-group                                   (-RG:BooleanSplit) Default value: false. Possible values: {true, false}
splitSample                          Optional<String>            --split-sample                                       (-SM:Boolean) Split file by sample. Default value: false. Possible values: {true, false}
tmpDir                               Optional<String>            --tmp-dir:GATKPathSpecifier                          Temp directory to use. Default value: null.
jdkDeflater                          Optional<Boolean>           -jdk-deflater                                        (--use-jdk-deflater)  Whether to use the JdkDeflater (as opposed to IntelDeflater)  Default value: false. Possible values: {true, false}
jdkInflater                          Optional<Boolean>           -jdk-inflater                                        (--use-jdk-inflater)  Whether to use the JdkInflater (as opposed to IntelInflater)  Default value: false. Possible values: {true, false}
verbosity                            Optional<String>            -verbosity:LogLevel                                  (--verbosity)  Control verbosity of logging.  Default value: INFO. Possible values: {ERROR, WARNING, INFO, DEBUG}
disableToolDefaultReadFilters        Optional<Boolean>           -disable-tool-default-read-filters                   (--disable-tool-default-read-filters)  Disable all tool default read filters (WARNING: many tools will not function correctly without their default read filters on)  Default value: false. Possible values: {true, false}
ambigFilterBases                     Optional<Integer>           --ambig-filter-bases                                 Threshold number of ambiguous bases. If null, uses threshold fraction; otherwise, overrides threshold fraction.  Default value: null.  Cannot be used in conjuction with argument(s) maxAmbiguousBaseFraction
ambigFilterFrac                      Optional<Double>            --ambig-filter-frac                                  Threshold fraction of ambiguous bases Default value: 0.05. Cannot be used in conjuction with argument(s) maxAmbiguousBases
maxFragmentLength                    Optional<Integer>           --max-fragment-length                                Default value: 1000000.
minFragmentLength                    Optional<Integer>           --min-fragment-length                                Default value: 0.
keepIntervals                        Optional<String>            --keep-intervals                                     Valid only if "IntervalOverlapReadFilter" is specified: One or more genomic intervals to keep This argument must be specified at least once. Required.
library                              Optional<String>            -library                                             (--library) Valid only if "LibraryReadFilter" is specified: Name of the library to keep This argument must be specified at least once. Required.
maximumMappingQuality                Optional<Integer>           --maximum-mapping-quality                            Maximum mapping quality to keep (inclusive)  Default value: null.
minimumMappingQuality                Optional<Integer>           --minimum-mapping-quality                            Minimum mapping quality to keep (inclusive)  Default value: 10.
dontRequireSoftClipsBothEnds         Optional<Boolean>           --dont-require-soft-clips-both-ends                  Allow a read to be filtered out based on having only 1 soft-clipped block. By default, both ends must have a soft-clipped block, setting this flag requires only 1 soft-clipped block  Default value: false. Possible values: {true, false}
filterTooShort                       Optional<Integer>           --filter-too-short                                   Minimum number of aligned bases Default value: 30.
platformFilterName                   Optional<String>            --platform-filter-name:String                        This argument must be specified at least once. Required.
blackListedLanes                     Optional<String>            --black-listed-lanes:String                          Platform unit (PU) to filter out This argument must be specified at least once. Required.
readGroupBlackList                   Optional<String>            --read-group-black-list:StringThe                    This argument must be specified at least once. Required.
keepReadGroup                        Optional<String>            --keep-read-group:String                             The name of the read group to keep Required.
maxReadLength                        Optional<Integer>           --max-read-length                                    Keep only reads with length at most equal to the specified value Required.
minReadLength                        Optional<Integer>           --min-read-length                                    Keep only reads with length at least equal to the specified value Default value: 1.
readName                             Optional<String>            --read-name:String                                   Keep only reads with this read name Required.
keepReverseStrandOnly                Optional<Boolean>           --keep-reverse-strand-only                           Keep only reads on the reverse strand  Required. Possible values: {true, false}
sample                               Optional<String>            -sample:String                                       (--sample) The name of the sample(s) to keep, filtering out all others This argument must be specified at least once. Required.
invertSoftClipRatioFilter            Optional<Boolean>           --invert-soft-clip-ratio-filter                      Inverts the results from this filter, causing all variants that would pass to fail and visa-versa.  Default value: false. Possible values: {true, false}
softClippedLeadingTrailingRatio      Optional<Double>            --soft-clipped-leading-trailing-ratio                Threshold ratio of soft clipped bases (leading / trailing the cigar string) to total bases in read for read to be filtered.  Default value: null.  Cannot be used in conjuction with argument(s) minimumSoftClippedRatio
softClippedRatioThreshold            Optional<Double>            --soft-clipped-ratio-threshold                       Threshold ratio of soft clipped bases (anywhere in the cigar string) to total bases in read for read to be filtered.  Default value: null.  Cannot be used in conjuction with argument(s) minimumLeadingTrailingSoftClippedRatio
===================================  ==========================  =======================================  ==========  ======================================================================================================================================================================================================================================================================================================================================================================================================================================================================================================================================================================================================================================================================================================================================================================================================================================================================================================================================================================================================================================================================================================================================================================================================================================================================================================================================================================================================================================================
