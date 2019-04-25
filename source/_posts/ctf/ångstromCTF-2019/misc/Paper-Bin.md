---
title: Paper Bin (ångstromCTF 2019)
date: 2019-04-25
tags:
- "CTF"
- "ångstromCTF 2019"
categories: misc
---

{% asset_img problem.png %}

## 解説

ただのフォレンジックでした。(ヒントを見てわかった)

まずは `paper_bin.dat` をダウンロードします。

あとは `foremost` で一発でした。

```shell
λ foremost paper_bin.dat
foremost: /usr/local/etc/foremost.conf: No such file or directory
Processing: paper_bin.dat
|*|
```

出力された `outpu/audit.txt` を確認すると pdf が20個も隠れていることがわかる。

```shell
λ cat output/audit.txt
Foremost version 1.5.7 by Jesse Kornblum, Kris Kendall, and Nick Mikus
Audit File

Foremost started at Mon Apr 22 14:28:03 2019
Invocation: foremost paper_bin.dat
Output directory: /Users/gupi/Desktop/output
Configuration file: /usr/local/etc/foremost.conf
------------------------------------------------------------------
File: paper_bin.dat
Start: Mon Apr 22 14:28:03 2019
Length: Unknown

Num	 Name (bs=512)	       Size	 File Offset	 Comment

0:	00000000.pdf 	     341 KB 	        222
1:	00000688.pdf 	     346 KB 	     352478
2:	00001384.pdf 	     363 KB 	     708830
3:	00002112.pdf 	     353 KB 	    1081566
4:	00002824.pdf 	     333 KB 	    1446110
5:	00003496.pdf 	     370 KB 	    1790174
6:	00004240.pdf 	     349 KB 	    2171102
7:	00004944.pdf 	     388 KB 	    2531550
8:	00005728.pdf 	     356 KB 	    2932958
9:	00006448.pdf 	     318 KB 	    3301598
10:	00007088.pdf 	     411 KB 	    3629278
11:	00007912.pdf 	     351 KB 	    4051166
12:	00008616.pdf 	     317 KB 	    4411614
13:	00009256.pdf 	     319 KB 	    4739294
14:	00009896.pdf 	     339 KB 	    5066974
15:	00010576.pdf 	     324 KB 	    5415134
16:	00011232.pdf 	     321 KB 	    5751006
17:	00011880.pdf 	     293 KB 	    6082782 	  (PDF is Linearized)
18:	00012472.pdf 	     374 KB 	    6385886
19:	00013224.pdf 	     344 KB 	    6770910
Finish: Mon Apr 22 14:28:04 2019

20 FILES EXTRACTED

pdf:= 20
------------------------------------------------------------------

Foremost finished at Mon Apr 22 14:28:04 2019
```

`00011880.pdf` にだけ `(PDF is Linearized)` という表示が出てるので、このファイルを調べるとフラグゲット。

## フラグ

`actf{proof_by_triviality}`

## 参考リソース

- [Foremost](http://foremost.sourceforge.net/)