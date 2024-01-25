# utilities

## grammars
### tips
 - with open 
    equal to try: open(f) finally: if f: f.close()
 - a(str_list) b(str_tuple) `c = [*a, *b]` (have all elements from a and b)
 - set_A.difference(set_B) for (A - B)
 - filter(), map(), zip(), reduce()
 - expanduser() 處理路徑中 '~' 字符, splitext() 分離路徑中副檔名, path 相關指令
 - split(), rsplit(), splitline(), strip()
### encoding
 - chinese words encoding:
    https://kknews.cc/tech/g252r48.html
    https://blog.miniasp.com/post/2019/01/02/Common-Regex-patterns-for-Unicode-characters
 - str.encode('unicode-escape') # print out unicode of string

### StringIO and sys
 - [reference](https://stackoverflow.com/questions/16571150/how-to-capture-stdout-output-from-a-python-function-call)
  ```
  class Capturing(list):
    def __enter__(self):
        self._stdout = sys.stdout
        sys.stdout = self._stringio = StringIO()
        return self
    def __exit__(self, *args):
        self.extend(self._stringio.getvalue().splitlines())
        del self._stringio    # free up some memory
        sys.stdout = self._stdout
  ```
  usage:
  ```
  with Capturing() as output:
    do_something(my_object)
  ```

## packages
### basics
 - argparse [action types](https://docs.python.org/3/library/argparse.html#action)
 - [enum package](https://blog.louie.lu/2017/08/02/%E4%BD%A0%E6%89%80%E4%B8%8D%E7%9F%A5%E9%81%93%E7%9A%84-python-%E6%A8%99%E6%BA%96%E5%87%BD%E5%BC%8F%E5%BA%AB%E7%94%A8%E6%B3%95-07-enum/) build up variable types
 - [opencc](https://github.com/BYVoid/OpenCC)
  - mode
    ```
    hk2s: 繁體中文 (香港) -> 簡體中文
    s2hk: 簡體中文 -> 繁體中文 (香港)
    s2t: 簡體中文 -> 繁體中文
    s2tw: 簡體中文 -> 繁體中文 (台灣)
    s2twp: 簡體中文 -> 繁體中文 (台灣, 包含慣用詞轉換)
    t2hk: 繁體中文 -> 繁體中文 (香港)
    t2s: 繁體中文 -> 簡體中文
    t2tw: 繁體中文 -> 繁體中文 (台灣)
    tw2s: 繁體中文 (台灣) -> 簡體中文
    tw2sp: 繁體中文 (台灣) -> 簡體中文 (包含慣用詞轉換 )
    ```
 - [logging](https://docs.python.org/zh-tw/3/howto/logging.html)
 - six: compatible python2 and python3
 - mpdb (python command line debugger)
 - re
 - pytube3: download youtube video

### pytest and linters
 - linter: flake8
 - linter: pylint
 - linter: pylance


### config, yaml, json, pkl, textgrid
 - configobj configparser (讀取 .ini)
### collections
 - reference: [容器資料型態 collections](https://steam.oxxostudio.tw/category/python/library/collections.html)
 - namedtuple()
    ```python
      from collections import namedtuple

      circle = namedtuple('Point', ['x', 'y', 'r'])
      c = circle(10,20,50)

      print(c)                 # Point(x=10, y=20, r=50)
      print(c.x, c.y, c.r)     # 10 20 50
      print(c[0], c[1], c[2])  # 10 20 50
    ```
 - OrderedDict
    ```python
      from collections import OrderedDict
      a = OrderedDict()
      a['x'] = 1
      a['y'] = 2
      print(a)    # OrderedDict([('x', 1), ('y', 2)])
    ```
 - defaultdict
    ```python
      from collections import defaultdict
      a = defaultdict(lambda: 0)
      for i in 'test':
          a[i] += 1
      print(a)  # defaultdict(<function <lambda> at 0x00000279A0ED6DD0>, {'t': 2, 'e': 1, 's': 1})
      print(a['b'])  # 0
    ```
### pandas, numpy
 - pandas
    - [indexing and selecting data](https://pandas.pydata.org/pandas-docs/stable/user_guide/indexing.html#different-choices-for-indexing)
### matplotlib, seaborn
 - matplotlib [cmap](https://matplotlib.org/3.1.0/tutorials/colors/colormaps.html), [heatmap](https://matplotlib.org/3.1.1/gallery/images_contours_and_fields/image_annotated_heatmap.html)
 - seaborn [heapmap](http://seaborn.pydata.org/generated/seaborn.heatmap.html?highlight=s)
### kaldi-io
 - io operation of kaldi (feature, ark, ...)


## githubs
### [kaldi-onnx](https://github.com/XiaoMi/kaldi-onnx)
  - convert model from kaldi to onnx (converter/convert.py)


## articales
### clean code example
 - https://towardsdatascience.com/python-clean-code-6-best-practices-to-make-your-python-functions-more-readable-7ea4c6171d60
### how to write a crawing programming
 - https://www.learncodewithmike.com/2020/02/python-beautifulsoup-web-scraper.html