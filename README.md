# FLAC2M4A
Hi!
This script has been created to convert lossless files (FLAC format) in lossy files (M4A format with codec aac). By default it looks for flac files in `$PWD` path, and it saves converted m4a files (_default 320kbps for a good quality_) to output directory that it will create if it doesn't exists.
## Dependencies
To use this script you need some dependencies. It uses [avconv](https://libav.org/avconv.html) for convertion.

_On Debian based distros you should install these packages_:
```
sudo apt-get update
sudo apt-get install libav-tools
```
_On Gentoo_:  
**After setting appropriate USE flags, run the next command:**
<pre><code><b>root #</b> emerge --ask media-video/libav</code></pre>
_On other distros_ use [Download section of Libav](https://libav.org/download/) to download _tarball_ files or download the package from [GitHub - libav/libav](https://github.com/libav/libav). Once you have downloaded it, follow the internal instructions.

## Hint
Can you use **flac2m4a** everywhere in your system if you insert the path of this script in your `$PATH`. My advice is to follow the next commands:
```
user@linuxmachine ~ $ ls
flac2m4a
user@linuxmachine ~ $ mkdir bin
user@linuxmachine ~ $ mv flac2m4a bin/
user@linuxmachine ~ $ ln -s flac2m4a/flac2m4a bin/flac2m4a
user@linuxmachine ~ $ export PATH=/home/user/bin/:$PATH
```
Now run **flac2m4a** everywhere!

## How it work

[![Preview video](http://img.youtube.com/vi/Pz7HKKJeIIM/maxresdefault.jpg)](http://www.youtube.com/watch?v=Pz7HKKJeIIM)

_Default settings_:
* `pathname` : is the work directory from you launch this program (`$PWD`)
* `output`: script creates a new directory called _output_ if it doesn't exists
* `bitrates`: It's setted to _320kbps_

_Directories' structure_:  
**I supponed that you've called `<name_of_link>` (previous created) as `flac2m4a`**
```
user@linuxmachine ~/bin/$ tree
.
├── flac2m4a -> flac2m4a/flac2m4a
├── flac2m4a
│   ├── doc
│   │   └── help
│   ├── flac2m4a
│   └── README.md
```

```
user@linuxmachine ~/Music $ tree
.
├── other_music
│   ├── Mayito Rivera - Necesito una amiga (Live).flac
│   └── Mayito Rivera - Negrito bailador.flac
├── Ray Barretto - Amor artificial.flac
├── Ray Barretto - Arrepientete.flac
└── Ray Barretto - Indestructible.flac
```
_Examples_:  
**Simple run of `flac2m4a`: it will create `output` folder with converted files inside it**
```
user@linuxmachine ~/Music $ flac2m4a
I'll convert all FLAC files inside ./
I've found 3 FLAC files to convert
	.
	.
	.
	.
	.
Done!
user@linuxmachine ~/Music $ tree
.
├── other_music
│   ├── Mayito Rivera - Necesito una amiga (Live).flac
│   └── Mayito Rivera - Negrito bailador.flac
├── output
│   ├── Ray Barretto - Amor artificial.m4a
│   ├── Ray Barretto - Arrepientete.m4a
│   └── Ray Barretto - Indestructible.m4a
├── Ray Barretto - Amor artificial.flac
├── Ray Barretto - Arrepientete.flac
└── Ray Barretto - Indestructible.flac
```
**Using `-o` or `--output-directory` <directory_name>: It will create all folders with converted files indise it**
```
user@linuxmachine ~/Music $ flac2m4a -o conversion/Barretto
I'll convert all FLAC files inside ./
I've found 3 FLAC files to convert
	.
	.
	.
	.
	.
Done!
user@linuxmachine ~/Music $ tree
.
├── conversion
│   └── Barretto
│       ├── Ray Barretto - Amor artificial.m4a
│       ├── Ray Barretto - Arrepientete.m4a
│       └── Ray Barretto - Indestructible.m4a
├── other_music
│   ├── Mayito Rivera - Necesito una amiga (Live).flac
│   └── Mayito Rivera - Negrito bailador.flac
├── Ray Barretto - Amor artificial.flac
├── Ray Barretto - Arrepientete.flac
└── Ray Barretto - Indestructible.flac
```
**Using `-p` or `--path` <directory_name>: It will search FLAC files in `<directory_name>`, then they will be converted in output folder**
```
user@linuxmachine ~/Music $ flac2m4a -p other_music
I'll convert all FLAC files inside other_music
I've found 2 FLAC files to convert
	.
	.
	.
	.
	.
Done!
user@linuxmachine ~/Music $ tree
.
├── conversion
│   └── Barretto
│       ├── Ray Barretto - Amor artificial.m4a
│       ├── Ray Barretto - Arrepientete.m4a
│       └── Ray Barretto - Indestructible.m4a
├── other_music
│   ├── Mayito Rivera - Necesito una amiga (Live).flac
│   └── Mayito Rivera - Negrito bailador.flac
├── output
│   ├── Mayito Rivera - Necesito una amiga (Live).m4a
│   └── Mayito Rivera - Negrito bailador.m4a
├── Ray Barretto - Amor artificial.flac
├── Ray Barretto - Arrepientete.flac
└── Ray Barretto - Indestructible.flac
```
**Use `-b` or `--bitrates` to set bitrates for output files**
```
user@linuxmachine ~/Music $ flac2m4a --bitrates 192
```
**Use `-f` or `--file` <file_name> to convert just <file_name>**
```
user@linuxmachine ~/Music $ flac2m4a -f Ray\ Barretto\ -\ Amor\ artificial.flac
```

**NB**: Obviously, all options can be used together.


## Thanks :)
