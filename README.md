# this doc for config shadowsocks for Ubuntu teminal

## workflow

1. install python, python-pip, python-pip and ss.
```
sudo apt-get install python
sudo apt-get install python-pip
sudo pip install shadowsocks
```

2. config shadowsocks, like shawdowsocks.json at root this repository root diretory, and run ss
```
sudo sslocal -c shawdowsocks.json -d start
```

3. config proxy
```
sudo apt-get install polipo
sudo cp config /etc/polipo/config
```

4. restart polipo and test
```
sudo /etc/init.d/polipo restart
export http_proxy="http://127.0.0.1:8123/"
curl www.google.com
```

## NOTITION

when you restart you computer, you need rerun this command
```
sudo sslocal -c shawdowsocks.json -d start
export http_proxy="http://127.0.0.1:8123/"
```

## option

This config is **Global** mode, if your want used **PAC** mode, need config as blew

1. install genpac
```
sudo pip install genpac
```

2. output pac file
```
mkdir ~/shadowsocks
cd shadowsocks
genpac --proxy="SOCKS5 127.0.0.1:1080" --gfwlist-proxy="SOCKS5 127.0.0.1:1080" -o autoproxy.pac --gfwlist-url="https://autoproxy-gfwlist.googlecode.com/svn/trunk/gfwlist.txt"
```

[ss-reference](https://jingsam.github.io/2016/05/08/setup-shadowsocks-http-proxy-on-ubuntu-server.html)

[pac-reference](http://www.voidcn.com/blog/hanshileiai/article/p-6208794.html)
