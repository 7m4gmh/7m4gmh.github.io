# EUROPI おぼえがき

- EuroPi Software https://github.com/Allen-Synthesis/EuroPi/tree/main/software
- Hardware Specifications https://github.com/Allen-Synthesis/EuroPi/tree/main/hardware/EuroPi
- Build Guide https://github.com/Allen-Synthesis/EuroPi/blob/main/hardware/EuroPi/build_guide.md
- Skiff-Friendly Build Instructions hardware/EuroPi/skiff_friendly_instructions.md

## ソフトウエア開発環境
- 2024-2-6現在、micropython-europi と micropython-ssd1306 は、どちらも python 3.10 以降に非対応。対策として、thonny は、最新版ではなく、 python 3.9 を搭載した thonny v.3.3.13 を使う。 https://github.com/thonny/thonny/releases/tag/v3.3.13

## ハードウエア
- LDO (7805) をそのまま取り付けると、 浅いユーロラックに入らない。いわゆる skiff friendly にする場合は、LDOをTO-220よりも背の低いものにするか、あるいはTO-220であれば、脚を直角に折り曲げた状態で、LDOを所定の位置の裏面に取り付ける。このとき、ショートしないように、ヒートシンク用の絶縁シートなどを貼り付ける。公式インストラクション [Skiff-Friendly Build Instructions ](https://github.com/Allen-Synthesis/EuroPi/blob/main/hardware/EuroPi/skiff_friendly_instructions.md) のやり方よりも、このほうが低くできるし、安全。
  - TO-252 の LDO を 熱伝導率のよい変換基板を介して水平に浮かせて裏面に取り付ける方法もおすすめ
    - TO-252 変換基板 https://akizukidenshi.com/catalog/g/g109075/
    - 三端子レギュレーター 5V1.5A TO-252 NJM7805SDL1 https://akizukidenshi.com/catalog/g/g111237/
    - NJM7805SDL1 を使うと、LDO OUTの 1μFのキャパシタ(C2)をセラミックコンデンサに変えることも可能。（C1をはじめ、ほかのキャパシタはすべて積層セラミックで問題ないはず。）
- LDOをそのままの位置に取り付ける場合、Raspberry Pi Picoの端面スルーホールとショートしやすいので、絶縁シートの貼り付けを強くおすすめします。
- セラミックコンデンサ(100nF/0.1uF/104)のフットプリントは、かなり狭い。手持ちの部品の幅がギリギリだとリード線がショートしやすい。SMDのキャパシタ(1206/3216M,1210/3225M)であれば、そのまま裏のハンダ面に貼り付けることができる。
  - スルーホールで取付可能なキャパシタ https://akizukidenshi.com/catalog/g/g115180/
  - SMDのキャパシタ C0G @24円 https://akizukidenshi.com/catalog/g/g115180/
  - SMDのキャパシタ X5R? @5円 https://www.aitendo.com/product/6989
- Raspberry Pi Pico のUSB端子は microUSBで、耐久性が低い。 RP2040 を搭載した USB Type-C の互換品が安く出回っており、ピン配列が同じであればこちらのほうがよい。 aitendo などで販売。
  - https://www.aitendo.com/product/21381
- イヤホンジャック(Thonki conn)は、PJ-301M、PJ-398SM、WQP518MA などが使用可能。
- OLEDパネルは、ピンヘッダがパネルに接近しているものを使うこと。amazonやaliexpressで売っているものの多くは、ピンの位置がパネルから離れていて、そのままでは使えない。やむを得ずピンが離れているものを使う場合は、180度のピンヘッダを間に挟んで、はんだ付けすることで取付可能。
  - そのまま実装できる(かもしれない)OLED https://ja.aliexpress.com/item/32982681500.html
  - 細工が必要なOLED https://ja.aliexpress.com/item/1005006230711152.html
- PUSHスイッチは、RSコンポーネンツで入手可能。また、モノタロウで型番を検索して出てくれば、RSコンポーネンツ商材の取り寄せが可能。  https://www.monotaro.com/p/5027/2697/
 
