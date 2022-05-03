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
demo.txt
...
Phái	B-ORGANIZATION
đoàn	I-ORGANIZATION
Nga	B-LOCATION
và	O
Ukraine	B-LOCATION
tại	O
vòng	B-EVENT
đám	I-EVENT
phán	I-EVENT
ở	O
Istanbul	B-LOCATION
,	O
Thổ	B-LOCATION
Nhĩ	I-LOCATION
Kỳ	I-LOCATION
,	O
ngày	B-DATETIME
29/3	I-DATETIME
.	O

...
output: 
[...,
[('Phái', 'B-ORGANIZATION'),
 ('đoàn', 'I-ORGANIZATION'),
 ('Nga', 'B-LOCATION'),
 ('và', 'O'),
 ('Ukraine', 'B-LOCATION'),
 ('tại', 'O'),
 ('vòng', 'B-EVENT'),
 ('đám', 'I-EVENT'),
 ('phán', 'I-EVENT'),
 ('ở', 'O'),
 ('Istanbul', 'B-LOCATION'),
 (',', 'O'),
 ('Thổ', 'B-LOCATION'),
 ('Nhĩ', 'I-LOCATION'),
 ('Kỳ', 'I-LOCATION'),
 (',', 'O'),
 ('ngày', 'B-DATETIME'),
 ('29/3', 'I-DATETIME'),
 ('.', 'O')]
 ]
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
