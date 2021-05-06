# Demux using QIIME1: Snake workflow for HTCF

1. Login to HTCF.
2. Move to your /scratch/ directory.
3. Clone the repo:
```
git clone --recurse-submodules https://github.com/RachelRodgers/demux-htcf-snake.git
```
4. Make a directory to hold the snakemake profile:
```
mkdir -p ~/.config/snakemake/slurm_demux
```
5. Edit line 2 of the config.yaml file to include your email address:
```
--mail-user=<yourEmailAddress>
```
6. Copy the cluster submit and profile files to the appropriate locations:
```
cd demux-htcf-snake
cp config/config.yaml ~/.config/snakemake/slurm_demux
cp slurm-submit/*.py ~/.config/snakemake
```
7. Create a directory to hold your sequences to be demultiplexed and move your data to that directory.
8. Create a directory to hold your mapping file and copy your mapping file to that directory.
9. Edit the ./config/demux_config.yaml file appropriately.
10. Submit in one of two ways:
	a. With sbatch script:
	```
	sbatch submit_demux_snake.sbatch
	```
	b. Interactively:
	```
	# start an interactive session
	interactive

	# load snakemake 5.10
	ml snakemake/5.10.0-python-3.6.5

	# dry run (prints steps and stops)
	snakemake --profile slurm_demux -np

	# production run:
	snakemake --profile slurm_demux
	```
11. See slurm output files in the logs_slurm/ directory which will generate inside the repository's directory.
