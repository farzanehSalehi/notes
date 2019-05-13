## Chapter1:Node Overview

### DOM:

HTML documents get parsed by a browser and converted into a tree structure of node objects representing a live document. The purpose of the DOM is to provide a programmatic interface for scripting (removing, adding, replacing, eventing, and modifying) this live document using JavaScript.


### Node Object Types:

- DOCUMENT_NODE (e.g., window.document)
- ELEMENT_NODE (e.g., `<body>`, `<a>`, `<p>`, `<script>`, `<style>`, `<html>`, `<h1>`)
- ATTRIBUTE_NODE (e.g., class="funEdges")
- TEXT_NODE (e.g., text characters in an HTML document including carriage returns
and whitespace)
- DOCUMENT_FRAGMENT_NODE (e.g., document.createDocumentFragment())
- DOCUMENT_TYPE_NODE (e.g., <!DOCTYPE html>)


### NodeType:

I list the name given to the interface/constructor that instantiates the most
common node types and their corresponding nodeType classifications by number and
name. What I hope you take away from the table is that the nodeType value (i.e., 1) is
just a numeric classification used to describe a certain type of node constructed from a
certain JavaScript interface/constructor. For example, the HTMLBodyElement interface
represents a node object that has a node type of 1, which is a classification for
ELEMENT_NODEs.

|Interface/constructor |nodeType (returned from .nodeType)|
|----------------------|----------------------------------|
|HTML*Element [e.g., HTMLBodyElement]| 1 (i.e., ELEMENT_NODE)||----------------------|----------------------------------|
|Text |3 (i.e., TEXT_NODE)||-----------------------|----------------------------------|
|Attr |2 (i.e., ATTRIBUTE_NODE)||-----------------------|----------------------------------|
|HTMLDocument |9 (i.e., DOCUMENT_NODE)||---------------------------|-----------------------------|
|DocumentFragment |11 (i.e., DOCUMENT_FRAGMENT_NODE)||---------------------------|-----------------------------|
|DocumentType |10 (i.e., DOCUMENT_TYPE_NODE)|


### Inherits properties and methods:

Each node object in a typical DOM tree inherits properties and methods from Node.
Depending on the type of node in the document, there are also additional subnode
objects/interfaces that extend the Node object.

- Object < Node < Element < HTMLElement < (e.g., HTML*Element)
- Object < Node < Attr (this is deprecated in DOM4)
- Object < Node < CharacterData < Text
- Object < Node < Document < HTMLDocument
- Object < Node < DocumentFragment


### Node properties:

- childNodes:
- firstChild:The first child of the element
- lastChild:The last child of the element
- nextSibling:If nextSibling availability return that,else return null
- nodeName:Get the name of the element
- nodeType:Get the number of the element in "NodeType"
- nodeValue:Get the value of the element
- parentNode:return parent element
- previousSibling:If previousSibling availability return that,else return null


### Node methods:

- appendChild():attached together
- cloneNode(): duplicate a single node or a node and
all its child nodes
- compareDocumentPosition()
- contains():whether a node is contained inside another node
- hasChildNodes()
- insertBefore()
- isEqualNode()
- removeChild()
- replaceChild()


### Document methods:

- document.createElement()
- document.createTextNode()


### HTML*Element properties:

- innerHTML
- outerHTML
- textContent
- innerText
- outerText
- firstElementChild
- lastElementChild
- nextElementChild
- previousElementChild
- children


### HTML element method:

- insertAdjacentHTML():method of the Element interface parses the specified text as HTML or XML and inserts the resulting nodes into the DOM tree at a specified position


## Chapter2:Document Nodes

### Documents:

- document.constructor
- document.nodeType
- document.doctype
- document.documentElement
- document.implementation.*
- document.activeElement
- document.body
- document.head
- document.title
- document.lastModified
- document.referrer
- document.URL
- document.defaultview
- document.compatMode
- document.ownerDocument
- document.hasFocus()
- document.childNodes[x]


