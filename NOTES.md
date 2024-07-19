### July 22, 2024
Brian, Josh, Mitch, Stephanie

  * TBD

### July 15, 2024

Brian, Josh, Mitch, Stephanie

* boldqc vs mriqc - we discussed these two quality-checking pipelines. Boldqc has the advantage of being easier to set up,
  but it's Harvard's in-house tool. It is older and does not have as many features as mriqc.  mriqc is much more widely used and we can expect longer-term support for it. It will take
  more work to get mriqc set up with xnat2. There is currently a series of Docker containers that are orchestrated to run mriqc.
  It is also possible to roll them into one container for convenience, see [this discussion](https://groups.google.com/g/xnat_discussion/c/3DLtaArns3I)
* Brian has a version of the Harvard "executors" code working with the SGE, which is used by their boldqc script to submit jobs to a cluster.
* For long-term support Stephanie prefers mriqc, so that will be investigated further.
* xnat2 is used to move files to the NAS from the MRI's computer using some bash scripts from the xnat-mribkup github repo. This is linked in the Code
  section of this repo.
* Container options: if it's low or no cost, running mriqc on a container hosted by IS&T would be the most convenient as this is already supported by
  xnat2. xnat2 has convenient integration of custom run options in its GUI for commands that exist within a Docker container. The Container Service is
  already enabled in xnat2. Option 2: write a custom Docker container that submits a job to the SCC to run mriqc. Option 3: tag scans in xnat2 to be
  processed by mriqc on the SCC, and a cronjob looks for the scans and submits them to the SCC using bash.
* The division of responsibility for the xnat2 service needs to be described in the Wiki - who keeps an eye on the mribkup script,
  the health of the NAS, handles accounts on xnat2, etc?  

### Earlier
