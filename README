It is recommended to follow the bash commands provided here. You will need ~32 GB disk space totally. While extraction and installation of required services will need extra disk space about ~35 GB. Docker containers need docker-ce and docker-compose to be installed and keep docker service running. You can use local services or a remote server for Docker.

First please download the compressed database file from Mendeley Data link provided below. You can decompress the ZIP database file with UNZIP command or use terminal commands given related section. Another compressed file will be created to extract again. You can use TAR command with parameters 'xvfz' or other extraction method installed in your system. Then you may remove ZIP and TAR.GZ files to keep disk space available. The last step is to clone the repository.  When cloning from github repo is finished, you can run docker-compose with detached mode in the same directory of database folder. Here is the final structure of directory tree:

```
plantenrichment
├── docker-compose.yml
└── db_folder
    ├── arabidopsis_thaliana_core_34_87_11
    ├── aria_log.00000001
    ├── aria_log_control
    ├── brachypodium_distachyon_core_34_87_12
    ├── demo
    ├── glycine_max_core_34_87_1
    ├── hordeum_vulgare_core_34_87_2
    ├── ib_buffer_pool
    ├── ibdata1
    ├── ib_logfile0
    ├── medicago_truncatula_core_34_87_2
    ├── multi-master.info
    ├── mysql
    ├── mysql_upgrade_info
    ├── oryza_sativa_core_34_87_7
    ├── performance_schema
    ├── PlantTEs
    ├── populus_trichocarpa_core_34_87_20
    ├── solanum_lycopersicum_core_34_87_250
    ├── sorghum_bicolor_core_34_87_14
    ├── sys
    ├── triticum_aestivum_core_34_87_3
    └── zea_mays_core_34_87_7
```

If your database folder is in another volume or disk, you can edit docker-compose.yml row #9 with your file path:

```
docker-compose.yml
- ./db_folder:/var/lib/mysql
```

```
docker-compose.yml with your path
- /your_path_to/db_folder/:/var/lib/mysql
```

All bash commands, services and containers are tested under Centos 7.9 and Docker 20.10.16. Despite tested on several linux and other operating system distributions, it is not guaranteed that all containers are compatible with your OS.


```
# install docker-ce docker-compose
# use official website https://docs.docker.com/get-docker/
# use official website https://docs.docker.com/compose/install/

# create a folder to download in and extract PlanTEnrichment database file from mendeley data
mkdir plantenrichment
cd plantenrichment
wget https://md-datasets-cache-zipfiles-prod.s3.eu-west-1.amazonaws.com/4sgh28xpyj-1.zip --no-check-certificate
unzip 4sgh28xpyj-1.zip
# you can remove ZIP file to save space
rm 4sgh28xpyj-1.zip 
mv 4sgh28xpyj-1/db_folder.tar.gz .
rm -rf 4sgh28xpyj-1

tar xvfz db_folder.tar.gz
# you can remove TAR.GZ file to save space
rm db_folder.tar.gz

# clone repo for the latest Dockerfile
git clone https://github.com/alirizaaribas-ibg/plantenrichment_demo.git
mv ./plantenrichment_demo/* .
docker-compose up -d

# open url on any web browser http://127.0.0.1:8880/ or http://{YOUR_SERVER_IP}:8880/

# complete your work and shutdown all containers
docker-compose down
sudo chown $USER:$USER -R db_folder/ # roll back permissions
```
