---
date: '2025-06-05T00:00:00Z'
draft: false
layout: 'post'
title: How I integrated AppImages into my Linux desktop
---

## intro
While I try to avoid AppImages in general, in the past I have needed to run some every once in a while. This is how I integrated the AppImages into my Linux desktop for easier use.
## the issue
I had AppImages, but no .desktop entries, so I would have to go back to the directory I saved them in every time I wanted to launch the app.
## solution
1. Put all AppImages in `~/AppImages/` or another directory of your choice. We'll need this later when we modify the .desktop files.
2. Extract the AppImage with ```./<filename>.AppImage --appimage-extract```
> Use ```--appimage-help``` for more info about other commandline flags.
3. Find the `.desktop` file in the ```squashfs-root``` folder created by the extraction.
4. Edit the `.desktop` to execute the AppImage from the correct directory: ```/home/myuser/AppImages/file.AppImage <other arguments>``` (or ```/var/home/``` if on Fedora Atomic as I am.)
5. Run ```desktop-file-install --dir=$HOME/.local/share/applications ~/<app>.desktop```
6. Run ```update-desktop-database ~/.local/share/applications``` (This will work with all custom .desktop entries, not just for AppImages)
7. An icon for the app must be present in your chosen icon theme already, or you won't have a desktop icon automatically. You can get the icon manually by grabbing it from the extracted AppImage from earlier and placing it in `~/.local/share/icons`.

*helpful links:*

[ArchWiki on desktop entries](https://wiki.archlinux.org/title/Desktop_entries#Application_entry)

[Freedesktop wiki on `desktop-file-utils` package](https://www.freedesktop.org/wiki/Software/desktop-file-utils/)

[AppImage docs on running, mounting, or extracting AppImages](https://docs.appimage.org/user-guide/run-appimages.html#mount-or-extract-appimages)
