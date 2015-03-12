# Ainos Cluster Setup Guide

## Set up ClearNLP on your ainos profile

    1. ssh ACCOUNT at ainos.mathcs.emory.edu
    2. cp -r ~henryyhc/share/* .
    3. cd scripts
    4. vim template.slurm
    5. Change the value of USERNAME to your account name
> You will no longer need your own ClearNLP jar files once the shared library is set up.

***
## How to submit task to ainos

###Generate jar file

1. Create 'rsynch.sh' under PROJECT_DIR/target/classes with the following code 

        #!/bin/bash
        JARNAME=clearnlp_xx.jar
        jar cf $JARNAME edu
        rsync -avc $JARNAME ACCOUNT@ainos.mathcs.emory.edu:~/jar
> clearnlp_xx is the name of your project

2. Run the shell script and upload the jar file to ainos

        sh PROJECT_DIR/target/classes/rsynch.sh

3. The jar file should be uploaded to ~ACCOUNT/jar/ at ainos

###Submit a task to ainos

1. ssh onto ainos

        ssh ACCOUNT@ainos.mathcs.emory.edu

2. Copy and modify the templete.slurm
        
        cd ~/scripts
        mkdir clearnlp-xx
        cp templete.slurm ./clearnlp-xx/clearnlp-xx.slurm
        cd clearnlp-xx

3. Modify the parameters in clearnlp-xx.slurm

        #SBATCH --job-name=JOB_NAME
        #SBATCH --time=02:00:00
        #SBATCH --ntasks=1
        #SBATCH --cpus-per-task=1
        #SBATCH --mem-per-cpu=2000
    
        ...
    
        # Jar files to run
        export JAR=/home/$USERNAME/jar
        export CLEARNLP_COREF=$JAR/clearnlp-xx.jar

        # Environment parameters
        ... Add variable(s) if needed

        # Run line
        java edu.emory.clir.clearnlp.CLASS_PATH

    > Please change JOB_NAME to your task name, and unit for mem-per-cpu: MB

4. Submit task to ainos

        sbatch clearnlp-xx.slurm
> Output file will be created within the directory of clearnlp-xx.slurm

###View/Kill running task(s) (if needed)

View the task queue

    squeue

Kill a running task

    scancel TASK_NAME

***
## (Optional) Set up ssh profile fingerprint: ssh with no password

**On your local machine**

    1. cd ~/.ssh #(mkdir ~/.ssh if directory does not exist)
    2. ssh-keygen -t rsa #(hit enter all the way with no input)
    3. cat id_rsa.pub
    4. Copy all fingerprint info that Step 3 gives

**On ainos**

    1. ssh ACCOUNT@ainos.mathcs.emory.edu
    2. cd ~/.ssh #(mkdir ~/.ssh if directory does not exist)
    3. vim authorized_keys
    4. Paste the all fingerprint info copied from your local machine
    5. chmod 700 ~/.ssh
    6. chmod 640 ~/.ssh/authorized_keys
