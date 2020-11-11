# HTCondor Snakemake profile

This profile configures Snakemake to submit jobs to the grid via DIRAC. This is primarily aimed for users of CERN/ganga.

### Prerequisites
Assumes you have valid access to DIRAC.

### Deploy profile

To deploy this profile run

    mkdir -p ~/.config/snakemake
    cd ~/.config/snakemake
    cookiecutter https://github.com/Snakemake-Profiles/htcondor.git

You will be asked for the name of the profile and for a path where the HTCondor logs will be stored. 
The logs will be used to update the status of submitted jobs (as recommended in the [documentation of the HTCondor Python bindings](https://htcondor.readthedocs.io/en/latest/apis/python-bindings/advanced/Scalable-Job-Tracking.html)).

Then, you can run Snakemake with

    snakemake --profile ganga_dirac ...

so that jobs are submitted to the cluster. If Snakemake is killed and restarted afterwards, it will automatically resume still running jobs.
