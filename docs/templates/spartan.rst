Spartan
=======

Template ID: ``spartan``


https://dashboard.hpc.unimelb.edu.au/


Quickstart
-----------

Take note below how to configure the template. This quickstart only includes the fields you absolutely require. This will write a new configuration to ``~/.janis.conf``. See `configuring janis <https://janis.readthedocs.io/en/latest/references/configuration.html>`__ for more information.

.. code-block:: bash

   janis init spartan \
       --container_dir <value>
   
   # or to find out more information
   janis init spartan --help

OR you can insert the following lines into your template:

.. code-block:: yaml

   template:
     id: spartan
     container_dir: <value>



Fields
-------

**Required**

=============  =============  ===============
ID             Type           Documentation
=============  =============  ===============
container_dir  <class 'str'>
=============  =============  ===============

**Optional**

===================  ===================================  =======================  ========================================================
ID                   Type                                 Default                  Documentation
===================  ===================================  =======================  ========================================================
execution_dir        <class 'str'>                                                 execution directory for Cromwell
queues               typing.Union[str, typing.List[str]]  cloud                    The queue to submit jobs to
singularity_version  <class 'str'>                        3.2.0-spartan_gcc-6.2.0
send_job_emails      <class 'bool'>                       True                     Send SLURM job emails to the listed email address
catch_slurm_errors   <class 'bool'>                       True                     Fail the task if Slurm kills the job (eg: memory / time)
max_cores            <class 'int'>                        32                       Override maximum number of cores (default: 32)
max_ram              <class 'int'>                        508                      Override maximum ram (default 508 [GB])
submission_queue     <class 'str'>                        cloud
max_workflow_time    <class 'int'>                        20100
janis_memory_mb
===================  ===================================  =======================  ========================================================

