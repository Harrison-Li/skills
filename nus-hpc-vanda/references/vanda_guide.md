# NUS HPC Vanda Reference

## Connection Details

- **Hostname:** `vanda.nus.edu.sg`
- **Username:** `e1547144`
- **Port:** `22`
- **Network:** Requires NUS VPN if off-campus.

## Job Scheduling (PBS Pro)

Vanda uses PBS Pro for job management.

### Essential Commands

- `qsub <script.pbs>`: Submit a batch job.
- `qstat -u <username>`: Check your job status.
- `qdel <job_id>`: Delete a job.
- `qsub -I`: Start an interactive session.

### Common Queues

- `volta_gpu`: For GPU-intensive tasks.
- `normal`: For standard CPU tasks.

## Storage

- **Home:** `/home/svu/e1547144` (Quota limited, backed up).
- **Scratch:** `/scratch/e1547144` (High performance, periodic purging).

## Software (Modules)

- `module avail`: List all available software.
- `module load <name>`: Load a specific module.
- `module unload <name>`: Unload a module.
- `module list`: Show currently loaded modules.

## Example PBS Script

```bash
#!/bin/bash
#PBS -N my_job
#PBS -P personal-e1547144
#PBS -l select=1:ncpus=36:mem=100gb:ngpus=1
#PBS -l walltime=5:00:00
#PBS -j oe
#PBS -o redox_opt_test_long.log

cd $PBS_O_WORKDIR
module load cuda12.2
source .venv/bin/activate
echo "Job started on $(date)"
echo "Running on host $(hostname)"
echo "Current directory: $(pwd)"
python my_script.py
```
