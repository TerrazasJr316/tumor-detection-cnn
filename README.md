# tumor-detection-cnn

## 🎯 Features

## 🛠️ Technologies Used

### Development environment

* **Anaconda Navigator 2.7+** – Environment configuration and workspace management

### Programming lenguage

* **Terminal** – Installation of libraries and packages
* **Python3** - Code development.
* **Jupyter Lab** – Code development and documentation

### Libraries & Frameworks

* **NumPy** – Mathematical operations and data structures
* **Pandas** – Data manipulation and analysis
* **Matplotlib** – Data visualization
* **Scikit-learn** – Training of classic ML models and clustering

## 📦 Installation and Configuration

### Requirements

* Python 3.10+ (stable version)
* Linux operating system (any distribution, recommended)
* Virtual environment in Anaconda Navigator

### 1. Clone the repository

```bash
git clone https://github.com/TerrazasJr316/tumor-detection-cnn.git
cd linear-forecasting
```

### 2. Launch the virtual environment

```bash
# to create
~$ conda create -n environment_name python=version anaconda
# to activate
~$ source activate environment_name
# to desactivate
~$ conda deactivate
```

[Managing Environment](https://www.anaconda.com/docs/tools/anaconda-navigator/tutorials/manage-environments)

### 3. Install required libraries

```bash
# conda
conda install conda-forge::numpy
conda install conda-forge::pandas
conda install conda-forge::matplotlib
conda install conda-forge::scikit-learn
conda install conda-forge::jupyter
conda install conda-forge::seaborn
conda install conda-forge::scikit-image
conda install conda-forge::tensorflow
conda install conda-forge::opencv
# pip
pip install numpy
pip install pandas
pip install matplotlib
pip install scikit-learn
pip install seaborn
pip install tensorflow
pip install scikit-image
pip install opencv
```

### 4. Set the dataset path & Hybrid Mount Disk

You can work with Google Colab to access the dataset directly from Google Drive or any preferred cloud storage service.

A hybrid architecture was applied by mounting a virtual drive connected to Google Drive but created locally, allowing continued development within Jupyter Lab on Archcraft Linux distribution (optional).

To configure the virtual drive locally, follow these steps:

#### 1. Install `rclone`

```bash
# update system
sudo pacman -Syyu
# install resource to mount disks
sudo pacman -S rclone
```

#### 2. Configuraction environment remote disk

```bash
rclone config

# to continue it'll ask you questions... step:1
# make a new one? press to create a new mount disk
n # new remote disk
# name> define a name for your virtual disk step:2
name_mount_disk
# Storage> ... Choose a number from below, or type in your own value.
# in my case i go to work with drive
22 # or
drive
# ... client_id> press enter
# ... client_secret> press enter

# scope> ... Choose a number from below, or type in your own value.
1 # to gain full read and write permissions

# root_folder_id> Leave blank normally.
# service_account_file> press enter

# ... Edit advanced config?
n # not advanced configuration
# Use web browser to automatically authenticate rclone with remote? ...
y # for to config auto
# Your browser will automatically open to authenticate with Google
# and allow the required permissions to rclone ...
# ... Configure this as a Shared Drive (Team Drive)?
n # not as a Shared Drive. if you case you want to share press y
# Configuration complete... Keep this "drive_cnn" remote?
y # keep your disk remote
# ... Finally... Edit existing remote
q # to quite
```

#### 3 Create directory mount

We'll create a directory mount for the remote disk at `/home/`

```bash
# create directory
mkdir name_directory_path/

# mount disk
rclone mount name_mount_disk: name_directory_path/ --vfs-cache-mode writes & # name_mount_disk check it on step:2
```

#### 4. dataset path

```bash
/home/username/name_directory_path 
```

Remplace `username` for your real user

## 🤖 Machine Learning workflow

### Visualization & Analysis

## 📁 Project Structure

```bash
```

## 🐛 Troubleshooting

### Automatically Mounted Remote Disk Partition

#### 1. Creat script

```bash
nano /tumor-detection-cnn/rclone_mount.sh
```

```bash
#!/bin/bash

# Make sure the mount directory exists before running the command.
mkdir -p /home/username/cnn

# Mount the unit with rclone
/usr/bin/rclone mount drive_cnn: /home/username/cnn \ # change it for your correct username
--config=/home/username/.config/rclone/rclone.conf \ # change it for your correct username
--allow-other \
--vfs-cache-mode writes \
--dir-cache-time 72h \
--poll-interval 15s \
--umask 000 \
--gid 1000 \
```

```bash
# permissions
chmod +x rclone_mount.sh
```

If you want to working with vim, that is correct. (optional)

#### 2. Create service `systemd`

```bash
sudo nano /etc/systemd/system/rclone-mount.service
```

```bash
Description=Montaje Automático de Google Drive con rclone
Requires=network-online.target
After=network-online.target

[Service]
Type=simple
User=username # change it

ExecStart=/home/username/tumor-detection-cnn/rclone_mount.sh # change it for the correct path
Restart=always

[Install]
WantedBy=multi-user.target
```

In the `rclone_mount.sh` script, when using the `--allow-other` flag, you will need to configure security rules in the following `fuse` script:

```bash
sudo nano /etc/fuse.conf
```

Search the line `#user_allow_other` and delete the `#` and then save changes.

#### 4. Enable & Start service

```bash
systemctl enable rclone-mount.service
systemctl start rclone-mount.service
systemctl status rclone-mount.service
```

Check it the `active (running)`.

## ❓ FAQ

## ✉️ Contact me & Social Media

### 💻 Computer Systems Engineering

Adaptable and flexible in different work environments, with strong critical thinking, solid problem-solving skills, and a collaborative, responsible mindset. My strongest areas are backend development, databases, and machine learning.

If you find this project useful, you can support it by giving a "☆ Star" to the repository.

![Email](https://img.shields.io/badge/Gmail-terrazasjosue0%40gmail.com-EA4335?style=for-the-badge&logo=Gmail&logoColor=white&labelColor=101010)
[![Facebook](https://img.shields.io/badge/Facebook-%40Josu%C3%A9_Terrazas-0866FF?style=for-the-badge&logo=Facebook&logoColor=withe&labelColor=101010)](https://facebook.com/josue.terrazasmendoza)
[![Instagram](https://img.shields.io/badge/Instagram-%40jos__mdz316-E4405F?style=for-the-badge&logo=Instagram&logoColor=white&labelColor=101010)](https://instagram.com/jos_mdz316/)
