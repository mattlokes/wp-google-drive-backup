# Wordpress Google Drive Backup Script
A cronable Bash Script to backup multiple wordpress websites to google drive.

## Requires:
1. gdrive  (https://github.com/prasmussen/gdrive)

## Steps to Setup:
1. Find Google Drive Directory Parent ID to backup to and set **BACKUP_DIR_GDRIVE_ID** below

   `gdrive list -m 200000 | grep <DIRECTORY_NAME> | awk '{print $1}'`
   
2. Choose a Directory for script to perform in and set **SCRATCH_DIR_PATH** below, all files except logs will be removed at the end
   
3. Choose the maximum number of backups to leave on Google Drive set **MAX_BACKUP_NUM** below, oldest backup will be deleted after maximum reached.
   
4. Set **SITE_NAMES** array to contain all websites to be backed up, this site name must be the database name and part of directory name where the site's root /var/www/ lives.
   
5. Set **MYSQLUSER** & **MYSQLPASS** as your mySQL user credentials.
6. Add to Crontab: 

 e.g `0 4 * * 1 <PATH_TO_SCRIPT>/wp_backup_gdrive`
7. Change Permission to execute only, to stop password being read:

`chmod 111 wp_backup_gdrive`

8. Profit!
