## VNC Viewer

Forward VNC service port 5900 to host by

```shell
    docker run -p 5900:5900 -v /path/shared/folder:/path/shared/folder {imagetag}
```

Now, open the vnc viewer and connect to port 5900. If you would like to protect vnc service by password, set environment variable `VNC_PASSWORD`, for example

```shell
    docker run -p 6080:80 -p 5900:5900 -e VNC_PASSWORD=password -v /path/shared/folder:/path/shared/folder {imagetag}
```

A prompt will ask password either in the browser or vnc viewer.

After that you can access the Desktop using a VNC viewer through localhost:5900.

## Wine Installation

This instance was created in the intent of Running an EA on MQL4, for this you might need Wine, however I decided to not add this to the repository.
If you wish to install Wine you should run this commands on the Terminal, once the image is running.

```shell
    wget -nv -O- https://dl.winehq.org/wine-builds/winehq.key | APT_KEY_DONT_WARN_ON_DANGEROUS_USAGE=1 apt-key add - 
    apt-add-repository "deb https://dl.winehq.org/wine-builds/ubuntu/ $(grep VERSION_CODENAME= /etc/os-release | cut -d= -f2) main"  
    dpkg --add-architecture i386  
    apt-get update 
    apt-get install -y --install-recommends winehq-stable     
```

After that you migh need winetricks.

```shell
    wget -nv -O /usr/bin/winetricks https://raw.githubusercontent.com/Winetricks/winetricks/master/src/winetricks 
    chmod +x /usr/bin/winetricks
    ./usr/bin/winetricks msxml6
```
