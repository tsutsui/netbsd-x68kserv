x68kserv - NetBSD/x68k クライアント向け NFS サーバーキット


1. x68kserv って何?

この "x68kserv" イメージは、 NetBSD/x68k でサポートされている SCSI I/F を
持たない X680x0 マシンで NetBSD/x68k をネットワーク経由で起動するために必要な
「NFS 上のルートファイルシステム」の環境を簡単に用意できるようにしたものです。

2. x68kserv イメージの内容

このイメージには、ブート可能な NetBSD/i386 ファイルシステムイメージが含まれており、
dhcpd(8), mountd(8), nfsd(8) などのデーモンが自動的に起動するようになっています。
また、NetBSD/x68k のファイルシステムを NFS でエクスポートするようになっており、
これには X のサーバーとクライアントを含む、すべてのリリースバイナリが含まれています。

Since NetBSD 6.1 version, a bootable x68k floppy image that contains
a brandnew netboot loader is also provided for easy bootstrap.
NetBSD 6.1版からは、より簡単な起動ができるように、新たに追加されたネットブート用
ブートローダーを含む x68k 起動用フロッピーイメージも用意しました。 

3. 必要なもの

- x86 ベースの PC で、NIC を持ち、USB デバイスからのブートが可能なもの
- 10BASE-T クロスケーブル (または HUB)
- Neptune-X または Nereid Ethernet が載っている X680x0 で、
  起動用のフロッピーの書き込みができて、かつフロッピーから起動できる本体
- 5.25" 2HD のフロッピーディスクのメディア


4. x68kserv の使い方

1) 2GB (以上) の USB フラッシュメモリーに、
    このイメージを、gunzip(1) と dd(1) を使って書き込みます
   (Windows 用の Rawrite32.exe ツールも使えます)。
    Rawrite32.exe ツールは以下のサイトにあります:
    http://www.NetBSD.org/~martin/rawrite32/
2) USB メモリーを x86 PC に挿し、そこから起動します (起動方法はマシン毎に異なります)
3) X680x0 と x86 x68kserv PC を 10BASE-T クロスケーブルなどで接続します。
   註: x68kserv は独自のアドレス (10.0.0.xxx) で dhcpd(8) を動かしますので、
   他のネットワークには接続しないでください。
4) ネットブート用ブートローダを含む NetBSD/x68k 起動用フロッピーを用意します:
   # gzcat x68knetbootfd-20130609.img.gz | dd of=/dev/rfd0c bs=15k
   (Human68k 用の gzip.x と rawrite.x のバイナリーも使用可能です)
5) 上記のネットブート用フロッピーで NetBSD/x68k を起動します
6) あとの楽しみ方はあなた次第です :-)


5. その他

ネットブートの詳細については以下の Togetter まとめも参照してください。
http://togetter.com/li/388921

---
Izumi Tsutsui
