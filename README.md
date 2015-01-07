WINDOWS VM FOR IE TESTING
=========================

With Valkyrie, it's pretty easy to build a VM in which to deploy a Drupal site,
push config into code, and share it between developers. However, it's a bit of
a challenge to test these sites on Internet Explorer without first deploying to
a test server, which, in turn, makes tweaking CSS more difficult.

This project aims to solve this by making it simple to launch a local Windows
VM that had access to the site hosted in the Valkyrie VM. It does this by
putting the Windows VM on the same subnet as the Valkyrie VM. After that,
adding entries to the hosts file will allow access via the included IE.

Note that this project uses a Vagrant box prepared by the team at modern.ie.
The medium term plan is to integrate this more fully into Valkyrie, and make
the hacking of the hosts file unnecessary.

The current system is Windows 7 with IE8.


INSTALLATION
------------

To begin, clone the project onto your host machine and launch it:

    $ git clone http://git.poeticsystems.com/valkyrie/windows-vm
    $ cd windows-vm
    $ vagrant up

This will launch a new Virtualbox VM, but it'll take a while the first time you
'vagrant up' since it'll have to download a ~3GB box.


USAGE
-----

The Windows VM will launch with a GUI, so that it can be accessed directly.
Once it's fully booted, the first thing we'll need to do is make the hosts file
writeable.

Open the file browser, and navigate to "My Computer >> C:\ >> Windows >>
System32 >> drivers >> etc", where you should see a 'hosts' file. Right-click
on it, and open Properties. Go to the Security tab, and click on the 'edit'
button. Then select the 'Users' group in the 'Group or user names' box, and
click the 'Allow' checkbox next to 'Full control'.

That should allow you to edit the hosts file. So, close that dialog, and
double-click on the hosts file, and choose to open it with 'notepad'. At the
bottom, add a line like:

    10.42.0.10  valkyrie.local

Save the file, open IE, and type in 'valkyrie.local' in the address field. With
that, you *should* see the Aegir login page. If you're on a Mac, replace
'.local' with '.val'

Assuming the above steps all worked, you can now add additional domains to the
hosts file, all on the same line after the valkyrie.local (or .val).
