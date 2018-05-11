Start your own Internet Radio
### Requirements
  1. [Icecast 2](http://icecast.org/)<br />
    Icecast is an free internet radio streaming server <br />
  2. [Ices-0/ Ices-2](http://icecast.org/ices/)<br />
    Ices can stream list-of-songs.<br />
    we are using Ices0.4 since Ices2 doesn't support mp3.<br/>
  3. [B.U.T.T(Broadcast using this tool)](https://danielnoethen.de/)<br />
    B.U.T.T is used to live stream audio data from computer mic.<br />
    example: podcast, interview e.t.c.<br />
  
### Installation Guide
#### 1. Icecast2 
  ``> sudo apt-get install icecast2`` <br/>
  Afterwards we must edit /etc/icecast2/icecast.xml. Most default values should work fine for now, but you should change the     passwords in the <authentication>...</authentication> section.<br />
  ``> vi /etc/icecast2/icecast.xml`` <br/>
  Now edit /etc/default/icecast2 to enable icecast2<br />
  ``> vi /etc/default/icecast2`` <br/>
  and set ENABLE=true<br />
  
  now start icecast server using.<br />
  ``> /etc/init.d/icecast2 start`` <br/>
  In case of any problem installing icecast2 follow this [link](https://www.howtoforge.com/linux_webradio_with_icecast2_ices2)<br />
#### 2. Ices 0.4
 Mp3 streaming is disabled in Ices2 (Ices2 supports only ogg), so you've to manually download, compile & install Ices-0.4.
 Dependencies<br />
 ``> apt-get install libmp3lame-dev libxml2-dev libshout-dev libvorbis-dev`` <br/> 
 
    cd /tmp/
    wget http://downloads.us.xiph.org/releases/ices/ices-0.4.tar.gz
    tar xf ices-0.4.tar.gz
    cd ices-0.4/
    ./configure --prefix=/usr/local --with-pic --with-lame
    make
    make install

    mkdir /etc/ices
    cp /usr/local/etc/ices.conf.dist /etc/ices/ices.conf
verify installation try this in terminal<br />
``> ices --version`` <br/> 

#### 3. B.U.T.T(Broadcast using this tool)
 Download lastest version of BUTT [Download link](https://sourceforge.net/projects/butt/files/butt/)<br />
 
    tar -xzf butt-*.tar.gz
    butt-0.1.16.tar.gz
    cd butt-0.1.13
    ./configure
    make
    sudo make install
  verify installation <br />
  ``> butt`` <br/>
### How to use Guide <br />
#### 1. Steam Playlist using Icescast2 + Ices0.4
  Make sure Icecast2 and Icse 0.4 installed sucessfully and icecast2 server is running in http://127.0.0.1:8000<br />
  we are using default icecast2 config:<br />
  ```mountpoint: stream<br/>
  post: 8000<br/>
  host: 127.0.0.1<br/>
  password: hackme
  ```
  Now create ``Playlist.txt`` file with list of mp3 song list.<br/>
  to stream mp3 with ices+icecast<br/>
  ``> ices -h 127.0.0.1 -p 8000 -m stream -P hackme -F Playlist.txt``<br/>
  Stream link: http://localhost:8000/stream <br/>
  You can open stream url using VLC [tutorial](https://www.wikihow.com/Use-VLC-Media-Player-to-Listen-to-Internet-Radio)<br/>
#### 2. Icescast2 + B.U.T.T
  start butt from the terminal<br/>
  ``> butt `` <br/>
  edit B.U.T.T settings<br/>
  go to ``settings/ main /server settings`` and add new server.<br/>
  **Server Config** <br/>
 ```Name: Test Type: IceCast
    Address: 127.0.0.1<br/>
    port: 8000
    password: hackme(default)
    IceCast Mountpoint: stream
    IceCast User: source
 ```
   close settings and start streaming by clicking on connect to server button(►)<br/>
   this will start live stream at http://localhost:8000/stream
