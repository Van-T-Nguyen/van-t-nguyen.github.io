## Welcome to GitHub Pages

You can use the [editor on GitHub](https://github.com/Van-T-Nguyen/van-t-nguyen.github.io/edit/main/index.md) to maintain and preview the content for your website in Markdown files.

Whenever you commit to this repository, GitHub Pages will run [Jekyll](https://jekyllrb.com/) to rebuild the pages in your site, from the content in your Markdown files.

### Markdown

Markdown is a lightweight and easy-to-use syntax for styling your writing. It includes conventions for

```markdown
Syntax highlighted code block

# Header 1
## Header 2
### Header 3

- Bulleted
- List

1. Numbered
2. List

**Bold** and _Italic_ and `Code` text

[Link](url) and ![Image](src)
```

For more details see [GitHub Flavored Markdown](https://guides.github.com/features/mastering-markdown/).

### Jekyll Themes

Your Pages site will use the layout and styles from the Jekyll theme you have selected in your [repository settings](https://github.com/Van-T-Nguyen/van-t-nguyen.github.io/settings/pages). The name of this theme is saved in the Jekyll `_config.yml` configuration file.

### Support or Contact

Having trouble with Pages? Check out our [documentation](https://docs.github.com/categories/github-pages-basics/) or [contact support](https://support.github.com/contact) and we’ll help you sort it out.

```Header 1``` #Header 1 **Header 1**
I first downloaded the Arch Linux ISO and set up a VM with the memory specifications in the PowerPoint.
Upon booting up the VM, I pinged ArchLinux.org and confirmed an Internet Connection.
I also configured the time with "timedatectl set-ntp true".
I created two partitions with cfdisk (The layout being the same as the one in the PowerPoint).
After creating these partitions, I used "mkfs.ext4" and "mkfs.fat -F32" to format /dev/sda2 and /dev/sda1 respectively.
I then mounted both partitions, after having created an efi folder under the mount folder in /dev/sda1.
Using pacstrap, I then downloaded to /mnt/ the base, linux, and linux-firmware packages.
I then created a UUID for my disk via "genfstab -U /mnt >> /mnt/etc/fstab".
arch-chroot /mnt to go to the root directory, to continue downloading packages.
First, however, I decided to switch to the Chicago local time as they share timezones with us.
(ln -sf /usr/share/zoneinfo/America/Chicago /etc/localtime)
I then connected the localtime to the hardware clock (hwclock --systohc)
I then decided to get both vim and nano to edit /etc/locale.gen (uncommenting us utf-8) using "pacman -sync vim nano"
I then used vim to edit etc/hosts and add my info according to the wiki and I created /etc/hostname as well.
I gave root a password via passwd.
I also got sudo (pacman -sync sudo) to add sudo users along with netctl (pacman -Syc netctl), I also grabbed dialog, wpa_supplicant, and dhcpcd.
I also enabled wheel users to use sudo by uncommenting the line in visudo, and then I made a user for myself in the wheel group.
Finally, I install grub and efibootmgr.
grub-install --target=x86_64 efi --efi-directory=/efi/ --bootloader-id=Arch #This originally failed, which prevented me from booting into Arch
#I had to start over from scratch to get it to work
grub-mkconfig -o /boot/grub/grub.cfg

With all this done, I finally remove the iso from my VM and boot into Arch successfully.

Within Arch, I try pinging ArchLinux.org again to discover that my network isn't set up yet. 
I cd into /etc/netctl and copy the ethernet-dhcp file from /examples in order to edit it with my info.
I first uncomment the dhcpcd line and then use ip a to discover my interface name is ens33 and edit ethernet-dhcp again.
I then enable and start both dhcpcd and wpa_supplicant (I'm on Wi-Fi) and lo and behold, my internet works!

Now begins the supplemental tasks...

Gnome was the GUI I ended up choosing to start off with, to begin, I used sudo pacman --sync xorg xorg-server to download the X Window System
I then installed Gnome via sudo pacman --sync gnome and then enabled and started it with sudo systemctl start(enable) gdm.service
This ensures that Gnome will always boot up at startup.
I also downloaded zsh while I was at it.
I used passwd to change codi and sal's accounts to the specified password
I then used sudo passwd -e codi/sal to force the passwords to be changed upon the next login to these accounts.
I found a neat website: bashrcgenerator.com to edit my terminal color scheme.
I used gedit to modify both .bashrc and .zhrc to add my alias and such.

ssh -p53997 van@129.244.245.21
