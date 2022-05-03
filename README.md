# Some function using for NER of NLP
- Read pickle
- write pickle
- read conll
- write conll
- convert IOtag to BIOtag
- convert BIOtag to IOtag
- convert IOtag to span
- convert doccano to CONLL
- convert CONLL to doccano

## 1.How to using 
Setup
```
pip install ner-utils
```
Using
```python
from ner_utils import ner_utils
data = ner_utils.read_pickle('demo.pkl')
```
## 2.Describe some function
- read_pickle and write_pickle
```python
data = read_pick('demo.pkl')
write_pickle(data,'new.pkl')
```

- read_conll and write_conll
```python
data = read_conll('demo.txt')
write_conll(data,'new.txt')
```
- convert doccano jsonl to CONLL
```python
'''
demo.jsonl
{'ID': 15593,
 'SOURCE': 'tan_data_185_email_BIO',
 'label': [[68, 78, 'PERSONTYPE'],
  [90, 100, 'PERSONTYPE'],
  [187, 198, 'PRODUCT']],
 'data': 'Sự hỗ trợ của các doanh nghiệp nhà nước , doanh nghiệp nước ngoài , nhà đầu tư cá nhân và nhà đầu tư tổ chức trong việc đưa ra các lựa chọn quan trọng như môi giới , giao dịch và mua bán chứng khoán có thể rất thành công .'}
 ...
 {}
 demo.txt
'''
ner_utils.convert_doccano2conll(
    doccano_path = 'demo.jsonl',
    conll_path = 'demo.txt',
    BIO = True
)
```

- convert CONLL to doccano jsonl
```python
'''
demo.txt

demo.jsonl
{'ID': 10,
 'SOURCE': 'source',
 'label': [[68, 78, 'PERSONTYPE'],
  [90, 100, 'PERSONTYPE'],
  [187, 198, 'PRODUCT']],
 'data': 'Sự hỗ trợ của các doanh nghiệp nhà nước , doanh nghiệp nước ngoài , nhà đầu tư cá nhân và nhà đầu tư tổ chức trong việc đưa ra các lựa chọn quan trọng như môi giới , giao dịch và mua bán chứng khoán có thể rất thành công .'}
....
{}

'''
ner_utils.convert_CONLL2doccano(
    conll_path = 'demo.txt',
    doccano_path = 'new.jsonl',
    start_id = 10,
    source = 'source'
)
```


## 3.How to package module to pypi
- you need account on: https://pypi.org/ and  https://test.pypi.org/
- You create folder include file: main.py (main code), licence.txt, __init__.py, README.MD, setup.cfg
- Create file setup.py include some information of package
```python
from setuptools import setup, find_packages
setup(name='ner_utils',
      version='0.1',
      description='utils for NER NLP',
      author='ndtan',
      author_email='ndtan.hcm@gmail.com',
      packages = ['ner_utils'],
      zip_safe=False)
```
- build package
```
python setup.py sdist
pip install twine
```
- Upload zipfile to pypi
```
twine upload dist/*

```
