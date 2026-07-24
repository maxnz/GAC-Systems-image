# GAC-Systems-Image: The Official Gustavus Adolphus College Systems 1 & 2 (MCS-276 & MCS-376) Raspberry Pi Image

This repository is used to create/update the GAC Systems Image using Ansible and `ansible-pull`. 


## Supported Hardware Revisions

The GAC Systems Image is designed to work on the Raspberry Pi 4B - 1GB version.

The image has been tested on the following revisions:
- Raspberry Pi 4B - 1GB
- Raspberry Pi 4B - 2GB
- Raspberry Pi 4B - 4GB
- Raspberry Pi 3B
- Raspberry Pi 3B+


## How it Works

Whenever the Pi checks for an update, it downloads the repository and looks for a file called `local.yml`.
It then runs any plays in that file.
Our `local.yml` file contains one play with one task which finds all `.yaml` files in `updates/` and includes their tasks if the version number they are associated with is greater than the version reported by the Pi.
It then runs these plays in order by version number.


## Creating Your Own Copy of the Image

The image uses Ansible to minimize the amount of work you have to do to set up your image.
To start, install a fresh copy of Raspbian Buster on your Pi.
Perform basic setup and make sure the Pi has an internet connection and can reach GitHub.
Install `pipx` from `apt` if you have not already.

Then run the commands
```
pipx install --include-deps ansible
pipx ensurepath

ansible-pull -U https://github.com/maxnz/GAC-Systems-image.git -e imgVersion=0
```
This will install the latest version of the GAC Systems Image on your Pi and set it up to check for updates automatically.


## Image Tools

### gac-systems-image

The GAC Systems Image also includes a tool called `gac-systems-image` that can help you manage your image.
It can help you
- Check what version your image is
- Manually check for an image update
- View information about your Pi

Run `gac-systems-image -h` to see information about how to use the tool.


## Creating an Update

See [UPDATE.md](UPDATE.md) for instructions.
