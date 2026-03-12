# CSV, JSON, and XML Parsing

## Explanation

Data interchange formats like CSV, JSON, and XML are ubiquitous. Python provides standard library modules to read and write these formats easily.

### CSV

Use the `csv` module for comma-separated values.

```python
import csv

# writing
data = [["Name","Age"], ["Alice",30], ["Bob",25]]
with open('people.csv', 'w', newline='') as f:
    writer = csv.writer(f)
    writer.writerows(data)

# reading
with open('people.csv', 'r', newline='') as f:
    reader = csv.reader(f)
    for row in reader:
        print(row)
```

Also supports `DictWriter`/`DictReader` for dictionaries.

### JSON

Use the `json` module for JavaScript Object Notation.

```python
import json

data = {'name': 'Alice', 'age': 30, 'items': [1, 2, 3]}
with open('data.json', 'w', encoding='utf-8') as f:
    json.dump(data, f)

with open('data.json', 'r', encoding='utf-8') as f:
    obj = json.load(f)
    print(obj)
```

For strings, use `json.dumps()` and `json.loads()`.

### XML

XML can be parsed with modules like `xml.etree.ElementTree` (for simple use), `xml.dom.minidom`, or third-party libraries like `lxml`.

```python
import xml.etree.ElementTree as ET

xml_str = '''
<root>
    <child name="foo">Text</child>
</root>
'''
root = ET.fromstring(xml_str)
for child in root:
    print(child.tag, child.attrib, child.text)

# writing
root = ET.Element('root')
child = ET.SubElement(root, 'child', attrib={'name': 'foo'})
child.text = 'Hello'
tree = ET.ElementTree(root)
tree.write('output.xml', encoding='utf-8', xml_declaration=True)
```

## Tasks

### Beginner

1. Create a CSV file representing a list of students and read it back.
2. Serialize a dictionary to JSON and then deserialize it.
3. Parse a simple XML string and extract data.

### Intermediate

1. Convert CSV data to JSON format programmatically.
2. Handle CSV files with different delimiters or quoting rules.
3. Validate XML against a simple schema or transform it.

### Advanced

1. Implement a streaming parser for large XML files using `xml.sax` or iterparse.
2. Build a data pipeline that reads CSV files, transforms the data, and writes JSON output.
3. Use third-party libraries (`pandas`, `lxml`) for complex parsing tasks.

## Quick Review

- `csv` module for tabular text files.
- `json` module for JSON serialization/deserialization.
- `xml.etree.ElementTree` for basic XML processing.
- Pay attention to encoding and newline handling.