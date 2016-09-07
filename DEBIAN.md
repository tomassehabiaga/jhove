Debian packaging JHOVE
======================

Vagrant based approach:

**TODO** : Unify documents for Java/Maven machine - see veraPDF packaging dox.

From JHOVE project root we need an SSH session on vagrant box:

vagrant up
vagrant ssh
now to package....

cd /vagrant
vagrant@vagrant:/vagrant$ mh_make -h
Usage: mh_make [option]...
Generate the Debian packaging by reading the information
from the Maven POM.

Options:
-h --help: show this text
-V --version: show the version
-s<svn url> --from-svn=<svn url>: download the source code from
the SVN repository before building the Debian packaging. Use a tagged
branch of the source code, for example
http://svn.apache.org/repos/asf/felix/releases/org.osgi.core-1.2.0/
-p<package> --package=<package>: name of the source package
-b<package> --bin-package=<package>: name of the binary package
-t<true|false> --run-tests=<true|false>: include or not the tests
d<true|false> --javadoc=<true|false>: include or not the javadoc
during the build
-a --ant: use Ant for the packaging instead of Maven
-v --verbose: show more information while running

To have mh_make working properly, you need first to install on your system
as many dependencies for your project as possible. Those dependencies should
also contain the required Maven metadata (POM files and jars in the
/usr/share/maven-repo repository)

Environment variables:
DEBFULLNAME - your full name, e.g. John Doe
DEBEMAIL - your packager email address
DEBLICENSE - the license for the files under the debian/ directory
must be one of GPL2, GPL3, LGPL2.1, Apache-2.0, BSD or any license
short name defined in http://www.debian.org/doc/packaging-manuals/copyright-format/1.0/
vagrant@vagrant:/vagrant$ mh_make -V
Maven Repo Helper version 1.6.9
vagrant@vagrant:/vagrant$ cat >>~/.bashrc <<EOF
DEBFULLNAME="Carl Wilson"
DEBEMAIL="carl@openpreservation.org"
DEBLICENSE="LGPL2.1"
export DEBFULLNAME DEBEMAIL DEBLICENSE
EOF
$ source ~/.bashrc
