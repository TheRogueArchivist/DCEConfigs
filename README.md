# DCEConfigs

This is the official DCE configurations repository.

Here you can share your working DCEConfig files, or download existing ones.

**PLEASE NOTE**: We have a zero tolerance policy against copyrighted files. DO NOT send any PR containing copyrighted binaries. Only DCEConfig files (text) are accepted.

## How to send your DCEConfig file

Please open a PR containing only one DCEConfig file at a time. Your config must be working and clear and must containg precise informations about the target game/software like the MD5 hash of the main executable and optionally the EAN/IAN barcode.

Here is an example of a good DCEConfig.yaml file that is welcome:

```
# DCEConfig file
# Title: Incredible Game
# EAN/IAN: 5901234123457
# MD5 (IG.exe): 0123456789ABCDEF0123456789ABCDEF
# NOTE: Remember to copy \Stuff\DATA0.DAT
# and \Stuff\DATA1.DAT from the
# original game disc to the 
# installation directory!

loader:
  target: "IG.exe" 

virtual_drives: ['L']

hooks:
  - api: "GetDriveTypeA"
    arg1: "L:\\"
    return: 5 # DRIVE_CDROM
  - api: "GetVolumeInformationA"
    arg1: "L:\\"
    arg2: "INCREDIBLE_GAME"
    return: true

file_redirections:
  - source: "L:\\Stuff\\DATA0.DAT"
    destination: ".\\Stuff\\DATA0.DAT"
  - source: "L:\\Stuff\\DATA1.DAT"
    destination: ".\\Stuff\\DATA1.DAT"
```