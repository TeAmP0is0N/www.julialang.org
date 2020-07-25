# Platform Specific Instructions for Official Binaries

All official Julia binaries produce portable installations.
Once installed, the directory in which Julia was installed can be moved to a
different location on the same computer, or even to a different computer.

## Windows

Julia is available for Windows 7 and later for both 32 bit and 64 bit versions.

**We highly recommend running Julia using a modern terminal, such as installing the [Windows Terminal from the Microsoft Store](https://aka.ms/terminal).**


### Installation Notes
@@tight-list
1.  Download the Windows Julia installer from https://julialang.org/downloads/. Note, the 32-bit Julia binaries work on both 32-bit and 64-bit Windows  (x86 and x86\_64), but the 64-bit Julia binaries only run on 64-bit Windows (x86\_64).
2. Run the installer and note the installation directory. The installation directory should look something like `C:\Users\JohnDoe\AppData\Local\Programs\Julia 1.5.0`, *please note this path*. 
@@

To invoke Julia by simply typing `julia` in the command line, the Julia executable directory needs to be added to PATH. Perform the following steps to add Julia to PATH.


#### Adding Julia to PATH on Windows 10,

@@tight-list
1.  Open Run (Windows Key + R),  type in `rundll32 sysdm.cpl,EditEnvironmentVariables` and hit enter.
2.  Under either the "User Variables" or "System Variables" section, find the row with "Path", and click edit.
3.  The "Edit environment variable" UI will appear. Here, click "New", and paste in the directory noted from the installation stage. This should look something like `C:\Users\JohnDoe\AppData\Local\Programs\Julia 1.5.0\bin`
4.  Click OK. You can now run Julia from the command line, by typing `julia`!
@@

#### Adding Julia to PATH on Windows 7 or 8

@@tight-list
1.  Open Run (Windows Key + R),  type in `rundll32 sysdm.cpl,EditEnvironmentVariables` and hit enter.
2.  In the System Variables window, highlight Path, and click Edit.
3.  In the Edit System Variables window, move the cursor to the end of the field.
4.  If there is no semicolon at the end, add it and paste in the text you copied into the notepad. This should look something like `C:\Users\JohnDoe\AppData\Local\Programs\Julia 1.5.0\bin`
5.  Click OK. You can now run Julia from the command line, by typing `julia`!
@@


### Windows 7 / Windows Server 2012 Installation Notes

Windows 7 / Windows Server 2012 users also need to install:

@@tight-list
*   the [TLS easy\_fix](https://support.microsoft.com/en-us/help/3140245/update-to-enable-tls-1-1-and-tls-1-2-as-a-default-secure-protocols-in) for the package manager to work, see [this Discourse thread](https://discourse.julialang.org/t/errors-for-git-pkg/9351) for more details.
*   [Windows Management Framework 3.0 or later](https://docs.microsoft.com/en-us/powershell/scripting/wmf/overview) to include PowerShell 3.0 or later.
@@

### Uninstallation

Uninstallation is preferably performed by using the Windows uninstaller. The directory in `%HOME%/.julia` can then be deleted if you want to remove all traces of Julia (this includes user installed packages).


## macOS

On macOS, a `Julia-<version>.dmg` file is provided, which contains `Julia-<version>.app`. Installation is the same as any other Mac software. Drag the `Julia-<version>.app` to Applications Folder's Shortcut. You can also run Julia from the disk image by opening the app. Julia runs on macOS 10.8 and later releases.

To start running Julia from the Terminal, you can do the following:

Navigate to `/usr/local/bin` and remove the `julia` file. Then type the following command:

```
ln -s /Applications/Julia-<version>.app/Contents/Resources/julia/bin/julia /usr/local/bin/julia
```

which creates a symlink to the Julia version of your choosing.

Remember to replace the version of `Julia-<version>.app` above with the version of your Julia app. Once that is done, you can close the shell profile page and quit Terminal. Now, just simply open Terminal again, type in `julia` in it, and it should run your version of Julia!

You can uninstall Julia by deleting Julia.app and the packages directory in `~/.julia`. Multiple Julia.app binaries can co-exist without interfering with each other. If you would also like to remove your preferences files, remove `~/.juliarc.jl` and `~/.julia_history`.



## Linux and FreeBSD

It is strongly recommended that the official generic binaries from the downloads page be used to install Julia on Linux and FreeBSD.



The generic Linux and FreeBSD binaries do not require any special installation steps, but you will need to ensure that your system can find the `julia` executable.

First, download the `.tar.gz` file from the [downloads page](/downloads/). Most users would prefer the `glibc` version of the distribution unless you know that your system uses `musl`. You need to extract this file to a suitable location. To extract the file, you can use the following command:

```
tar -xvzf julia-x.y.z-linux-x86\_64.tar.gz
```

This will extract the files to a folder named `julia-x.y.z`. We would refer this as `<Julia directory>`. To run Julia, you can do any of the following:

*   Create a symbolic link to `julia` inside a folder which is on your system `PATH`
*   Add Julia's `bin` folder (with full path) to your system `PATH` environment variable
*   Invoke the `julia` executable by using its full path, as in `<Julia directory>/bin/julia`

To add Julia's `bin` folder (with full path) to `PATH` environment variable, you can edit the `~/.bashrc` (or `~/.bash_profile`) file. Open the file in your favourite editor and add a new line as follows:

```
export PATH="$PATH:/path/to/<Julia directory>/bin"
```

Apart from this, there are several ways through which you can change environment variable. You can follow [this guide](https://help.ubuntu.com/community/EnvironmentVariables) to find out a way convenient for you.

Julia installs all its files in a single directory. Deleting the directory where Julia was installed is sufficient. If you would also like to remove your packages, remove `~/.julia`. The startup file is at `~/.juliarc.jl` and the history at `~/.julia_history`.



# Platform Specific Instructions for Unofficial Binaries



The following distribution-specific packages are community contributed. They may not use the right versions of Julia dependencies or include important patches that the official binaries ship with. In general, bug reports will only be accepted if they are reproducible on the official generic binaries on the downloads page.



## Chocolatey on Windows

If you use Chocolatey for package management, you can install the latest Julia release by executing the following one-liner, in either a powershell or command prompt:

```
choco install julia --confirm
```

Chocolatey automatically creates a shim for the Julia executable, so you simply type `julia` to run Julia in the terminal. When a new version is released simply execute `choco upgrade julia --confirm`. If you want to uninstall Julia run `choco uninstall julia --confirm`.



## HomeBrew on Mac

Julia can be installed using the [Homebrew package manager](https://brew.sh/) as follows:

```
brew cask install julia
```

This automatically puts the binary into a directory in the user's PATH, so you can simply type `julia` to run Julia in the terminal.



## Fedora/RHEL/CentOS/SL/OEL Linux

A [Copr repository](https://copr.fedoraproject.org/coprs/nalimilan/julia/) is provided for Fedora, RHEL, CentOS, Scientific Linux and Oracle Enterprise Linux systems to allow for automatic updating to the latest stable version of Julia.

If you are using RHEL, CentOS, Scientific Linux or Oracle Enterprise Linux (version 5 or higher), first [enable EPEL](https://fedoraproject.org/wiki/EPEL#How_can_I_use_these_extra_packages.3F) for your distribution version. Then follow the steps below.

If you are using Fedora (version 19 or higher), directly run:

```
sudo dnf copr enable nalimilan/julia
sudo yum install julia
```

If you are using CentOS (version 7 or higher), directly run:

sudo yum-config-manager --add-repo https://copr.fedorainfracloud.org/coprs/nalimilan/julia/repo/epel-7/nalimilan-julia-epel-7.repo
sudo yum install julia

If both `dnf` and `yum-config-manager` are not available for your distribution, download the relevant `.repo` file from the Copr webpage, copy it to `/etc/yum.repos`, and run the second command.

Note that Fedora guidelines advise against uploading new breaking releases to official repositories: therefore your distribution will not provide the new major versions of Julia which were published after it. When reporting issues, please ensure you are using the latest available release by using one of the Copr repositories displayed on this page. In order to use nightly Julia builds, replace `nalimilan/julia` with `nalimilan/julia-nightlies` in the instructions above. These can then be updated with `yum upgrade julia`.



## Debian/Ubuntu Linux

Recent Debian/ubuntu distributions include their own build of Julia, which can be installed in the usual way. If this is not the version of Julia you want, you will need to use the official binaries.

```
sudo apt install julia
```

## Arch Linux
The Arch User Repository has [a package for Julia](https://aur.archlinux.org/packages/julia-bin) that is built from the official binaries of Julia. To install it run:

```
sudo pacman -S base-devel git
git clone https://aur.archlinux.org/julia-bin.git
cd julia-bin
makepkg -si
```

## FreeBSD Ports

Julia is available in the [Ports Collection](https://svnweb.freebsd.org/ports/head/lang/julia/). To install from the FreeBSD binary package manager, `pkg`, run

```
pkg install julia
```
