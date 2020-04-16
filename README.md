# The UPM Concept
UPM - The concept of package management options.
Note: This will not include any code, just ideas and represent the core of UPM as a concept.

## What is UPM?
I hate that there is 1,000 package managers. I designed UPM to take the best ideas from all of them, and add a couple ideas.

## UPM Terminology
Specific Terminology:
Argument: A command line argument used in the command (Package, DDOs, Etc)
DDO: Short for "Double Dash Opions". For example "dpkg **--install** ..." or "apt **--fix-missing** install". 
Shorthand DDO: The single dash options like "-v" for verbose and "-i" for install (on some PMs).

## UPM command line concepts
Let's say you want to install GIMP. To do it with UPM, you have the following command. \
`sudo upm install --stable --version 2.9 gimp`

Let's break it down. `sudo` is... well sudo. `upm` would be the command whoever implements this uses. `install` is the term used to get installation (more on terms later). `--stable` is the option where you want the stable release (`--rolling` is the other option. This is mandatory UNLESS you do `.UPMFile` stuff (more on that later). `--version` is the option to chose a specific version *if your repo allows for it*. `2.9` was the version we used with `--version` (it must always be after). `gimp` is the package name, it can be whatever. Any arguments can be changed through the previously mentioned `.UPMFile`.

## What are "terms"
Terms reference specifically to the terms used as `update` (update repositories), `install` (install packages), `remove` to to remove packages, etc. Whatever is supported will depend who implements UPM and if someone else makes a script. The core will involve those terms. They can also be given aliases in `.UPMFile` files.

## UPMFile's
These allow customizations for the UPM version you have. A `.UPMFile` with a `.UPMConfig/` would be included in the `/home/yourusername` directory. A `.UPMFile` would add different sources, aliases, defaults, and scripting. `.UPMFile` syntax is represented [in this file](https://github.com/KaiLikesLinux/universal-package-manager-concept/blob/master/.UPMFile). Scripting can be done however as the developer pleases, but mandatory inclusions are shell scripts allowed by a distribution (i.e. Fish, Dash, Bash, Zsh, etc.). How this is done will be standardized with getting agreements from communities. `.UPMFile`'s will also be able to call external scripts or binaries. Knowing abuse is imminant, binaries and external scripts will have no sudo access, if it requests sudo access it will be denied UNLESS you add it as "trusted", which is done by adding `.trusted` to a `script` keyword. For example `script.trusted = "/path/to/script/"`. Do not do this to scripts unless you can trust them.
