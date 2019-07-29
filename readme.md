# monkey  get banana Prolog

## 概要

埼玉大学 人工知能 第14回 課題  

Prologを用いた猿とバナナの問題を解くプログラムの制作

## 問題設定

問題設定 — 猿とバナナの問題 — :
初期状態 state( atdoor, onfloor, atwindow, hasnot)
猿はド ア付近 (atdoor) の床の上 (onfloor) におり ， 台が窓付近にあり (atwindow)， バナナを手にしていない (hasnot)
猿が部屋の中央 (middle) で台の上に登ればバナナを 手にする ことができる (バナナは部屋の中央に吊るされている)
canget(S1) は状態 S1 から 猿がバナナを 手にする こ と ができ れば真
述語は move, canget の 2 種類， 関数は walk, push の 2 種類
canget( S1) :- move( S1, M, S2), canget( S2). は， 状態 S1 で行動 M を選択して状態 S2 に遷移し， S2から猿がバナナ を手にすることができるならば canget( S1)は真となる

## 課題

以下の Prolog プログラムで質問 canget( state( atdoor, onfloor, atwindow, hasnot)). を与えると true が出ることなく無限ループに陥る．これを節の順番を変えるだけで true と判定するプログラムに書き換えよ．

```
move( state( P1, onfloor, B, H), walk(P1,P2), state( P2, onfloor, B, H)).
move( state( P1, onfloor, P1, H), push(P1, P2), state( P2, onfloor, P2, H)).
move( state( P, onfloor, P, H), climb, state( P, onbox, P, H)).
move( state( middle, onbox, middle, hasnot), grasp, state( middle, onbox, middle, has)).
canget( state( P, C, B, has)).
canget( S1) :- move( S1, M, S2), canget( S2)
```

## 環境構築

```
$ brew install swi-prolog
```

## 実行

```
$ swi-pl -f monkey.swi
?- canget( state( atdoor, onfloor, atwindow, hasnot)).
```

## 制作日

- 課題出題日 2019/07/29
- 課題制作日 2019/07/29
- 課題提出日 2019/07/29
- 課題締切日 2019/08/09 13:00