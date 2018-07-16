whats ruby ruby is the interpreted scripting language for quick and easy object oriented programming it has many features to process text files and to do system management tasks as in perl it is simple straight forward and extensible features of ruby simple syntax normal object oriented features e g class method calls advanced object oriented features e g mix in singleton method operator overloading exception handling iterators and closures garbage collection dynamic loading of object files on some architectures highly portable works on many unix like posix compatible platforms as well as windows macos haiku etc cf https github com ruby ruby blob trunk doc contributing rdoc platform maintainers how to get ruby for a complete list of ways to install ruby including using third party tools like rvm see https www ruby lang org en downloads the trunk of the ruby source tree can be checked out with the following command svn co https svn ruby lang org repos ruby trunk ruby or if you are using git then use the following command git clone https github com ruby ruby git there are some other branches under development try the following command to see the list of branches svn ls https svn ruby lang org repos ruby branches or if you are using git then use the following command git ls remote git github com ruby ruby git ruby home page the url of the ruby home page is https www ruby lang org mailing list there is a mailing list to talk about ruby to subscribe to this list please send the following phrase subscribe in the mail body not subject to the address ruby talk request ruby lang org how to compile and install this is what you need to do to compile and install ruby if you want to use microsoft visual c to compile ruby read win32 readme win32 instead of this document if configure does not exist or is older than configure ac run autoconf to re generate configure run configure which will generate config h and makefile some c compiler flags may be added by default depending on your environment specify optflags and warnflags as necessary to override them edit defines h if you need usually this step will not be needed remove comment mark before the module names from ext setup or add module names if not present if you want to link modules statically if you dont want to compile non static extension modules probably on architectures which do not allow dynamic loading remove comment mark from the line option nodynamic in ext setup usually this step will not be needed run make on mac set ruby codesign environment variable with a signing identity it uses the identity to sign ruby binary see also codesign 1 optionally run make check to check whether the compiled ruby interpreter works well if you see the message check succeeded your ruby works as it should hopefully optionally run make update gems and make extract gems if you want to install bundled gems run make update gems and make extract gems before running make install run make install this command will create the following directories and install files into them destdir prefix bin destdir prefix include ruby major minor teeny destdir prefix include ruby major minor teeny platform destdir prefix lib destdir prefix lib ruby destdir prefix lib ruby major minor teeny destdir prefix lib ruby major minor teeny platform destdir prefix lib ruby site ruby destdir prefix lib ruby site ruby major minor teeny destdir prefix lib ruby site ruby major minor teeny platform destdir prefix lib ruby vendor ruby destdir prefix lib ruby vendor ruby major minor teeny destdir prefix lib ruby vendor ruby major minor teeny platform destdir prefix lib ruby gems major minor teeny destdir prefix share man man1 destdir prefix share ri major minor teeny system if rubys api version is x y z the major is x the minor is y and the teeny is z note teeny of the api version may be different from one of rubys program version you may have to be a super user to install ruby if you fail to compile ruby please send the detailed error report with the error log and machine os type to help others some extension libraries may not get compiled because of lack of necessary external libraries and or headers then you will need to run make distclean ext to remove old configuration after installing them in such case copying see the file copying feedback questions about the ruby language can be asked on the ruby talk mailing list https www ruby lang org en community mailing lists or on websites like https stackoverflow com bug reports should be filed at https bugs ruby lang org read howtoreport for more information contributing see the file contributing md the author ruby was originally designed and developed by yukihiro matsumoto matz in 1995 matz ruby lang org