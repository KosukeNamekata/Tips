
### 便利なpythonのコード

**「基本」**pythonは、全てがオブジェクト指向プログラム  
- pythonの変数、リストなどは、全てクラスによって定義された「**インスタンス**」と同じような機能を持ち、**多くのメソッドが用意されている**。


**「基本」**ある変数の正体を調べたいとき： type, dir

- `type(x)`: xの型を返す関数です。たとえば、次のプログラムを実行すると  

- `dir(x)`: xの持っているメソッドを全て表示してくれます。


**「基本」**リストへの操作：appendとextendの違い...
「pythonのリストは、インスタンス」。numpyを入れないと、四則演算はできないが、様々なメソッドがビルドインされている。  

- `list.append(x)`: 　リストの末尾に要素を一つ追加します。a[len(a):] = [x] と等価です。

- `list.extend(x)`: イテラブルのすべての要素を対象のリストに追加し、リストを拡張します。a[len(a):] = iterable と等価です。

- `list.sort(key=None, reverse=False)`: リストの項目を、インプレース演算 (in place、元のデータを演算結果で置き換えるやりかた) でソートします。引数はソート方法のカスタマイズに使えます。 sorted() の説明を参照してください。


＊**pythonでdetrend**
- Kepler LCに対して、J.D.のホームページ参照： https://github.com/jradavenport/appaloosa/tree/master/appaloosa

- 前原さんの論文: https://ui.adsabs.harvard.edu/abs/2012Natur.485..478M/abstract

- scipyに含まれている、それぞれのmethodをまとめているサイト： https://org-technology.com/posts/low-pass-filter.html


＊**pythonで周期解析**
- gatspyに入っているperiodicで周期解析ができる
```
    from gatspy import datasets, periodic
    model = periodic.LombScargleFast(fit_period=True)
    model.optimizer.period_range = (1, 10)
    model.fit(times, lc)
    print("**Rotational Period** is {} day".format(model.best_period))　＃こういう形で、文字を埋められる。
```
- astropy.stats.LombScargleでLomb-Scargle Periodgramがかける
```
    from astropy.stats import LombScargle
    frequency, power = LombScargle(time[ss], bvamp[ss]).autopower()
```
