##### <u>Human vs Machine data</u> 
- **human readable**
	- text, images, forms
	- mostly unstructured
	- focus on usability
- machine readable
	- needs to be structured
	- focus on efficiency
	- generally not human readable
##### <u>Markup languages </u>
A **markup language** allows code to go from human w/readable to machine w/readable. 

**SGML** is a superset of all markup languages. It separates the structure of a document to the content of the document. It contains:
tags and content: `<tag> content <\tag>`
attributes: `<tag attribute="value">`
### <u>XML</u>
- eXtensible Markup Language
- **hierarchical**
- designed to carry data (not display)
- author defines tags
- meta-tools to define purpose of tags (DTD, schemas)

An XML document can be **valid** or **invalid** against an XML schema which describes the types of data that should be contained on each line.

XML Suite:
- Syntax: defines how XML should be written
- Namespaces: global semantic partitions
- Schema: semantic definitions or validity
- XPATH: locate data
##### <u>Syntax</u>
- All elements have a closing tag
- All tags are case sensitive
- All elements are properly nested
- All documents have a root element
- All attributes are quoted `<tag id="|">`
##### <u>Namespaces</u>
