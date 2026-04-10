---
name: nus-hpc-vanda
description: Access, manage, and submit jobs to the NUS HPC Vanda cluster. Use this when you need to SSH into vanda.nus.edu.sg, manage PBS jobs, or handle files on the Vanda cluster for user e1547144.
---

# NUS HPC Vanda Skill

This skill provides procedures for interacting with the NUS High-Performance Computing (HPC) cluster, specifically "Vanda".

## Core Functionality

- **SSH Access**: Connect to `vanda.nus.edu.sg` via SSH.
- **Job Submission**: Prepare and submit PBS scripts.
- **Job Management**: Monitor or cancel jobs using PBS commands.
- **Software Management**: Load and manage environment modules.
- **File Transfers**: Upload scripts and download results.

## Quick Reference

See [vanda_guide.md](references/vanda_guide.md) for detailed commands, storage paths, and module information.

## Workflows

### 1. SSH into Vanda
User: `e1547144`
Host: `vanda.nus.edu.sg`
Port: `22`

```bash
ssh e1547144@vanda.nus.edu.sg
```
*Note: Ensure NUS VPN is connected if off-campus.*

### 2. Submit a GPU Job
1. Create a PBS script (see template in references).
2. Submit using `qsub`:
   ```bash
   qsub my_script.pbs
   ```

### 3. Check Job Status
```bash
qstat -u e1547144
```

### 4. Interactive GPU Session
```bash
qsub -I -q volta_gpu -l select=1:ncpus=10:ngpus=1
```
