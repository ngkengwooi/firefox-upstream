# Firefox Upstream

[Debian Stable](https://www.debian.org) does not ship the regular release of [Mozilla Firefox](https://www.firefox.com), but [Firefox ESR](https://packages.debian.org/stable/firefox-esr). Those who wish to install the regular Firefox from Mozilla will usually have to install the binaries into their own home directory and create the application shortcut [manually](https://wiki.debian.org/Firefox). This launcher script automates that process. I call the project repository 'Firefox Upstream' because it uses the Firefox binaries directly from Mozilla.

The installation script installs a launcher script and an application shortcut system-wide. The shortcut appears in the application menu as 'Mozilla Firefox'. It uses the same icon as Firefox ESR, which is installed by default with most desktop environments on Debian. When the user launches that shortcut, the launcher script checks whether Firefox is installed in the user's home directory. If it is, the launcher script launches that; else, the launcher downloads the latest release of Firefox from Mozilla's server, installs it in the user's home directory, and launches that. 

Files are installed at the following locations:
* Firefox binaries: $HOME/.local/share/firefox/
* Launcher script: /usr/local/bin/firefox
* Application shortcut: /usr/share/applications/firefox-upstream.desktop

## Why?

I wrote the scripts for my own use. I manage several multi-user computers, all running Debian Stable. I wanted every user to be able to install the latest Firefox from Mozilla easily. I didn't want to install it system-wide and have to update them manually. Firefox installed in the user's own home directory will update itself.

## How to use

Clone this repository or download the ZIP archive to your computer.

```
git clone https://github.com/ngkengwooi/firefox-upstream.git
```

Make the scripts executable:

```
cd firefox-upstream
chmod +x firefox install
```

As root or superuser, execute the installation script:

```
sudo ./install
```

A new Firefox icon should appear in the application menu. Launch that to start installing Firefox.

## Known issues

1. The first time you try to launch Firefox using the launcher script, it will take a while for the browser to appear. This is because the script needs to download and then install the binaries in the background. This is expected behaviour. The browser should subsequently launch almost immediately.
2. If you uninstall Firefox ESR, the shortcut for the launcher script will lose its icon. Either modify the script to point to another icon (for example, the generic web-browser.png icon), or keep Firefox ESR installed.
