<h2> Arch Linux Installation </h2>
<ol>
  <li>I first downloaded the Arch Linux ISO and set up a VM with the memory specifications in the PowerPoint.</li>
  <li>Upon booting up the VM, I pinged ArchLinux.org and confirmed an Internet Connection.</li>
  <li>I also configured the time with "timedatectl set-ntp true".</li>
  <li>I created two partitions with cfdisk (The layout being the same as the one in the PowerPoint).</li>
  <li>After creating these partitions, I used "mkfs.ext4" and "mkfs.fat -F32" to format /dev/sda2 and /dev/sda1 respectively.</li>
  <li>I then mounted both partitions, after having created an efi folder under the mount folder in /dev/sda1.</li>
  <li>Using pacstrap, I then downloaded to /mnt/ the base, linux, and linux-firmware packages.</li>
  <li>I then created a UUID for my disk via "genfstab -U /mnt >> /mnt/etc/fstab".</li>
  <li>arch-chroot /mnt to go to the root directory, to continue downloading packages.</li>
  <li>First, however, I decided to switch to the Chicago local time as they share timezones with us. (ln -sf /usr/share/zoneinfo/America/Chicago /etc/localtime)</li>
  <li>I then connected the localtime to the hardware clock (hwclock --systohc)</li>
  <li>I then decided to get both vim and nano to edit /etc/locale.gen (uncommenting us utf-8) using "pacman --sync vim nano"</li>
  <li>I then used vim to edit etc/hosts and add my info according to the wiki and I created /etc/hostname as well.</li>
  <li>I gave root a password via passwd.</li>
  <li>I also got sudo (pacman --sync sudo) to add sudo users along with netctl (pacman --sync netctl), I also grabbed dialog, wpa_supplicant, and dhcpcd. #This was necessary as I'm using Wi-Fi, I had to look this up.</li> 
  <li>I also enabled wheel users to use sudo by uncommenting the line in visudo, and then I made a user for myself in the wheel group.</li>
  <li>Finally, I install grub and efibootmgr.</li>
  <li>grub-install --target=x86_64 efi --efi-directory=/efi/ --bootloader-id=Arch #This originally failed, which prevented me from booting into Arch, I had to start over from scratch to get it to work</li>
  <li>grub-mkconfig -o /boot/grub/grub.cfg this and the above command sets up grub and lets you boot into Arch using grub.</li>
</ol>

<h2>Booting into Arch</h2>
<ol>
  <li>Within Arch, I try pinging ArchLinux.org again to discover that my network isn't set up yet.</li>
  <li>I cd into /etc/netctl and copy the ethernet-dhcp file from /examples in order to edit it with my info.</li>
  <li>I first uncomment the dhcpcd line and then use ip a to discover my interface name is ens33 and edit ethernet-dhcp again.</li>
  <li>I then enable and start both dhcpcd and wpa_supplicant (I'm on Wi-Fi) and lo and behold, my internet works!</li>
</ol>
  
<h2>Extra Tasks</h2>
<ol>
  <li>Gnome was the GUI I ended up choosing to start off with, to begin, I used sudo pacman --sync xorg xorg-server to download the X Window System</li>
  <li>I then installed Gnome via sudo pacman --sync gnome and then enabled and started it with sudo systemctl start(enable) gdm.service</li>
  <li>This ensures that Gnome will always boot up at startup.</li>
  <li>I also downloaded zsh while I was at it.</li>
  <li>I used passwd to change codi and sal's accounts to the specified password</li>
  <li>I then used sudo passwd -e codi/sal to force the passwords to be changed upon the next login to these accounts.</li>
  <li>I found a neat website: bashrcgenerator.com to edit my terminal color scheme.</li>
  <li>I used gedit to modify both .bashrc and .zhrc to add my alias and such.</li>
</ol>

As you can see in my video, I also installed conky to show off. This is my installation guide in full. 

<a href="DockerProject.md">Project 2</a>
<a href="VPN.md">Project 3</a>
