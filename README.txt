# All inputs provided by Praveen. & Sruthi

Add your ssh key to https://alioth.debian.org/account/editsshkeys.php

Also join the team mailing list (packaging discussions) and send an
introduction mail.

https://lists.alioth.debian.org/mailman/listinfo/debian-in-workers


and also https://lists.debian.org/debian-dug-in/ (debian India community
list)





Create ~/.ssh/config and add


Host svn.debian.org git.debian.org alioth.debian.org
User scratch-guest

git remote add origin
git+ssh://git.debian.org:/git/debian-in/fonts-sambhota-tsugring.git

git push --all && git push --tags

> Sruthi, have you pushed the file into fonts-sambhota-yigchung? I don't
> see them there, so wondering if i'm looking in the wrong place.

You can do a gbp clone

gbp clone --pristine-tar
git+ssh://git.debian.org:/git/debian-in/fonts-sambhota-yigchung.git

You can also see them on the browser at
https://anonscm.debian.org/cgit/debian-in/fonts-sambhota-yigchung.git


Sruthi
-------

1. Create folder "fonts-sambhota-tsugring-1.1.1"
2. Download http://www.aliadne.net/tibet/Opentype/TibetanTsugRing111.otf
to the folder
3. Create "fonts-sambhota-tsugring-1.1.1.tar.gz" from the downloaded folder
4. Rename "fonts-sambhota-tsugring-1.1.1.tar.gz" to
"fonts-sambhota-tsugring_1.1.1.orig.tar.gz"
5. Clone https://git.fosscommunity.in/Srud/fonts-sambhota-yigchung and copy "debian" folder to 'fonts-sambhota-tsugring-1.1.1"
6. Edit "install" (change 'truetype' to 'opentype'), "changelog", "control" and "copyright" files inside "debian" accordingly.
7. Remove docs file as there is no documentation
8. Run command 'dpkg-buildpackage' on parent folder of "debian" to get .deb file.
9. Move to parent directory (cd ..) and run command gbp import-dsc --pristine-tar fonts-sambhota-tsugring_1.1.1-1.dsc (this will import all packaging files to a git repo. It will create upstream, master and pristine-tar branches.)
10. Push the git repo (all branches and tags) to any git hosting service. Once we decide which team to join, will move everything to alioth.
-- nk
(From Praveen)
Request membership in debian-in group here
https://alioth.debian.org/projects/debian-in

ssh <username>@git.debian.org
cd /git/debian-in
./setup-repository fonts-sambhota-tsugring

See https://wiki.debian.org/Alioth/Git#Accessing_repositories

This is old style project management, we are working on moving to
github-style pull request workflow. We are planning to use Pagure
(https://pagure.io/), it is another Free Software like gitlab already
used by Fedora.
(From Praveen)

    # add git-debian remote
    git remote add origin ssh://<DEBIAN-USERNAME>@git.debian.org/git/debian-in/<REPOSITORY-NAME>.git
    cd to the git repo and 'git push --all && git push tags

-- nk

11.  Run lintian on the debian package to ensure that there are no issue. Note: Ignore Warning: "W: fonts-monlam source: newer-standards-version 3.9.8 (current is 3.9.5)" as this may be due to older dpkg version you're using.
12. To resolve W: fonts-monlam: new-package-should-close-itp-bug,  send Bug request as shown below:

To: submit@bugs.debian.org
Subject: ITP: <font details> Tibetan Fonts

Body:
package: wnpp
Severity: wishlist
Owner: Sruthi Chandran <srud@openmailbox.org>

 Package Name : fonts-ddc-uchen
    Version : 1.0
    Upstream Author : Dzongkha Development Commission
    URL :  http://www.dzongkha.gov.bt/IT/download/fonts/
    License : OFL
    Description :  This is a free Tibetan OpenType Font, created by
    Christopher John Fynn for the Dzongkha Development Commission.


8.1  lintian ../fonts-sambhota-tsugring_1.0-1_i386.changes

8.2 http://lists.alioth.debian.org/pipermail/debian-in-workers/2016-August/002837.html Send email of this format to: debian-in-workers@lists.alioth.debian.org
    <--- Subject: RFS: <package-name>
    Hi,

    I have updated the package fonts-sambhota-tsugring as suggested by FTP masters.

    It is pushed Alioth debian-in repository /git/debian-in/fonts-sambhota-tsugring.git

    Please review and upload.

    Thanks & Regards,
    krishnan
    -->


8.3 Run 'debclean' to cleanup all unwanted files after building

-- nk


Can someone who use Ubuntu request this package be added to Ubuntu? (I
don't use Ubuntu).

Steps here https://wiki.ubuntu.com/SyncRequestProcess

In short,

Install ubuntu-dev-tools package and run

requestsync command.

Package name is fonts-sambhota-yigchung

