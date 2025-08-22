# norns shield おぼえがき

## セットアップ
詳しくは、 https://monome.org/docs/norns/shield/

### システムイメージ

#### microSDカードのフラッシュ
参考 https://monome.org/docs/norns/shield/#flashing-microsd-card

使用するnorns shieldとSBC(RPi3/4)の組み合わせによって、異なるOSのイメージを使用する。
norns shiled のバージョンが 211028 以降は、搭載されているオーディオコーデックチップが異なる。


### OSの設定
初回起動時に、メニューからwifiを設定するか、またはイーサネットに接続して、各種設定を行う。
デフォルトでsshでのリモートログインが可能。

~~~
ssh we@norns.local
~~~
パスワードは "sleep"。

wifiの設定とmicroSDカードのファイルシステムの拡張は、raspi-configのメニューから行うことができる。
~~~
sudo raspi-config
~~~

#### wifi
日本で使う場合は、wifiの設定を JP に変更する。

__raspi-config > Localiczation options > WLAN Country > JP Japan__

#### expand filesystem
nornsオフィシャルのOSイメージでは、expand filesystemを手動で実行する必要がある。

__raspi-config > advanced options > expand filesystem__ 

https://monome.org/docs/norns/shield/#expand-filesystem

#### Time Zone
__raspi-config > Localiczation options > Time Zone > Asia > Tokyo__ 


#### アップデート
- アプリケーション・ソフトウエアのアップデートは、norns shildのメニューから行う。（OSのアップデートは行われない。）
- OSのアップデートは、sshログイン後に、 apt で行う。
- aptで正常に動かなくなった場合（典型的にはkernelの書き換え、OLEDの不具合など）は、OSイメージの再インストールで対処。


## 筐体

- ケースやパネルに組み合わせる場合、ネジ類は M2.5 または M2.6 に揃える。ただし、OLEDパネルは M2 も可。
- RPiの基板上面からnorns shieldの基板裏面までの間隔は約16mm（RPiのコネクタの高さが約11mm、シールドのコネクタのベース部分が約5mm）。15mmのスペーサーにワッシャーを挟むか、16mmのスペーサーでつなげる。いずれの場合も、RPiのボードの厚み(1.65-1.7mm)を吸収するために、どこかでワッシャーによる高さの調整が必要になる。

## 電源

- microUSB による供給。 PRi用に売られているものは、 電圧降下を考慮して、5.1V - 5.4V が一般的。
- 電流は、PRi3の場合2Aで足りる。ただし、HDMI接続やeMMCを使う場合は、電流が足りなくなることがある。RPi4は、2.4A以上が無難。
- 電源によっては、ノイズが回り込むことがある。 （問題なく使えるACアダプタとして、GEO151-UB-6020 あるいは後継機種。使用実績が多い様子。）
