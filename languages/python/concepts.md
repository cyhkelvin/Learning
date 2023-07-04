# concepts


## import
  - module and package [reference](https://medium.com/pyladies-taiwan/python-%E7%9A%84-import-%E9%99%B7%E9%98%B1-3538e74f57e3)

## singleton
  - [reference](https://hackmd.io/P-tOlvwjSGaoVLVC6QFX3Q)
  - how to implement a singleton
  - difference between \_\_init\_\_ and \_\_new\_\_ 

## process and thread in python
  - [reference](https://www.itread01.com/content/1548457405.html)

## lambda function and partial function
  - [reference](https://github.com/dokelung/Python-QA/blob/master/questions/scope/%E7%82%BA%E4%BB%80%E9%BA%BC%E9%80%99%E5%85%A9%E6%AE%B5%20python%20lambda%20%E5%87%BA%E7%8F%BE%E4%B8%8D%E5%90%8C%E7%9A%84%E7%B5%90%E6%9E%9C.md)

## staticmethod and classmethod
  - variable cls
  - [ref](https://openhome.cc/Gossip/Python/StaticClassMethod.html)

## decorator 
  - [ref1-example](https://blog.techbridge.cc/2018/06/15/python-decorator-%E5%85%A5%E9%96%80%E6%95%99%E5%AD%B8/)
  - [ref2-moreExample](https://medium.com/citycoddee/python%E9%80%B2%E9%9A%8E%E6%8A%80%E5%B7%A7-3-%E7%A5%9E%E5%A5%87%E5%8F%88%E7%BE%8E%E5%A5%BD%E7%9A%84-decorator-%E5%97%B7%E5%97%9A-6559edc87bc0)
  - useful example of decorator:
  ```
  def record_execution_time(func):
      def wrapper(*args, **kwargs):
          global logger
          logger.info(f'{func.__name__} for {**kwargs} start executing')
          t1 = time.time()
          func(*args, **kwargs)
          t2 = time.time()
          logger.info(f'{func.__name__} for {**kwargs} execution time:{t2-t1} secs')
      return wrapper
  ```