Defines the features and versions to which you
can pass the hasFeature() method:(document.implementation.hasFeature('feature','supportVersions'))

|Feature |Supported versions|
|-----------------|-----------------|
|Core |1.0, 2.0, 3.0||-----------|-------------|
|XML |1.0, 2.0, 3.0||-------------|-------------|
|HTML| 1.0, 2.0||--------------|--------------|
|Views| 2.0||------------------|-----------|
|StyleSheets |2.0||-------------|--------|
|CSS| 2.0||-----------------|---------|
|CSS2| 2.0||----------------|-----------|
|Events |2.0, 3.0||----------|-------------|
|UIEvents| 2.0, 3.0||-----------|-----------|
|MouseEvents |2.0, 3.0||----------------|----------|
|MutationEvents| 2.0, 3.0||-------------|-------------|
|HTMLEvents| 2.0||-------------|--------------|
|Range |2.0||--------------|------------|
|Traversal| 2.0||-----------|------------|
|LS (loading and saving between files and DOM trees synchronously) |3.0||--------------|----------------|
|LS-Async (loading and saving between files and DOM trees asynchronously) |3.0||--------------|------------------|
|Validation| 3.0|


## Chapter3:Element Nodes

### HTML*Element Object Properties and Methods:

- createElement()
- tagName:same nodeName
- children
- getAttribute()
- setAttribute()
- hasAttribute()
- removeAttribute()
- classList()
- dataset
- attributes

### Class attribute:

- classList
- className
- classList.add()
- classList.remove()
- classList.contains()
- classList.toggle()

## Chapter4:Element Node Selection

###  Selecting a Specific Element Node:

- querySelector()
- getElementById()

### Selecting/Creating a List of Element Nodes:

- querySelectorAll()
- getElementsByTagName()
- getElementsByClassName()

### Selecting All Immediate Child Element Nodes:

- children

### Preconfigured Selections/Lists of Element Nodes:

- document.all : All elements in the HTML document
- document.forms : All `<form>` elements in the HTML document
- document.images : All `<img>` elements in the HTML document
- document.links : All `<a>` elements in the HTML document
- document.scripts : All `<script>` elements in the HTML document
- document.styleSheets : All `<link>` or `<style>` elements in the HTML document

## Chapter5:Element Node Geometry and Scrolling Geometry

### offsetTop and offsetLeft : 

we can get the offset pixel value of an element node from the offsetParent. These element node properties give us the distance in pixels from an element’s outside top and left borders to the inside top and left borders of the offsetParent. The value of the offsetParent is determined by searching the nearest ancestor elements for an element that has a CSS position value not equal to static.

### getBoundingClientRect():

Using the getBoundingClientRect() method, we can get the position of an element’s outside border edges as the element is painted in the browser viewport relative to the top and left edges of the viewport.

### Getting an Element’s Size(border + padding + content):

The getBoundingClientRect() method returns an object with a top, right, bottom, and left property/value as well as a height and width property/value. 

- height
- width

if you want don't use as getBoundingClientRect,you must have to use "offsetHeight" and "offsetWidth".

### Getting an Element’s Size( padding + content):

- clientHeight
- clientWidth

### Get the Topmost Element in the Viewport at a Specific Point:

- elementFromPoint

### scrollHeight and scrollWidth :

The scrollHeight and scrollWidth properties simply give you the height and width of the node being scrolled.

###  Get and Set Pixels Scrolled from the Top and Left:

- scrollTop
- scrollLeft

###  Scroll an Element into View:

- scrollIntoView() : By selecting a node contained inside a node that is scrollable, we can tell the selected node to scroll into view by using the scrollIntoView() method.

## Chapter6 : Element Node Inline Styles

###  Getting, Setting, and Removing Individual Inline CSS Properties:

