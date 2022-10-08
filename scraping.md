# playground
https://scrapinghub.github.io/xpath-playground/  
http://www.whitebeam.org/library/guide/TechNotes/xpathtestbed.rhtm
# lxml and xpath example
```python
# https://stackoverflow.com/questions/2084670/how-to-extract-links-from-a-webpage-using-lxml-xpath-and-python
import lxml.html

html_string = '''<!DOCTYPE html PUBLIC "-//W3C//DTD HTML 4.01 Transitional//EN"
   "http://www.w3.org/TR/html4/loose.dtd">

<html lang="en">
<head/>
<body>
    <table border="1">
      <tbody>
        <tr>
          <td><a href="http://stackoverflow.com/foobar" title="Foobar">A link</a></td>
        </tr>
        <tr>
          <td><a href="http://stackoverflow.com/baz" title="Baz">Another link</a></td>
        </tr>
      </tbody>
    </table>
</body>
</html>'''

doc = lxml.html.fromstring(html_string)

doc.xpath("//a[@href='http://stackoverflow.com/foobar']")[0].text
  'A link'
doc.xpath("//a[@href='http://stackoverflow.com/foobar']")[0].get("title")  # attribute
  'Foobar'
doc.xpath("//ns:entry", namespaces={"ns":"http://example.com/test"})  # namespace
  ???
```

## lxml
https://jessicastringham.net/2018/09/21/xml/  
https://docs.python.org/3.6/library/xml.etree.elementtree.html
# xpath
https://devhints.io/xpath
# Examples
```html
<a href="https://www.macrotrends.net/stocks/charts/JNJ/johnson-johnson/stock-price-history">Johnson &amp; Johnson (JNJ)</a>
```
```python
links[0].get('href')
  'https://www.macrotrends.net/stocks/charts/JNJ/johnson-johnson/stock-price-history'
links[0].attrib
  {'href': 'https://www.macrotrends.net/stocks/charts/JNJ/johnson-johnson/stock-price-history'}
 links[0].text
  'Johnson & Johnson (JNJ)'
```
https://www.swtestacademy.com/xpath-selenium/
