# GPU Server Usage Rules and Best Practices

## User Rights and Access

1. **User Names**: User names should be unique, easily recognizable.

   - Example User Names: `miyoshi`, `sun`, `tanaka`

2. **Password Policy**: For users who choose to log in using a password, ensure that it is a strong, unique password to enhance security. We recommend to use SSH keys (RSA) for authentication.

3. **Server Reservation**: Enter expected time of use, server number, and number of GPUs in the google calendar. Contact Dr. Miyoshi for calendar access.

## GPU Server Usage

### User Rights and Access

**User Privileges**: While users have sudo rights, please exercise caution and discretion. Avoid making changes to shared system settings without prior approval from the lab administrators.

Basically, all users are granted sudo privileges; however, exercise caution when using sudo to modify shared environments or data. If you need to make updates or changes, please report them in advance through the GPU channel.
### GPU Usage

1. **Report Protocol**:
    - When using a GPU, please report details such as your username, the server name, and the specific GPU(s) you wish to use.
    - It's essential to accurately estimate your usage time, as it helps other users plan their work efficiently.
  
    Example:
    ```Server: S5: GPU: 1,2. Perspective Time: 4 hours.```

1. **Avoiding Shared GPUs**: To minimize conflicts and maintain a fair usage policy, avoid using GPUs claimed by other users. Check the Slack channel for real-time GPU availability status.

2. **GPU Memory Management**:
   - Besides releasing GPU memory, also ensure that you terminate your processes and sessions correctly when you finish your work.
   - Use monitoring commands to check GPU memory usage and to identify any lingering processes.
   - Make sure you release all GPU memory when you finish the use of the GPU machine, especially for Jupyter users. Sometime, the GPU memory still occupied even you stop the program, in this case, you need to use `kill` command to kill the process.


### Independent Development Environment

1. **Recommendation**:
   - We strongly suggest utilizing Docker or Conda virtual environments to create isolated development environments. This prevents conflicts between different software packages and versions used by lab members.

2. **Documentation and Sharing**:
   - Document your environment setup and dependencies for future reference and easy sharing with colleagues. This documentation can save time when onboarding new lab members or when troubleshooting issues.

3. **Data Backups**:
   - Regularly back up your work and data. Hardware failures or unexpected issues can lead to data loss. Use the lab's designated backup system or an external storage solution.

4. **Resource Efficiency**:
   - Ensure that your code is optimized for GPU use. Avoid resource wastage by writing efficient code that minimizes GPU memory consumption.

5. **Communication**: Active communication is vital for efficient resource sharing. If you foresee a lengthy GPU usage time, consider collaborating with other lab members and coordinating schedules to minimize resource contention.

6. **Security and Privacy**:
   - Protect sensitive data and code. Ensure that your GPU server environment is secure, and follow lab security policies for data access and sharing.

7. **Cleanliness**:
   - Keep your development environment and files organized. Remove unnecessary files and data regularly to maintain optimal storage space.
  
## Docker Image/Container Names

1. **Docker Image Names**: Choose descriptive and specific names for your Docker images: project_username_version.

   - Example Docker Image Name:  `motionmodel_miyoshi_v1`.

2. **Docker Container Names**: When you run a Docker container, give it a meaningful name based on the purpose or task it's performing, including you name. 

   - Example Docker Container Name: `meta_model_miyoshi`. 
3. Do not access the container/image that is not yours.
4. Clean up your containers/images when you do not need them.

## File Name Convention

1. **File Name Convention**: Follow a consistent and descriptive file naming convention for data, code, and documentation.

   - For datasets: Use a convention that includes the data source, date, and version if applicable, e.g., `astro_data_2023_v1.csv`.
   
   - For code scripts: Include a brief description of the script's purpose, e.g., `data_preprocessing.py`, `model_training.ipynb`.

   - For documentation: Use clear names and include the date or version for easy reference, e.g., `project_report_v2.pdf`, `experiment_notes_2023-10-13.txt`.

## Specific Command Examples

1. **Docker Image Creation**:

   - Create a Docker image from a Dockerfile:
     ```bash
     docker build -t ml_project_image /path/to/dockerfile_directory
     ```
    - Pull a Docker image from Docker Hub:
      ```bash
      docker pull ml_project_image
      ```
2. **Docker Container Launch**:

   - Start a Docker container with a specific name:
     ```bash
     docker run --name ml_container1 -it ml_project_image
     ```
3. **Using conda virtual envrioment**
   - Create a conda virtual environment:
     ```bash
     conda create -n myenv python=3.6 pip
     ```
    - Activate the conda virtual environment:
      ```bash
        conda activate myenv
        ```
    - Deactivate the conda virtual environment:
    - ```bash
        conda deactivate
        ```
    - Install packages in the conda virtual environment:
    - ```bash
        conda install numpy
        ```
    - List all conda virtual environments:
    - ```bash
        conda env list
        ```
    - Remove a conda virtual environment:
    - ```bash
        conda env remove -n myenv
        ``` 
4. **GPU Memory Check**:

   - Use `nvidia-smi` to monitor GPU memory usage and identify processes using the GPU resources:
     ```bash
     nvidia-smi
     ```

5. **Data Backup**:

   - Create a backup of a file or directory using `rsync`:
     ```bash
     rsync -av /path/to/source /path/to/backup
     ```


5. **Monitoring Tools**:

   - Install and use `nvidia-smi` and `gpustat` for real-time GPU monitoring:
     ```bash
     nvidia-smi
     gpustat
     ```

6. **Data Security**:

   - Encrypt sensitive files using GPG:
     - To encrypt: `gpg -c sensitive_data.txt`
     - To decrypt: `gpg -d sensitive_data.txt.gpg`

7. **File transfer between machines**

    To upload a file from your local machine to a GPU server:
   - `scp /path/to/local/file username@remote_host:/path/to/remote/file`
    To download a file from a GPU server to your local machine:
    - `scp username@remote_host:/path/to/remote/file /path/to/local/file`


By following these rules, best practices, naming conventions, and command examples, you contribute to a more organized, efficient, and secure working environment in your lab, ensuring that GPU resources are used effectively while promoting a harmonious working atmosphere.
