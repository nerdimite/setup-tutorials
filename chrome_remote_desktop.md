# Setup Chrome Remote Desktop for a Remote Ubuntu Machine

## 0. SSH into your remote machine

Before we begin, SSH into your remote machine using your terminal.

## 1. Install Chrome Remote Desktop

The first step is to install chrome remote desktop on your Ubuntu machine. You can do this by running the following command in the SSH terminal of your remote machine:

```bash
wget https://dl.google.com/linux/direct/chrome-remote-desktop_current_amd64.deb
sudo apt-get install --assume-yes ./chrome-remote-desktop_current_amd64.deb
```

## 2. Installing an X Windows System desktop environment

Next, we need to install an X Windows System desktop environment. This is required to run the GUI applications on the remote machine. We will be using the XFCE desktop environment. You can install it by running the following command:

```bash
sudo DEBIAN_FRONTEND=noninteractive \
    apt install --assume-yes xfce4 desktop-base dbus-x11 xscreensaver
```

Configure Chrome Remote Desktop to use the XFCE desktop environment by running the following command:

```bash
sudo bash -c 'echo "exec /etc/X11/Xsession /usr/bin/xfce4-session" > /etc/chrome-remote-desktop-session'
```

## 3. Setup Chrome Remote Desktop

1. Go to your local browser and open [Chrome Remote Desktop Headless Setup](https://remotedesktop.google.com/headless) page. Click on **Set up via SSH**.
2. Click on **Begin** and then **Next** coz we have already installed Chrome Remote Desktop on the remote machine.
3. Click on **Authorize**.
4. Copy the Debian Linux command that is shown and paste it and run it in your remote machine's SSH terminal. It will ask you to setup a 6 digit pin, so remember that.
5. Go to [Remote Access](https://remotedesktop.google.com/access) which should show your remote machine being online. Click on it to connect and enter the pin you set up earlier. Viola! You are now connected to your remote machine.

You can now run the GUI applications on your remote machine using Chrome Remote Desktop.
