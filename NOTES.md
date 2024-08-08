### August 8, 2024
* Stephanie has submitted the ISR for a new xnat2-compute node and a memory upgrade for xnat2 to 12 GB.
* As xnat2 has Docker v27 installed Brian is trying to install the dev version of the Container Service (3.5.0 pre-release) as it fixes the incompatibility problems between the CS and Docker >v24. 


### August 2, 2024
* To do next week: Brian will try to update the container service to the beta 3.5.0 release to see if it will retrieve Docker containers. No further testing can be done until the compute VM is online.
* If the quote on the VM is available it needs to be made clear that the xnat2 server will also get updated to the compute VM specs.

### August 1, 2024
* Docker v27 was installed on `xnat2.bu.edu`, which is not what was requested in ticket (INC20379296)[https://bu.service-now.com/sp?id=form&table=incident&view=sp&sys_id=2199e88797638e10ff07f027f053aff4]. However, the [current dev version](https://bitbucket.org/xnatdev/container-service/src/dev/CHANGELOG.md) of the Container Service allows for newer Docker versions to be used. Once the XNAT service is restored I will install the dev version and see if it works ok
* An update to the Tomcat version on July 30 broke the XNAT service. See ticket [INC20382305](https://bu.service-now.com/nav_to.do?uri=%2Fincident.do%3Fsys_id%3D19b2aea8c37f0e50155dd2da05013131)

### July 26, 2024

* Mitch has submitted info on the ticket to get a compute VM created.  That then triggered more paperwork for all of the VMs plus the NAT.
* original xnat VMs will stay alive for now.
* It looks like CNC has been paying the bill for the 2 original xnat VMs plus the NAS. xnat2 hasn't been billed yet.  xnat2 and xnat-compute will be billed to the CNC, once we know pricing (expected to be pretty modest). Stephanie will submit an ISR for that.  
* Docker software needs to be installed on xnat2.bu.edu so that it can pull containers. But it must be version 24 or older to avoid a compatibility problem with xnat.  Mitch says to submit a ticket to the Sys Admin group and ask them to do it. (brian will do that) DONE - INC20379296
* We discussed increasing the specs on xnat2 VM to be the same as the compute VM (4 cores, 16GB RAM) as it's currently pretty minimal (2 cores, 4GB RAM). Once the quote comes in the ISR can be adjusted.
* note the postgres admin account setup is described in the Wiki.


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
