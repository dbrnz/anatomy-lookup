# anatomy-lookup
Ontology lookup to UBERON and ILX

### Install
```
pip install git+https://github.com/napakalas/anatomy-lookup.git
```

### Lookup use
```python
from anatomy_lookup import AnatomyLookup

al = AnatomyLookup()
al.search('nasophayrnx')
```
results
```
('http://purl.obolibrary.org/obo/UBERON_0001728',
 'nasopharynx',
 0.8313473463058472)
```

can use force
```
al.search('cochlear g.', force=True)
```
results
```
('http://purl.obolibrary.org/obo/UBERON_0000395',
 'cochlear ganglion',
 1.0000001192092896)
```

### Update UBERON and ILX terms
```
al.update_terms()
```

### Lookup with scope
```
al.search_with_scope('C1', ['Spinal cord'])
```
results
```
[('http://purl.obolibrary.org/obo/UBERON_0006469',
  'C1 segment of cervical spinal cord',
  0.758830189704895),
 ('http://purl.obolibrary.org/obo/UBERON_0007266',
  'intervertebral disk of atlas',
  0.7131606340408325),
 ('http://purl.obolibrary.org/obo/UBERON_0002828',
  'ventral cochlear nucleus',
  0.6487032771110535),
 ('http://purl.obolibrary.org/obo/UBERON_0006489',
  'C2 segment of cervical spinal cord',
  0.5675715208053589),
 ('http://purl.obolibrary.org/obo/UBERON_0006478',
  'Brodmann (1909) area 37',
  0.5620466470718384)]
```
running with force is also available
```
al.search_with_scope('C1', ['Spinal cord'], force=True)
```

### Close instance to free resource
```python
al.close()
```

###  Rebuild term embedding
```python
al.build_indexes()
```
This will download the latest release of SCKAN from https://github.com/SciCrunch/NIF-Ontology/releases
an then build the index

### Running annotation
```
from anatomy_lookup import AnatomyAnnotator
anno = AnatomyAnnotator()
anno.annotate('annotation.json','name', ['systems', 'organ'])
```
can use force also
```
anno.annotate('annotation.json','name', ['systems', 'organ'], force=True)
```

### Save to xlsx
```
anno.save_to_xlsx('annotation_test.xlsx')
```

### Save to json
```
anno.save_to_json('annotation_test.json')
```
