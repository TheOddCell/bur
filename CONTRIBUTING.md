# Contributing/Adding your own packages
Each package directory may only contain 10kB.

Any other files at that point must be downloaded from the internet from an open source hoster, like github, gitlab, or your own git location
## Directory tree
```
[root]
├── scripts - No binaries unless self contained for all supported architectures
│   └── package
│       ├── info.bur
│       └── [scripts]
└── fetch - brl fetch scripts.
    └── fetchpackage
        ├── info.bur
        └── [fetch script]
```
### Scripts
Exactly what they say on the tin.
### Fetch scripts
See https://bedrocklinux.org/0.7/extending.html#brl-fetch-new-distros
### `info.bur`
Here's an example from `fetch/idlebox`:

(both fetch scripts and normal scripts use the same format and comments don't actually work in `pmmm` as of this moment)
```
version=2.0.0
description=Simple stratum with just busybox and a few config files
files=idlebox
# ^ Any files that will be installed. May include URLs or normal files, seperated by spaces.
# | If this is a script, it will be placed in /bin or the helper's desired location.
# | If this is a fetch script, it will be placed in /bedrock/share/brl-fetch/distros/.
url=https://github.com/TheOddCell/idlebox/
# ^ Homepage URL
maintainer=TheOddCell
# ^ Seperated by spaces, GitHub usernames of anyone who is allowed to edit this
readmepls=please read the setup instructions at https://github.com/TheOddCell/idlebox/blob/main/README.md
# ^ Important info, such as "Please read the readme!".
licence=The Unlicence
# ^ Licence that your code uses.
```
Any files not listed in `files` will be uncopied, but still usable depending on the helper.

For `pmmm`, it will be placed in `[pmmm strata]/usr/bur/[type]/[name]`
