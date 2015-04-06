# phpdomxml-0.9.0 Quick Docs #

This project is my tiny contribution to the open source community. phpdomxml is an OOP implementation of the XML DOM for PHP. It tries not to be a 100% complete implementation of the nifty w3c standards. In fact, its aim is to be a light-weight implementation for 'every-day' usage of XML-documents in a PHP 4.10+ environment. phpdomxml does not rely on any external libraries, it does however require the expat XML parser functions for PHP, which should be included by default.

The methods and properties follow the design as layed out by the World Wide Web Consorticum and as was implemented in ECMAScript or compatible languages like Javascript and Actionscript. phpdomxml does not support validating by DTD through the document type definition. The document type is recorded when reading an XML document, but not used.
Implementation

This project started out as a necassity for an OOP implementation of the XML DOM for PHP. A few months ago PHP 5.0 was released and, though I didn't find the time to look under the hood, it seems to have a very solid implementation of the DOM. Since it will take some time for hosting providers to make the switch from PHP 4.x to PHP 5.0, it seemed like a good idea to release this work to the open source community.

There are some beautiful implementations of the XML DOM for PHP out there. I, however, took the liberty of making some shortcuts by treating some of the objects as simple (associative) PHP arrays. For instance, the Attr and NamedNodeMap interfaces are dropped and the attributes of an element can be addressed by using the attributes array of an XML\_Node interface, or by using the DOM-compliant XML\_Element::getAttribute().

The following interfaces are not implemented in phpdomxml: Attr, DocumentFragment, DocumentType, DOMImplementation, Entity, EntityReference, NamedNodeMap, NodeList, Notation and ProcessingInstruction.
Interfaces

The list below specifies interfaces and their methods and properties. Elements denoted in red are w3c standards that are implemented in phpdomxml-0.9.0. Elements denoted in green are extensions to the standard.

  * XML\_CDATASection (spec)
> > Inherits the XML\_CharacterData interface through the XML\_Text interface.

  * XML\_CharacterData (spec)
> > The XML\_CharacterData interface extends XML\_Node with a set of attributes and methods for accessing character data in the DOM.


> Properties
> > o data
> > o length


> Methods
> > o appendData (example) (spec)
> > > Append the string to the end of the character data of the node.

> > o deleteData (example) (spec)
> > > Deletes specified data.

> > o insertData (example) (spec)
> > > Insert a string at the specified offset.

> > o replaceData (example) (spec)
> > > Replace the characters starting at the specified offset with the specified string.

> > o substringData (example) (spec)
> > > Extracts a range of data from the node.

  * XML\_Comment (spec)

> > From this object are accessible comments in XML, i.e. all characters between "<!--" and "-->". Extends XML\_CharacterData.

  * XML\_Document (spec)
> > The Document interface represents the entire XML document. Conceptually, it is the root of the document tree, and provides the primary access to the document's data. Extends XML\_Node.


> Properties
> > o docType
> > o documentElement
> > o implementation


> Methods
> > o createAttribute
> > o createAttributeNS
> > o createCDATASection (spec)
> > > Creates a CDATASection node whose value is the specified string.

> > o createComment (example) (spec)
> > > Creates a Comment node given the specified string.

> > o createDocumentFragment
> > o createElement (example) (spec)
> > > Creates an element of the type specified. Note that the instance returned implements the Element interface, so attributes can be specified directly on the returned object.

> > o createElementNS
> > o createEntityReference
> > o createProcessingInstruction
> > o createTextNode (example) (spec)
> > > Creates a Text node given the specified string.

> > o getElementById (example) (spec)
> > > Returns the Element whose ID is given by elementId. If no such element exists, returns null.

> > o getElementsByTagName (example) (spec)
> > > Returns an array containing all Elements of the given name in the same order as they appear in the source document.

> > o getElementsByTagNameNS
> > o importNode

  * XML\_Element (spec)
> > Apart from text, XML\_Element nodes are the most common objects in every XML document. Extends XML\_Node.


