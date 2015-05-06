# FAQ #

## What is Inguma? ##

Inguma is an open source penetration testing and vulnerability research toolkit written completely in Python. The environment was originally oriented to attack Oracle-related systems, but it is evolving to a full-fledged penetration tool, so it can be used against many other kinds of systems.

## What does Inguma mean? ##

[Inguma](http://en.wikipedia.org/wiki/Inguma) is the name of a Basque's mythological spirit who kills people in their sleep and also, the one that creates the nightmares.

## Who are the authors? ##

The current project admin is Hugo Teso, a Spanish security enthusiast that actually works in [PenTesting](http://en.wikipedia.org/wiki/Penetration_test). You can contact him at hugo.teso[AT](AT.md)gmail[DOT](DOT.md)com.

The original author of Inguma is Joxean Koret, a Basque software developer who mainly works with Oracle products. You can contact him at joxeankoret[AT](AT.md)yahoo[DOT](DOT.md)es.

## What purpose was it created for? ##

It was created mainly for fun and learning, not for (economic) profit. You can use Inguma for commercial purposes, anyway, as it's licensed under GPLv2. Refer to the GPL version 2 license text for more details.

## It doesn't work for me! ##

Well, it is an alpha version so, it's not a bug, it's a feature. Please, open a bug in the project's issue tracker detailing your problem.

## What are the "discover" and "gather" modules? ##

Discover modules are used to discover hosts or networks using passive and/or active techniques. Gather modules are used to further existing information about a particular host or network. These modules could be said of as being aimed at host reconnaissance.

## It doesn't work "always" in Win32! ##

If you can run [Scapy](http://www.secdev.org/projects/scapy/) without problems in your Windows box, Inguma should work. Inguma has successfully been tested in Win2k, WinXP and Win2k3; but only the console based UI, not the Gtk GUI.

## I want to collaborate! ##

Ok. Send patches and/or ideas to the project members and we will take a look. Help in this open source project (as in any other OS project) is very needed.

## Can I use it for commercial purposes? (About the license) ##

Of course, but you need to comply with the GPLv2 License, which allows the commercial usage of it. In previous versions support for InlineEgg (which is not free) was added, making a module (SIDVault remote root) non-free. As of current version, Inguma is completely free (free as in freedom).

The support for InlineEgg have been dropped starting from version 0.0.6 and a replacement library (PyShellcodeLib) has been added.

## I created a new module for Inguma. Now, what? ##

Send it to me and we will add to the next release.

## Trace module doesn't work! ##

The module "trace" and many other that needs raw socket manipulation requires Inguma to be executed as "root" under Unix or Unix like boxes or as Administrator under Win32 boxes (or a user in the Administrator groups, of course). For additional information on module requirements, please see their individual wiki entries.

## Module smbclient/rpcdump/samrdump doesn't work! ##

You need to download and install Impacket. In the near future it will be replaced with the scapy implementation.

## There is no gui! ##

Inguma comes with 2 GUIs: text-based and PyGtk-based. The most tested one and the only one that will surely work is the text based. The PyGtk one is only the first version of it.

## No module named cx\_Oracle ##

When you try to use any Oracle related module you may find that error. You need to download and install yourself [cx\_Oracle](http://cx-oracle.sourceforge.net/).

## apps11i: cannot concatenate 'str' and 'NoneType' objects ##

The "apps11i" module is a little bit buggy. If you launch the module against a non Oracle E-Business Suite 11i server you will notice that error. Try launching it against one Oracle Financials instance ;)

## I wana hack someone's mailbox/computer! ##

Any new message like this will be published in the web page. I'm a little bit tired ("potrotaraino nago") of such mails.