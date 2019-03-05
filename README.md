# Intro

This is a fork of https://github.com/SchedMD/slurm-gcp - an elastic slurm cluster in the cloud. Not using elasticity at all - using this cluster as a testbed. 

## Stand-alone Cluster in Google Cloud Platform

The supplied scripts can be used to create a stand-alone cluster in Google Cloud
Platform. The scripts setup the following scenario:

* 1 - controller node
* 1 - login node
* 2 - compute nodes

The default image for the instances is CentOS 7; changed the slurm version to 17.11.7 to reflect Amarel. 

On the controller node, slurm is installed in:
/apps/slurm/<slurm_version>
with the symlink /apps/slurm/current pointing to /apps/slurm/<slurm_version>.

The login nodes mount /apps and /home from the controller node.

To deploy, you must have a GCP account and have the GCP Cloud SDK installed.  
See [Cloud Cloud SDK](https://cloud.google.com/sdk/downloads).

   
From the root of your slurm-gcp repo, lauch: 
   ```
   $ gcloud deployment-manager deployments [--project=<project id>] create slurm --config slurm-cluster.yaml
   ```

You can login either from the gcp console or ssh into the nodes. Restart slurmctld at will. 


