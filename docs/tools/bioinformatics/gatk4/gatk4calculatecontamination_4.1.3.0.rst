:orphan:

GATK4: CalculateContamination
===========================================================

*1 contributor · 3 versions*

Calculates the fraction of reads coming from cross-sample contamination, given results from GetPileupSummaries. The resulting contamination table is used with FilterMutectCalls.

This tool is featured in the Somatic Short Mutation calling Best Practice Workflow. See Tutorial#11136 for a step-by-step description of the workflow and Article#11127 for an overview of what traditional somatic calling entails. For the latest pipeline scripts, see the Mutect2 WDL scripts directory.

This tool borrows from ContEst by Cibulskis et al the idea of estimating contamination from ref reads at hom alt sites. However, ContEst uses a probabilistic model that assumes a diploid genotype with no copy number variation and independent contaminating reads. That is, ContEst assumes that each contaminating read is drawn randomly and independently from a different human. This tool uses a simpler estimate of contamination that relaxes these assumptions. In particular, it works in the presence of copy number variations and with an arbitrary number of contaminating samples. In addition, this tool is designed to work well with no matched normal data. However, one can run GetPileupSummaries on a matched normal bam file and input the result to this tool.


Quickstart
-----------

    .. code-block:: python

       from janis_bioinformatics.tools.gatk4.calculatecontaminations.versions import Gatk4CalculateContamination_4_1_3

       wf = WorkflowBuilder("myworkflow")

       wf.step(
           "gatk4calculatecontamination_step",
           Gatk4CalculateContamination_4_1_3(
               pileupTable=None,
           )
       )
       wf.output("contOut", source=gatk4calculatecontamination_step.contOut)
       wf.output("segOut", source=gatk4calculatecontamination_step.segOut)
    

*OR*

1. `Install Janis </tutorials/tutorial0.html>`_

2. Ensure Janis is configured to work with Docker or Singularity.

3. Ensure all reference files are available:

.. note:: 

   More information about these inputs are available `below <#additional-configuration-inputs>`_.



4. Generate user input files for Gatk4CalculateContamination:

.. code-block:: bash

   # user inputs
   janis inputs Gatk4CalculateContamination > inputs.yaml



**inputs.yaml**

.. code-block:: yaml

       pileupTable: pileupTable




5. Run Gatk4CalculateContamination with:

.. code-block:: bash

   janis run [...run options] \
       --inputs inputs.yaml \
       Gatk4CalculateContamination





Information
------------


:ID: ``Gatk4CalculateContamination``
:URL: `https://software.broadinstitute.org/gatk/documentation/tooldocs/4.1.2.0/org_broadinstitute_hellbender_tools_walkers_contamination_CalculateContamination.php <https://software.broadinstitute.org/gatk/documentation/tooldocs/4.1.2.0/org_broadinstitute_hellbender_tools_walkers_contamination_CalculateContamination.php>`_
:Versions: 4.1.4.0, 4.1.3.0, 4.1.2.0
:Container: broadinstitute/gatk:4.1.3.0
:Authors: Hollizeck Sebastian
:Citations: TBD
:Created: 2019-09-09
:Updated: 2019-09-09



Outputs
-----------

=======  ======  =========================
name     type    documentation
=======  ======  =========================
contOut  File    contamination Table
segOut   File    segmentation based on baf
=======  ======  =========================



Additional configuration (inputs)
---------------------------------

====================  =======================  ==================================  ==========  =============================================================================================================================================
name                  type                     prefix                                position  documentation
====================  =======================  ==================================  ==========  =============================================================================================================================================
pileupTable           File                     -I                                              pileup table from summarize pileup
javaOptions           Optional<Array<String>>
compression_level     Optional<Integer>                                                        Compression level for all compressed files created (e.g. BAM and VCF). Default value: 2.
contaminationTable    Optional<File>           --contamination-table                           Tables containing contamination information.
statsFile             Optional<File>           --stats                                         The Mutect stats file output by Mutect2
readOrientationModel  Optional<File>           --orientation-bias-artifact-priors              One or more .tar.gz files containing tables of prior artifact probabilities for the read orientation filter model, one table per tumor sample
segmentationFileOut   Optional<Filename>       --tumor-segmentation                            Reference sequence file
contaminationFileOut  Optional<Filename>       -O                                           2
====================  =======================  ==================================  ==========  =============================================================================================================================================
