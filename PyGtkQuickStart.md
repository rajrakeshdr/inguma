# Inguma GUI Quick start #

This documents aims to provide a **fast introduction to Inguma PyGtk GUI** and guide new users on the initial fast steps to perform a basic test agains one target. It will **not be a complete guide** of all Inguma's features.

First we need to **run ginguma.py** as _root or administrator_ user so all modules could be launched.

```
user@laptop:~/Inguma$ sudo ./ginguma.py 
[sudo] password for user: 
Checking: 
	GTK UI dependencies... 	OK 
WARNING: No route found for IPv6 destination :: (no default route?) 
	Scapy... 		OK 
	Network conectivity... 	OK 
	GtkSourceView2... 	OK 
	VTE Terminal... 	OK 
	/usr/bin/nmap... 	OK 
	/pentest/web/w3af/w3af_console... 	OK 
Starting Inguma, running on: 
  Python version: 
    2.6.4 (r264:75706, Dec  7 2009, 18:45:15) 
    [GCC 4.4.1] 
  GTK version: 2.18.3 
  PyGTK version: 2.16.0 
```

Once the aplication finishes loading there are **two main paths to follow** in order to start working:

  * **Manually launch the desired modules** one by one: discovers->ipaddr, dicovers-> tcptrace, etc...
  * Use the **“Add Target” button** so the first non intrusive probes will be done automatically.

We will use the second one. So press the **“Add Target”** button and a new dialog will appear. Select **“domain”**, fill the text input with the name of your target like _“testphp.acunetix.com”_, don't select **“Use Nmap”** as we want to use Inguma's own modules, and press **“Accept”**.

<a href='http://wiki.inguma.googlecode.com/hg/img/Step-1.png'><img width='500' src='http://wiki.inguma.googlecode.com/hg/img/Step-1.png' /></a>

For each of the modules launched a new **"output dialog"** will apperar containing the module output, also at the bottom of the application, the **“Actions”** tab will have a new entry for each executed module.

<a href='http://wiki.inguma.googlecode.com/hg/img/Step-2.png'><img width='500' src='http://wiki.inguma.googlecode.com/hg/img/Step-2.png' /></a>

Once all modules finish to execute, some new data will be added in the **two main information areas** of the GUI: _the map and the data tree_.

On the tree a new node will appear for the new target containing all the information gathered. If you want to see all it at the same time, press the button **“Show Log”** at the top toolbar to _hide the log window_.

The main window is dominated by the network map, press the button **“Show KB”** to _hide also the side pannel_ and give more space to the map. Actually _the map shows network trace to the target_ and we can have it also clustered by ASN information if we _right-click on a blank part of the map_ and press **“Get ASN”** option:

<a href='http://wiki.inguma.googlecode.com/hg/img/Step-3.png'><img width='500' src='http://wiki.inguma.googlecode.com/hg/img/Step-3.png' /></a>

After finished, if you recover bottom pannel with the **“Show Log”** button, change to the **“Logs”** tab so you can see this _module output_.

<a href='http://wiki.inguma.googlecode.com/hg/img/Step-4.png'><img width='500' src='http://wiki.inguma.googlecode.com/hg/img/Step-4.png' /></a>

Now the map offers information about the nodes between our network and the target and the networks we cross in every comunication. The toolbar at the right of the map offers options to modify **map “Zoom”** (first four buttons) and **“Orientation”** (next four ones with arrow icons).

The last one is helpful in situations were you have many distant targets and you are not interested in intermediate nodes, by pressing it the graph will **fold those nodes** to allow faster access to targets.

<a href='http://wiki.inguma.googlecode.com/hg/img/Step-5.png'><img width='500' src='http://wiki.inguma.googlecode.com/hg/img/Step-5.png' /></a>

This map has **two different contextual menus** that popup on _right clicking a node or a blank portion of the graph_.

The node's menu offers many node's information and also classified modules that can be launched against this node.

The graph menu goups actions that affect the whole graph, like the **“Get ASN”** we already used, and different graphs that show the Knowledge Base (KB) information in different manners.

[Step-XX.png]

Let's advance with a portscan probe against our target. For this we will use **“nmapscan”** module. On ginguma's startup one of the dependency checks looked for nmap presence. If the check was ok right click on target node (in red) and go to **“Gathers->Scanners->nmapscan”**:

<a href='http://wiki.inguma.googlecode.com/hg/img/Step-6.png'><img width='500' src='http://wiki.inguma.googlecode.com/hg/img/Step-6.png' /></a>

This new dialog offers many **scan profiles** already prepared and the option to customize your scan by manually feeding the command text entry. If you don't remember any Nmap option just press the **“Help”** button.

<a href='http://wiki.inguma.googlecode.com/hg/img/Step-7.png'><img width='500' src='http://wiki.inguma.googlecode.com/hg/img/Step-7.png' /></a>

Wait until scan finishes and then let's see what has changed. Now we can see _scan results on the normal popup dialog_. Also _KB Tree and map have been updated_ with new information regarding open ports, services found and Operative system.