- setProperty
- getPropertyValue
- removeProperty

###  Getting, Setting, and Removing All Inline CSS Properties:

- cssText
- setAttribute : Example:div.setAttribute('style','background-color:red;border:1px solid black;');
- getAttribute
- removeAttribute

### Get an Element’s Computed Styles:

- getComputedStyle() : No values can be set on a CSSStyleDeclaration object returned from getComputedStyles(), as it’s read-only

### Using the class and id Attributes to Apply and Remove CSS Properties on an Element :

- element.setAttribute('id','name');
- element.classList.add('name');
- element.removeAttribute('id');
- element.classList.remove('name');


## Chaper7 : Text Nodes

### Getting a Text Node Value:

- data
- nodeValue

### Manipulating Text Nodes:

- appendData()
- deleteData()
- insertData()
- replaceData()
- subStringData()

### differences between textContent and innerText:

- innerText is aware of CSS. So, if you have hidden text, innerText ignores this text, whereas textContent does not.
- Because innerText cares about CSS, it will trigger a reflow, whereas textContent
will not.
- innerText ignores the Text nodes contained in `<script>` and `<style>` elements.
- innerText, unlike textContent, will normalize the text that is returned. Just think of textContent as returning exactly what is in the document, with the markup removed. This will include whitespace, line breaks, and carriage returns.
- innerText is considered to be nonstandard and browser-specific while textContent is implemented from the DOM specifications.

### Combine Sibling Text Nodes into One Text Node :

- normalize()

### Split a Text Node:

- splitText()


## Chapter8 : DocumentFragment Nodes

### Create DocumentFragments:

- createDocumentFragment()

### differences between createDocumentFragment() and createElement():

You might wonder what is the advantage to using a document fragment over simply creating (via createElement()) a `<div>` in memory and working within this `<div>` to create a DOM structure. Here are the differences between the two:
- A document fragment may contain any kind of node (except `<body>` or `<html>`),whereas an element may not.
- The document fragment itself is not added to the DOM when you append a fragment. The contents of the node are. This is in contrast to appending an element node in which the element itself is part of the append operation.
- When a document fragment is appended to the DOM, it transfers from the document fragment to the place where it is appended. It’s no longer in memory in the place you created it. This is not true for element nodes that are used to contain nodes only briefly and then are moved to the live DOM.

###  Leaving Fragments:

- cloneNode(true) : When appending a document fragment, the nodes contained in the fragment are moved from the fragment to the structure you are appending to.


## Chapter9 : CSS Stylesheets and CSS Rules

###  CSSStyleSheet Properties and Methods:

- disabled : readOnly
- href : readOnly
- media : readOnly
- ownerNode : readOnly
- parentStylesheet : readOnly
- title : readOnly
- type : readOnly
- cssRules
- ownerRule
- deleteRule : document.querySelector('#styleId').sheet.deleteRule(index)
- insertRule : document.querySelector('#styleId').sheet.insertRule('element{attr:value}',1)->1 is where you want set your style in array
- cssText
- parentRule
- parentStylesheet
- selectorText
- style
- type

## Chapter10 : JavaScript in the DOM 

### Defer the Downloading and Execution of External JavaScript :

Defer : that will defer the blocking, downloading, and execution of an external JavaScript file until the browser has parsed the closing `</html>` node.
According to the specification, deferred scripts are supposed to be executed in document order and before the DOMContentLoaded event.


### Asynchronously Download and Execute External JavaScript Files :

async : that will override the sequential blocking nature of `<script>` elements when the DOM is being constructed by a web browser.
async is a Boolean attribute; it does not have a value.


###  Force Asynchronous Downloading and Parsing of External JavaScript :

script : A known hack for forcing a web browser into asynchronous JavaScript downloading and parsing without using the async attribute is to programmatically create `<script>` elements that include external JavaScript files and insert them in the DOM.


## Chapter11 : DOM Events

