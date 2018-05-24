# Internet Radio
**Internet radio** (also web radio, net radio, streaming radio, e-radio, IP radio, online radio) is a digital audio service transmitted via the Internet. Broadcasting on the Internet is usually referred to as webcasting since it is not transmitted broadly through wireless means. It can either be used as a stand-alone device running through the Internet, or as a software running through a single computer system([more..](https://en.wikipedia.org/wiki/Internet_radio))<br/>

In this guide, we are focussing on open source applications so that anyone with minimum Linux knowledge can create Internet Radio free of cost. 

## Software Requirement to start Internet Radio

### 1. Icecast Server
Icecast is a streaming media server which currently supports Ogg Vorbis and MP3 audio streams. It can be used to create an Internet radio station or a privately running jukebox and many things in between([more..](http://icecast.org/docs/icecast-2.4.1/introduction.html))<br/>
### 2. Ices 
To stream list of songs to Icecast server([more..](http://icecast.org/docs/icecast-2.4.1/introduction.html))<br/>
Ices-0.4 support Mp3 format.<br/>
Ices2 only support Ogg Vorbis format.<br/>
### 3. B.U.T.T(Broadcast using this tool)
Butt is to stream live audio data from your computer's Mic or Line input to an Icecast server([more..](http://icecast.org/docs/icecast-2.4.1/introduction.html))<br/>

> Note: Icecast and Ices requires either Linux or Windows.
<br/>
## Installation Guide(Ubuntu)
#### Icecast 2
installation and configuration guide -<br/>
https://www.howtoforge.com/linux_webradio_with_icecast2_ices2<br/>

#### Ices 0.4<br/>
Before installing ices make sure your system satisfies these requirements-<br/>
libmp3lame-dev, libxml2-dev, libshout-dev, libvorbis-dev <br/>
```> apt-get install libmp3lame-dev libxml2-dev libshout-dev libvorbis-dev```<br/>

then download ices-0.4.tar.gz from http://icecast.org/ices/ and make to install<br/>
```
cd /tmp/
wget http://downloads.us.xiph.org/releases/ices/ices-0.4.tar.gz
tar xf ices-0.4.tar.gz
cd ices-0.4/
./configure --prefix=/usr/local --with-pic --with-lame
make
make install

mkdir /etc/ices
cp /usr/local/etc/ices.conf.dist /etc/ices/ices.conf
```
to verify installation of Ices from the terminal -<br/>
```> ices --version ```

#### B.U.T.T(broadcast using this tool)
download Source Code (tar.gz) from https://danielnoethen.de/ and make to install<br/>
```
tar -xzf butt-*.tar.gz
cd butt-*
./configure
make
sudo make install
```
to verify installation of BUTT from the terminal -<br/>
```> butt ```
