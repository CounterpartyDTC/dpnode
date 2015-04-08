# Setup a Full Dogeparty Node

These instructions are based on Linux Ubuntu 14.04, any other Unix based distribution should work quite similar.

As `root` run the following commands:


```
# Install Docker
wget -qO- https://get.docker.com/ | sh

# Install Fig, see for latest version: http://www.fig.sh/install.html
curl -L https://github.com/docker/fig/releases/download/1.0.1/fig-`uname -s`-`uname -m` > /usr/local/bin/fig
chmod +x /usr/local/bin/fig

# Clone all the necessary repos into a project folder:
cd
mkdir dpnode
cd dpnode
git clone https://github.com/Dogeparty/dogecoind-docker.git
git clone https://github.com/Dogeparty/insight-docker.git
git clone https://github.com/Dogeparty/insight-doge-api.git
git clone https://github.com/Dogeparty/dogepartyd-docker.git
git clone https://github.com/Dogeparty/dogeblockd-docker.git
git clone https://github.com/Dogeparty/dogeparty-wallet-dev-server-docker.git

# Link the Dockerfile for the insight.js project to build a container with it later
ln insight-docker/Dockerfile insight-doge-api/Dockerfile

# Let's build all machines
fig build

# dogecoind has to sync first
fig up -d dogecoind

# And now start all the other components
fig up
```

