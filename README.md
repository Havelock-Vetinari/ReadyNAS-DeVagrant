# ReadyNAS-DeVagrant
Debian Wheezy based vagrant with chroot for ReadyNAS 6 x86 SDK

##Requires
VirtualBox Guest Addition to mount shared folder:

     vagrant plugin install vagrant-vbguest #install vagrant plugin which takes care of this

##Usage

     #put code into 'src' dir
     vagrant up
     vagrant ssh
     schroot -c r6
     cd /mnt/src
     #make #build #work
     
