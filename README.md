# rsync-homedir-excludes

#Usage:

    # download to `/var/tmp/ignorelist`
    wget https://raw.githubusercontent.com/rubo77/rsync-homedir-excludes/master/rsync-homedir-excludes.txt -O /var/tmp/ignorelist
    # or copy to `/var/tmp/ignorelist`
    cp ./rsync-homedir-excludes.txt /var/tmp/ignorelist

    # edit the file /var/tmp/ignorelist to your needs
    nano /var/tmp/ignorelist

    # define a Backup directory, for example:
    BACKUPDIR=/media/$USER/linuxbackup/home/$USER/
    BACKUPDIR=/media/workspace/home/$USER/

    # first append the “-n” parameter rsync will simulate the operation. you should use this before you start:
    rsync -naP --exclude-from=/var/tmp/ignorelist /home/$USER/ $BACKUPDIR
		
		#check for permission denied errors in your homedir:
		rsync -naP --exclude-from=/var/tmp/ignorelist /home/$USER/ $BACKUPDIR|grep denied
		
		# if it is all fine, start your backup with
    rsync -aP --exclude-from=/var/tmp/ignorelist /home/$USER/ $BACKUPDIR

At the start, there is a section with directories, probably not worth a backup. Uncomment those lines to exclude them as well.

If you 