<a href='http://wiki.inguma.googlecode.com/hg/img/Step-8.png'><img width='500' src='http://wiki.inguma.googlecode.com/hg/img/Step-8.png' /></a>

On the targte's node at the map we can see now OS infromation directly and the new information on the node's menu:

<a href='http://wiki.inguma.googlecode.com/hg/img/Step-9.png'><img width='500' src='http://wiki.inguma.googlecode.com/hg/img/Step-9.png' /></a>

The **"Services"** submenu groups information and actions for each one of the open ports found. Information like _port number or service detected_ and actions like _open in a browser_ (for HTTP related ports) or _in terminal_ (telnet or console like servces). Also **bruteforce modules** are offered here.

As we found an HTTP server on port 80 of this target, let's do some basic _vulnerability assesment_ of the service using the **nikto module**. First, let's _update the nikto rules database_ by pressing the **“Properties”** button on the _top toolbar_, going to **“Update”** tab and pressing the update button for the **“Nikto Rules”**.

<a href='http://wiki.inguma.googlecode.com/hg/img/Step-10.png'><img width='500' src='http://wiki.inguma.googlecode.com/hg/img/Step-10.png' /></a>

As always, once finished a module output dialog will popup with the output information. So we now have the rules updated and all we need is to popup the target's menu and go to **“Gathers->web->nikto”** module.

A small dialog will ask for the module required information: _Target IP_ already filled, set _Port_ to 80 and _Timeout_ to 2. Press **"Accept"** and wait for some time as more that 3000 checks take long to complete... ;-)

<a href='http://wiki.inguma.googlecode.com/hg/img/Step-11.png'><img width='500' src='http://wiki.inguma.googlecode.com/hg/img/Step-11.png' /></a>

As new vulnerabilities are found, they are added to the module _output dialog_:

<a href='http://wiki.inguma.googlecode.com/hg/img/Step-12.png'><img width='500' src='http://wiki.inguma.googlecode.com/hg/img/Step-12.png' /></a>

Once finished a summary of the results will be added to the dialog and _more data to the KB tree_, of course:

<a href='http://wiki.inguma.googlecode.com/hg/img/Step-13.png'><img width='500' src='http://wiki.inguma.googlecode.com/hg/img/Step-13.png' /></a>

And more important, the node menu has a new submenu under port 80 with _all the vulnerabilities found_ , just by clicking on each of them, they will be **opened on the browser**.

<a href='http://wiki.inguma.googlecode.com/hg/img/Step-14.png'><img width='400' src='http://wiki.inguma.googlecode.com/hg/img/Step-14.png' /></a>

False positives are as common as with the real nikto ;-)

Now that we collected more information regarding the target and it's services we can start exploring other graphs by using the graph's context menu.

On those other graphs you can see _relations between IP, ports, vulnerabilites, etc..._ feel free to explore.

<a href='http://wiki.inguma.googlecode.com/hg/img/data_vis.png'><img width='500' src='http://wiki.inguma.googlecode.com/hg/img/data_vis.png' /></a>

Now let's **search for exploits** for the _OpenSSH version we identified on port 22_. First we need to download, or update, the exploits so let'g go back to the **“Properties”** dialog, **“Update”** tab and press the **“Update”** button for _Exploit DB_. Before downloading the exploits, switch the _bottom pannel_ to **“Logs”** tab to folow the _actions performed_. This will _take some time_ and make you Hard drive work as there are many exploits to unpack:

<a href='http://wiki.inguma.googlecode.com/hg/img/Step-15.png'><img width='500' src='http://wiki.inguma.googlecode.com/hg/img/Step-15.png' /></a>

Once finished we can go to the **“Exploit”** tab on the _left of the main window_ where we will be able to manage them. _Exploits need some seconds to load._

Once loaded we can fill the **“Text to search”** entry with the version of OpenSSH we found and press the **“Search”** button:

<a href='http://wiki.inguma.googlecode.com/hg/img/Step-16.png'><img width='500' src='http://wiki.inguma.googlecode.com/hg/img/Step-16.png' /></a>

To study one exploit in more detail just **right click** on it and the _inguma's editor will popup_ with the code of the selected exploit:

<a href='http://wiki.inguma.googlecode.com/hg/img/Step-17.png'><img width='500' src='http://wiki.inguma.googlecode.com/hg/img/Step-17.png' /></a>

Actually we didn't found an exploit for this version but we can also _search for the HTTP server, the OS, etc..._ if happen that we find a working one, just look at the _path column_, create a new terminal by pressing the **“New Tab”** button at the **“Term”** tab at the _left of the main window_, and go to this path to execute the exploit.

<a href='http://wiki.inguma.googlecode.com/hg/img/Step-18.png'><img width='500' src='http://wiki.inguma.googlecode.com/hg/img/Step-18.png' /></a>

Automation of this search by adding an option on the node's menu is work in progress, as is to open the terminal in the adecuate directory on double clicking one exploit.

Finally press **“Save”** button at the _top toolbar_ if you want to **save the actual work** for the future.

There is much more that inguma has to offer but for knowing all the details you will have to read the whole documentation.