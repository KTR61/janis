Pbs Singularity
===============

Template ID: ``pbs_singularity``



Quickstart
-----------

Take note below how to configure the template. This quickstart only includes the fields you absolutely require. This will write a new configuration to ``~/.janis.conf``. See `configuring janis <https://janis.readthedocs.io/en/latest/references/configuration.html>`__ for more information.

.. code-block:: bash

   janis init pbs_singularity \
       --container_dir <value>
   
   # or to find out more information
   janis init pbs_singularity --help

OR you can insert the following lines into your template:

.. code-block:: yaml

   template:
     id: pbs_singularity
     container_dir: <value>



Fields
-------

**Required**

=============  =============  ==================================================
ID             Type           Documentation
=============  =============  ==================================================
container_dir  <class 'str'>  Location where to save and execute containers from
=============  =============  ==================================================

**Optional**

=============================  ===================================  ==========================================  ==========================================================================================
ID                             Type                                 Default                                     Documentation
=============================  ===================================  ==========================================  ==========================================================================================
intermediate_execution_dir     <class 'str'>
queues                         typing.Union[str, typing.List[str]]                                              A queue that work should be submitted to
mail_program                                                                                                    Mail program to pipe email to, eg: 'sendmail -t'
send_job_emails                <class 'bool'>                       False                                       (requires JanisConfiguration.notifications.email to be set) Send emails for mail types END
catch_pbs_errors               <class 'bool'>                       True
build_instructions             <class 'str'>                        singularity pull $image docker://${docker}  Instructions for building singularity, it's recommended to not touch this setting.
singularity_load_instructions                                                                                   Ensure singularity with this command executed in shell
max_cores                                                                                                       Maximum number of cores a task can request
max_ram                                                                                                         Maximum amount of ram (GB) that a task can request
can_run_in_foreground          <class 'bool'>                       True
run_in_background              <class 'bool'>                       False
=============================  ===================================  ==========================================  ==========================================================================================