> Properties
> > o tagName
> > > The name of the element.


> Methods
> > o getAttribute (spec)
> > > Retrieves an attribute value by name.

> > o getAttributeNode
> > o getAttributeNodeNS
> > o getAttributeNS
> > o getElementById
> > > Return element with specified attribute 'id' set or null if none found.

> > o getElementsByTagName (spec)
> > > Returns an array containing all Elements with the given tag name in the same order as they appear in the source document.

> > o getElementsByTagNameNS
> > o hasAttribute (spec)
> > > Returns true when an attribute with a given name is specified on this element, false otherwise.

> > o hasAttributeNS
> > o removeAttribute (spec)
> > > Removes an attribute by name.

> > o removeAttributeNode
> > o removeAttributeNS
> > o setAttribute (example) (spec)
> > > Adds a new attribute, or changes an existing one.

> > o setAttributeNode
> > o setAttributeNodeNS
> > o setAttributeNS

  * XML\_Node (spec)
> > The Node interface is the primary datatype for the entire Document Object Model. It represents a single node in the document tree.


> Properties
> > o attributes
> > > An array containing the attributes of this node (if it is an Element) or null otherwise.

> > o childNodes
> > > An array that contains all children of this node.

> > o firstChild (example)
> > > The first child of this node. If there is no such node, this returns null.

> > o lastChild (example)
> > > The last child of this node. If there is no such node, this returns null.

> > o localName
> > o namespaceURI
> > o nextSibling (example)
> > > The node immediately following this node. If there is no such node, this returns null.

> > o nodeName (example)
> > > The name of this node.

> > o nodeType
> > > A code representing the type of the underlying object
> > > - XML\_ELEMENT\_NODE = 1
> > > - XML\_TEXT\_NODE = 3
> > > - XML\_CDATA\_SECTION\_NODE = 4
> > > - XML\_COMMENT\_NODE = 8
> > > - XML\_DOCUMENT\_NODE = 9

> > o nodeValue (example)
> > > The value of this node.

> > o ownerDocument
> > > The Document object associated with this node. This is also the Document object used to create new nodes.

> > o parentNode
> > > The parent of this node. All nodes, except XML\_Document may have a parent. However, if a node has just been created and not yet added to the tree, or if it has been removed from the tree, this is null.

> > o prefix
> > o previousSibling (example)
> > > The node immediately preceding this node. If there is no such node, this returns null.


> Methods
> > o appendChild (example) (spec)
> > > Adds a new child to the end of the list of children of this node. If the new child is already in the tree, it is first removed.

> > o cloneNode
> > o hasAttributes (spec)
> > > Returns whether this node (if it is an element) has any attributes.

> > o hasChildNodes (spec)
> > > Returns whether this node has any children.

> > o insertBefore (spec)
> > > Inserts a new child before an existing child node (refChild). If refChild is null, the new child is added at the end of the list of children.

> > o isSupported
> > o normalize
> > o removeChild (example) (spec)
> > > Removes the indicated child node from the list of children, and returns it.

> > o replaceChild

  * XML\_Text (spec)
> > The XML\_Text interface inherits from XML\_CharacterData and represents the textual content (termed character data in XML) of an Element.


> Methods
> > o splitText
  * XML
> > The XML object inherits from XML\_Document and serves as access point for your XML needs in projects..


> Methods
> > o load
> > > Load an XML document from the specified URL.

> > o save
> > > Save an XML document to the specified file or URL.

> > o parseXML
> > > Parses the XML text in the specified argument.

> > o send
> > > Encodes the specified XML object into an XML document and sends it to the specified URL using the POST method.

> > o sendAndLoad
> > > Encodes the specified XML object into an XML document, sends it to a specified URL using the POST method, downloads the server's response and then loads it into a given target object.

  * XML\_Parser

> > The XML\_Parser parses an XML document into a DOM object.


> Methods
> > o parse
> > > Parse a raw XML document.