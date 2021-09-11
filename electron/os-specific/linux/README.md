# LINUX DOES NOT HAVE ONE SYSTEM FOR FILE ASSOCIATIONS

I currently do not have the ability to compile for Linux, mostly due to time reasons, however here is a general template of the `.desktop` file that should be made for a presumed installer.

```
[Desktop Entry]
Version=1.5
Type=Application
Name=Hat.sh
GenericName=Encryption program
Comment=Encrypt and decrypt any file
Exec=hat.sh --e=%U
TryExec=hat.sh
Icon=hat.sh
Terminal=false
Categories=Utilities
StartupNotify=true
MimeType=application/heb;
```
## PLEASE REMEMBER I HAVE NOT TESTED THIS
Any contributions to this would be appreciated :')