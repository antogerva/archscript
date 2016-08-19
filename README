```bash
#!/bin/sh

# Dernière édition: 11 mars 2008
# VersionID: archSCRIPT v 0.2 (Ogry)
# Info supplémentaire: Systhème de base seulement

# archSCRIPT v0.1 - Un installateur automatique d'Arch Linux (version loins d'être terminé)
# Copyright (C) 2008   Antoine Gervais  (antogerva[a]gmail.com)
# 
#
##
# Tout d'abord, ceci est un logiciel libre et de ce fait vous pouvez
# le configurer comme cela vous chante en accord avec les therme de la
# GNU, General Public License, tel que stipuler par la troisième version
# de la Free Software Foundation ou encore a une version à venir. Vous
# devrez avoir avoir une copie de la GNU General Public License qui
# vient avec ce programme, si ce n'est pas vous pouvez l'obtenir
# à cette page <http://www.gnu.org/licenses/>.
##
#
########
# Note : Si ce programme est distribué sous license GPL... ce n'est pas
# pour rien ! Je vous recommande grandement de regarder attentivement le
# code source de ce script et d'y apporter vos propre
# config/personalisation ;-)
#
# Ce sript est à la base optimiser pour les canadiens français, mais vous
# pouvez faire une configuration propre à vous et le redistribuer sous
# un autre nom en indiquant qu'il est basé sur celui-ci.
# 
########---------------------------------------------------------------########








########---------------------------------------------------------------########


# -- Index --

#  Configuration du vrai pacman.conf..................................ligne 
#  Configurartion du fstab............................................ligne
#  Configuration du menu.lst (de grub)................................ligne
#  Configuration du rc.conf


########---------------------------------------------------------------########

#
#
#
#
#
#

############
#Bonjour à vous, cher utilisateur de ce script,
#
# Donc, si vous lisez présentement ce texte, je peux lire en vous à peu près trois
# de personnes, soit vous êtes le fameux guru du forums, qui ne rate jamais une
# une occasions de s'instruire... ou vous encore un de ces nooby qui à poser une 
# question stupide l'autre.... ou encre un mélange des deux ;D
#
# Bref, quelques soit les raisons d'utilisation de ce scripte, sachez que chaque
# partie du fichier est largement documenter, pour vous donner au moins une idée
# de ce que fait tel commande.
#
# D'ailleur, si vous êtes nouveau depuis peu, dans le monde de Linux, il se peut
# que vous trouvez cette méthode d'installaion par script un peu primitive...
# mais détrompez-vous, non seulement vous obtiendrez un systhème aux
# moins 4 fois plus rapide qu'Ubuntu ainsi que grandement simiaire à celle de
# Gentoo, mais en plus, vous aurez un très bon avant goût de comment fonctionne
# un systhème Linux et dite vous aussi, que dans l'univers de l'open-source ça
# serait stupide de faire uniquement du clique bouton, alors que vous avez un 
# merveilleux a étudier devant vos yeux ;-)
#
#
###########


# J'imagine que vos partitions et tout et tout son déjà aménager pour acceuillir
# votre nouveau systhème

# cfdisk

function SETTINGS()
{
  

    # c'est sur cette variable que tout votre systhème est installer... donc soyez vigilant ;)
    SOURCELOCATION=/mnt/arch


    # Partition info

    SWAPPART=/dev/hda5

    FilesSysthem=/dev/hda6
TypeFilesSysthem=reiseirfs

    Home=$FilesSysthem
TypeHOME=$TypeFilesSysthem

########---Experts---#######
#TypeBOOT=
#
#    USR=$FilesSysthem
#TypeUSR=
#
#    PROC=$FilesSysthem
#TypePROC=
#
#    DEV=$FilesSysthem
#TypeDEV=  
#
#    SYS=$FilesSysthem
#TypeSYS=
#
#    BIN=$FilesSysthem
#TypeBIN=
#
#    SBIN=$FilesSy
#TypeSBIN=
#
#    TMP=$FilesSysthem
#TypeTMP=
#
#    OPT=$FilesSysthem
#TypeOPT=
#
#    VAR=$FilesSysthem
#TypeVAR=
#
#    MEDIA=$FilesSysthem
#TypeMEDIA=
#
#    MNT=
#TypeMNT=
#
###########################

                 ###=--=######=--=###         ##
                 # !Option du Grub! #       ####
                 #  --------------  #     ######
##################                  #  ####################
                   GRUB_ROOT=hd0,9  ###########################
                   GRUB_SETUP=hd0   #  #############################
##################                  #     ######  
                 #                  #       ####
                 ###=--=######=--=###         ##

 # Information Général


  ScriptName=archSCRIPT-0.1.sh




  # Localisation info
  ZONEINFO=America/Montreal
  LOCALE=fr_CA                                      
  HARDWARECLOCK=localtime                                               
  TIMEZONE=America/Montreal                                          
  KEYMAP=cf
  CONSOLEFONT=lat9w-16
  CONSOLEMAP=8859-15
  UTC=-4

  # Networking info
  HOSTNAME=rorqual
  DOMAINNAME=
  FQDN=
  IPPREFIX=24
  IPADRESS=192.168.1.169
  GATEWAY=192.168.1.1
  DNS1=192.168.1.1
  DNS2=192.168.1.1
  IPBROADCAST=192.168.1.255


  # À venir, votre propre configuration du kernel
  #
  KERNELCONFIGMIRROR=http://www.mywebsite/kernel/.config



############---Configuration de vos Packages---##############
#
#Il vous suffit simplement de décommenter les lignes qui vous
#intéresse, pour qu'elle soivent installer.


  WindowsManagerPackage=""

  CompizPackage=""
  
  GnomePackage=""

  KdemodPackage=""

  Xfce4Package=""

  PackagePerso=""

}
SETTINGS

# ici j'appèlle le nom de la variale le execPATH
# car c'est là que l'on se trouve au tout, quand on démarre le script
# en présumant que vous êtes au même endroit quand le script à son
# exécution... ça sera un truc qu'il faudra que j'arrange pour qu'on
# puisse le démarrer de n'importe où.

execPATH=$(pwd)

# Maintenant notre systhème temporaire(pacman) sera mit sur /tmp
# le temps qu'on installe nos là base de arch ...

mkdir -pv "$SOURCELOCATION/tmp" "$SOURCELOCATION/etc"
cd "$SOURCELOCATION/tmp"
echo "bien, pour commencer on va installer quelques fichier temporaire dans:" ; pwd 

wget  ftp://ftp.archlinux.org/core/os/i686/pacman-3.*
tar zxvf pacman*.pkg.tar.gz
sed -i 's| /etc/pacman.d|'"$SOURCELOCATION"'/tmp/etc/pacman.d|' "$SOURCELOCATION"/tmp/etc/pacman.conf


##
## Inutile pour le moment de disposer de la liste des packages de base
##
#wget ftp://ftp.archlinux.org/core/os/i686/packages.txt
#grep '^base/' packages.txt | sed -r 's|^base/(.*)-[^-]*-[^-]*-[^-]*\.pkg.tar.*|\1|' | xargs echo -n "" > basepackages.txt
#programme_de_base=$(cat basepackages.txt)
##




pacman()
{
 (echo "# /etc/pacman.conf"                                                        &&
  echo "#"                                                                         &&
  echo "# See the pacman manpage for option directives"                            &&
  echo "#"                                                                         &&
  echo "# GENERAL OPTIONS"                                                         &&
  echo ""                                                                          &&
  echo "[options]"                                                                 &&
  echo "# The following paths are commented out with their default values listed." &&
  echo "# If you wish to use different paths, uncomment and update the paths."     &&
  echo ""                                                                          &&
  echo "#RootDir     = /"                                                          &&
  echo "DBPath      = $SOURCELOCATION/var/lib/pacman/"                             &&
  echo "CacheDir    = $SOURCELOCATION/var/cache/pacman/pkg/"                       &&
  echo "LogFile     = $SOURCELOCATION/var/log/pacman.log"                          &&
  echo "HoldPkg     = pacman glibc"                                                &&
  echo "#XferCommand = /usr/bin/wget --passive-ftp -c -O %o %u"                    &&
  echo ""                                                                          &&
  echo ""                                                                          &&
  echo "#"                                                                         &&
  echo "# REPOSITORIES"                                                            &&
  echo "# - can be defined here or included from another file"                     &&
  echo "# - pacman will search repositories in the order defined here"             &&
  echo "# - local/custom mirrors can be added here or in separate files"           &&
  echo "# - repositories listed first will take precedence when packages"          &&
  echo "#   have identical names, regardless of version"                           &&
  echo ""                                                                          &&
  echo "# Repository entries are of the format:"                                   &&
  echo "#       [repo-name]"                                                       &&
  echo "#       Server = ServerName"                                               &&
  echo "#       Include = IncludePath"                                             &&
  echo ""                                                                          &&
  echo "# The header [repo-name] is crucial - it must be present and"              &&
  echo "# uncommented to enable the repo."                                         &&
  echo ""                                                                          &&
  echo ""                                                                          &&
  echo "########################"                                                  &&
  echo ""                                                                          &&
  echo "[current]"                                                                 &&
  echo "# Add your preferred servers here, they will be used first"                &&
  echo "#Include = /etc/pacman.d/current"                                          &&
  echo "Server = ftp://ftp.archlinux.org/current/os/i686"                          &&
  echo ""                                                                          &&
  echo ""                                                                          &&
  echo "[core]"                                                                    &&
  echo "# Add your preferred servers here, they will be used first"                &&
  echo "Server = ftp://ftp.archlinux.org/core/os/i686"                             &&
  echo ""                                                                          &&
  echo "[extra]"                                                                   &&
  echo "# Add your preferred servers here, they will be used first"                &&
  echo "#Include = /etc/pacman.d/extra"                                            &&
  echo "Server = ftp://ftp.archlinux.org/extra/os/i686"                            &&
  echo ""                                                                          &&
  echo ""                                                                          &&
  echo "[community]"                                                               &&
  echo "# Add your preferred servers here, they will be used first"                &&
  echo "#Include = /etc/pacman.d/community"                                        &&
  echo "Server = ftp://ftp.archlinux.org/community/os/i686"                        &&
  echo ""                                                                          &&
  echo ""                                                                          &&
  echo "[kdemod]"                                                                  &&
  echo "Server = http://kdemod.ath.cx/repo/current/i686"                           &&
  echo ""                                                                          &&
  echo ""                                                                          &&
  echo "[archlinuxfr]"                                                             &&
  echo "Server = http://repo.archlinux.fr/i686"                                    &&
  echo ""                                                                          &&
  echo ""                                                                          &&
  echo "#[unstable]"                                                               &&
  echo "# Add your preferred servers here, they will be used first"                &&
  echo "#Include = /etc/pacman.d/unstable"                                         &&
  echo "# An example of a custom package repository.  See the pacman manpage for"  &&
  echo "# tips on creating your own repositories."                                 &&
  echo "#[custom]"                                                                 &&
  echo "#Server = file:///home/custompkgs"                                         &&
  echo ""                                                                          &&
  echo "# End /etc/pacman.conf"                                                    &&
  echo ""                                                                          &&
  echo "") > "$SOURCELOCATION/tmp/etc/pacman.conf"
}
pacman




rconfig()
{
 (echo "# /etc/rc.conf - Main Configuration for Arch Linux"                        &&
  echo ""                                                                          &&
  echo ""                                                                          &&
  echo ""                                                                          &&
  echo ""                                                                          &&
  echo "# -----------------------------------------------------------------------" &&
  echo "# LOCALIZATION"                                                            &&
  echo "# -----------------------------------------------------------------------" &&
  echo ""                                                                          &&
  echo ""                                                                          &&
  echo ""                                                                          &&
  echo "# LOCALE: available languages can be listed with the "locale -a" command"  &&
  echo "# HARDWARECLOCK: set to "UTC" or "localtime""                              &&
  echo "# TIMEZONE: timezones are found in /usr/share/zoneinfo"                    &&
  echo "# KEYMAP: keymaps are found in /usr/share/kbd/keymaps"                     &&
  echo "# CONSOLEFONT: found in /usr/share/kbd/consolefonts"                       &&
  echo "# CONSOLEMAP: found in /usr/share/kbd/consoletrans"                        &&
  echo "# USECOLOR: use ANSI color sequences in startup messages"                  &&
  echo ""                                                                          &&
  echo ""                                                                          &&
  echo ""                                                                          &&
  echo "LOCALE="$LOCALE.utf8""                                                     &&
  echo "HARDWARECLOCK="$HARDWARECLOCK""                                            &&
  echo "TIMEZONE="$TIMEZONE""                                                      &&
  echo "KEYMAP="$KEYMAP""                                                          &&
  echo "CONSOLEFONT="lat9w-16""                                                    &&
  echo "CONSOLEMAP="8859-15""                                                      &&
  echo "USECOLOR="yes""                                                            &&
  echo ""                                                                          &&
  echo "# -----------------------------------------------------------------------" &&
  echo "# HARDWARE"                                                                &&
  echo "# -----------------------------------------------------------------------" &&
  echo ""                                                                          &&
  echo ""                                                                          &&
  echo "# Module Blacklist - modules in this list will never be loaded by udev"    &&
  echo ""                                                                          &&
  echo "MOD_AUTOLOAD="yes""                                                        &&
  echo "# Module Blacklist - modules in this list will never be loaded by udev"    &&
  echo "# Example: MOD_BLACKLIST=(fglrx)"                                          &&
  echo "MOD_BLACKLIST=()"                                                          &&
  echo "# Modules to load at boot-up (in this order)"                              &&
  echo "# - prefix a module with a ! to blacklist it"                              &&
  echo "# Example: MODULES=(fuse reiserfs ipw2200  battery fan svgalib radeon)"    &&
  echo "MODULES=()"                                                                &&
  echo ""                                                                          &&
  echo ""                                                                          &&
  echo "# Scan for LVM volume groups at startup, required if you use LVM"          &&
  echo "USELVM="no""                                                               &&
  echo ""                                                                          &&
  echo "# -----------------------------------------------------------------------" &&
  echo "# NETWORKING"                                                              &&
  echo "# -----------------------------------------------------------------------" &&
  echo ""                                                                          &&
  echo ""                                                                          &&
  echo "HOSTNAME="rorqual""                                                        &&
  echo "# Use "ifconfig -a" or "ls /sys/class/net/" to see all available"          &&
  echo "# interfaces."                                                             &&
  echo ""                                                                          &&
  echo "# Interfaces to start at boot-up (in this order)"                          &&
  echo "# Declare each interface then list in INTERFACES"                          &&
  echo ""                                                                          &&
  echo "#   - prefix an entry in INTERFACES with a ! to disable it"                &&
  echo "#   - no hyphens in your interface names - Bash doesn't like it"           &&
  echo ""                                                                          &&
  echo "# Note: to use DHCP, set your interface to be "dhcp" (eth0="dhcp")"        &&
  echo "# Don't use this for wireless interfaces, see network profiles below"      &&
  echo ""                                                                          &&
  echo "eth0="dhcp""                                                               &&
  echo "INTERFACES=(eth0 eth1 !wlan0)"                                             &&
  echo "lo="lo 127.0.0.1""                                                         &&
  echo ""                                                                          &&
  echo ""                                                                          &&
  echo "#eth0="eth0 192.168.0.2 netmask 255.255.255.0 broadcast 192.168.0.255""    &&
  echo "#wlan0="dhcp""                                                             &&
  echo "#wlan_wlan0="wlan0 mode auto key s:xxxxxxxxxxxxxxxxxxx essid myessid""     &&
  echo "#eth1="dhcp""                                                              &&
  echo ""                                                                          &&
  echo ""                                                                          &&
  echo ""                                                                          &&
  echo "# Routes to start at boot-up (in this order)"                              &&
  echo "# Declare each route then list in ROUTES"                                  &&
  echo "# - prefix an entry in ROUTES with a ! to disable it"                      &&
  echo "#"                                                                         &&
  echo "# gateway="default gw 192.168.0.1""                                        &&
  echo "# ROUTES=(!gateway)"                                                       &&
  echo ""                                                                          &&
  echo "# Enable these network profiles at boot-up.  These are only useful"        &&
  echo "# if you happen to need multiple network configurations(ie, laptop users)" &&
  echo "# - set to menu to present a menu during boot-up(dialog package required)" &&
  echo "# - prefix an entry with a ! to disable it"                                &&
  echo ""                                                                          &&
  echo "# Network profiles are found in /etc/network-profiles"                     &&
  echo ""                                                                          &&
  echo "# NET_PROFILES=(config_wpa maison)"                                        &&
  echo ""                                                                          &&
  echo ""                                                                          &&
  echo ""                                                                          &&
  echo "# -----------------------------------------------------------------------" &&
  echo "# DAEMONS"                                                                 &&
  echo "# -----------------------------------------------------------------------" &&
  echo ""                                                                          &&
  echo "# Daemons to start at boot-up (in this order)"                             &&
  echo "#   - prefix a daemon with a ! to disable it"                              &&
  echo "#   - prefix a daemon with a @ to start it up in the background"           &&
  echo ""                                                                          &&
  echo "DAEMONS=(@syslog-ng @networkdbusgpm @crond @hal @alsa @wicd fam esd stbd)" &&
  echo ""                                                                          &&
  echo ""                                                                          &&
  echo "# End of file"                                                             &&
  echo ""                                                                          &&
  echo "") > $SOURCELOCATION/etc/rc.conf

}


mkdir -pv "$SOURCELOCATION/var/lib/pacman/"
mkdir -pv "$SOURCELOCATION/root"
mkdir -pv "$SOURCELOCATION/boot/grub"


$SOURCELOCATION/tmp/usr/bin/pacman.static --dbpath "$SOURCELOCATION/var/lib/pacman/" --root "$SOURCELOCATION" --config "$SOURCELOCATION/tmp/etc/pacman.conf" --noconfirm -Sy base  ### $programme_de_base <== (intutille pour le moment)


cat /etc/resolv.conf > "$SOURCELOCATION"/etc/resolv.conf



source /etc/profile



function fstabconfig()
{
 (echo "# Begin /etc/fstab" &&
  echo "                                                                              " &&
  echo "# <file system>  <mount-point>  <type>   <options>             <dump>  <pass> " &&
  echo "#                                                                             " &&
  echo "$SWAPPART        swap           swap     defaults              0       0      " &&
  echo "$FilesSysthem    /              reiserfs defaults              0       1      " && 
  echo "$Home            /home          ext3     defaults              0       0      " &&
  echo "#                                                                             " && 
  echo "#$Boot           /boot          ext2     defaults              0       0      " &&
  echo "#                                                                             " &&
  echo "#none            /proc          proc     defaults              0       0      " &&
  echo "#none            /sys           sysfs    defaults              0       0      " &&
  echo "#                                                                             " &&
  echo "#                                                                             " &&
  echo "# Grâce à /dev/pts on facillite pas mal plus la vie à Xterm & Cie...          " &&
  echo "#                                                                             " &&
  echo "none            /dev/pts        devpts   gid=5,mode=666        0       0      " &&
  echo "/dev/cdrom      /mnt/cdrom      iso9660  ro,user,noauto,unhide 0       0      " &&
  echo "/dev/dvd        /mnt/dvd        udf      ro,user,noauto,unhide 0       0      " &&
  echo "#                                                                             " && 
  echo "#                                                                             " && 
  echo "# End /etc/fstab") > $SOURCELOCATION/etc/fstab
}

function grubconfig()
{
 (echo "# Begin /boot/grub/menu.lst"                                                &&
  echo ""                                                                           &&
  echo "# numlockx ## à vérifier si c'est bien cela pas sur)"                       &&
  echo ""                                                                           &&
  echo "# By default boot the first menu entry."                                    &&
  echo "default 0"                                                                  &&
  echo ""                                                                           &&
  echo "# Allow 30 seconds before booting the default."                             &&
  echo "timeout 10"                                                                 &&
  echo ""                                                                           &&
  echo "# Use prettier colors."                                                     &&
  echo "color light-blue/black light-cyan/blue"                                     &&
  echo ""                                                                           &&
  echo "# The first entry is for LFS."                                              &&
  echo "title LFS 6.3"                                                              &&
  echo "root ($GRUB_ROOT)"                                                          &&
  echo "kernel  /boot/vmlinuz26 root=/dev/$FilesSysthem vga=790 ro"                 &&
  echo "initrd /boot/kernel26.img"                                                  &&
  echo ""                                                                           &&
  echo ""                                                                           &&
  echo ""                                                                           &&
  echo ""                                                                           &&
  echo ""                                                                           &&
  echo ""                                                                           &&
  echo "") > $SOURCELOCATION/boot/grub/menu.lst
}

# Avec les commandes qui suivent, notre rc.conf, fstab et notre menu.lst vont se créer.
rconfig
fstabconfig
grubconfig


# nouveau /etc/pacman.conf ==> configurer le comme vous le vouler :)

cat > $SOURCELOCATION/etc/pacman.conf << "EOF"
# /etc/pacman.conf
# ++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
# See the pacman manpage for option directives

#
# GENERAL OPTIONS
#
[options]
# The following paths are commented out with their default values listed.
# If you wish to use different paths, uncomment and update the paths.
#RootDir     = /
#DBPath      = /var/lib/pacman/
#CacheDir    = /var/cache/pacman/pkg/
#LogFile     = /var/log/pacman.log
HoldPkg     = pacman glibc
#XferCommand = /usr/bin/wget --passive-ftp -c -O %o %u

#
# REPOSITORIES
#   - can be defined here or included from another file
#   - pacman will search repositories in the order defined here
#   - local/custom mirrors can be added here or in separate files
#   - repositories listed first will take precedence when packages
#     have identical names, regardless of version number
#
# Repository entries are of the format:
#       [repo-name]
#       Server = ServerName
#       Include = IncludePath
#
# The header [repo-name] is crucial - it must be present and
# uncommented to enable the repo.
#

[current]
# Add your preferred servers here, they will be used first
#Include = /etc/pacman.d/current
Server = ftp://ftp.archlinux.org/current/os/i686

[core]
Server = ftp://ftp.archlinux.org/core/os/i686


[extra]
# Add your preferred servers here, they will be used first
#Include = /etc/pacman.d/extra
Server = ftp://ftp.archlinux.org/extra/os/i686

[community]
# Add your preferred servers here, they will be used first
#Include = /etc/pacman.d/community
Server = ftp://ftp.archlinux.org/community/os/i686

[kdemod]
Server = http://kdemod.ath.cx/repo/current/i686

[archlinuxfr]
Server = http://repo.archlinux.fr/i686

[svn]
Server = http://cvs.archlinux.org 


#[compiz-fusion]
#Server = http://arch.nesl247.org/compiz-fusion/i686

#[unstable]
# Add your preferred servers here, they will be used first
#Include = /etc/pacman.d/unstable

# An example of a custom package repository.  See the pacman manpage for
# tips on creating your own repositories.
#[custom]
#Server = file:///home/custompkgs

# ++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
# Fin du /etc/pacman.conf
EOF

# on va modifier notre locale.gen

sed -e "s/#$LOCALE/$LOCALE/" $SOURCELOCATION/etc/locale.gen > $SOURCELOCATION/etc/locale.gen2
mv $SOURCELOCATION/etc/locale.gen $SOURCELOCATION/etc/locale.gen.old
mv $SOURCELOCATION/etc/locale.gen2 $SOURCELOCATION/etc/locale.gen


# ici on doit copier le script dans notre nouveau systhème, pour qu'il puisse continuer une fois en chroot
cp $execPATH/$ScriptName $SOURCELOCATION/root/$ScriptName


# la voie semble être libre... chrootons!

chroot "$SOURCELOCATION" \
/bin/bash --login +h /root/$ScriptName grubinstall # le archSCRIPT sera ainsi redémarrer à la fonction grubinstall

## On va mettre grub sur le mbr
function grubinstall()
{
grub --batch <<EOF
root ($GRUB_ROOT) 
setup ($GRUB_SETUP)
quit
EOF
}

locale-gen

pacman -S yaourt


# clochette :)

echo -e "\a"
echo -e "\a"
echo -e "\a"
echo -e "\a"
echo -e "\a"

```
