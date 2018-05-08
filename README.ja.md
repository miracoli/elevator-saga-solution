# Elevator Saga の解答

下記サイトで公開されているElevator Sagaに対する解答です。

* http://play.elevatorsaga.com/

最終的な解答コードは [elevator-saga.js](./elevator-saga.js) となります。

以降は実装の経緯になります。

## 最初の戦略

まずはAPIを読んで、エレベータとしてのあるべき動作を考えてみました。(普段乗っているエレベータの気持ちになって)

* フロアのボタンが押下された情報はフロア×方向(上/下)として保持(各フロアのボタン押下状態を取るAPIが無いのが不親切だが、そこが今回の肝なのかもしれない)
    * 停止中のエレベータで、近くにあるものを向かわせる
    * そのフロアに止まったら、該当の情報をクリア
    * フロアを通過前に情報をチェックし、進行方向と同じボタンが押下されていて、かつ乗客がまだ乗れる場合には、該当フロアに止まる
    * 行き先フロアが無くなったら、ボタンが押下されたフロアで現フロアから一番近いフロアに移動＋進行方向を設定
* エレベータ内の行き先フロアボタンが押下されたら、現在フロアから進行方向の順でソートしてフロアに止まる順番をリセットする

各Challengeを50回実行した結果は下記の通りです。(クリアできるかどうかは乱数によるぶれ幅が広い感じ)

```
Total time: 1,978 seconds
--------------------------------------------
All         :  49.11 (442/900)
Challenge  1: 100.00 (50/50)
Challenge  2:  88.00 (44/50)
Challenge  3:  94.00 (47/50)
Challenge  4:  94.00 (47/50)
Challenge  5:  50.00 (25/50)
Challenge  6:   2.00 (1/50)
Challenge  7:  16.00 (8/50)
Challenge  8:  84.00 (42/50)
Challenge  9:  94.00 (47/50)
Challenge 10:  16.00 (8/50)
Challenge 11:  62.00 (31/50)
Challenge 12:  14.00 (7/50)
Challenge 13:   0.00 (0/50)
Challenge 14:   4.00 (2/50)
Challenge 15:  32.00 (16/50)
Challenge 16: 100.00 (50/50)
Challenge 17:  30.00 (15/50)
Challenge 18:   4.00 (2/50)
--------------------------------------------
```
