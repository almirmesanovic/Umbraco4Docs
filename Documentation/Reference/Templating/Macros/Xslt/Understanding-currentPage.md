#Understanding "currentPage"

As mentioned on the previous page, the currentPage parameter is important for us in Umbraco.  It is the complete XML document of the published site, and is how we reference the data stored in each document.  By default, the context of the XML document is set to the requested page.

In XSLT, to reference a parameter or a variable, we prefix the name of the variable/parameter with a $-sign, thus `$currentPage`.  However, before we use this parameter, we need to know what is in the XML document, and how to reference the content.

XML is referenced in XSLT through the use of XPath, a query syntax that resembles that of a file system. Since XML has the ability to contain various levels of information, XPath has means to traverse these levels, and retrieve data based upon the current context.  But again, before we can use XPath, we must know what is in the XML document.

The XML document contains all the content of the published documents. This data is stored in the XML document structured in the same manner as your tree is laid out in Umbraco. So, documents are nested to create the hierarchy that we can easily use. Each document in Umbraco consists of several common pieces of data, and they are:

* `id` (integer)
* `parentID` (integer)
* `level` (integer)
* `writerID` (integer)
* `creatorID` (integer)
* `nodeType` (integer)
* `template` (integer)
* `sortOrder` (integer)
* `createDate` (datetime)
* `updateDate` (datetime)
* `nodeName` (text)
* `urlName` (text)
* `writerName` (integer)
* `creatorName` (integer)
* `path` (CSV of integers)
* `isDoc` (empty)

These are stored as attributes of the node, which is named after the Document Type alias, e.g. `<Textpage>`. The properties that are added to the document in Umbraco which are editable, are added as childnodes, so a single document could look like this:

	<Textpage
		id="1312"
		parentID="1120"
		level="3"
		writerID="0"
		creatorID="3"
		nodeType="1118"
		template="1047"
		sortOrder="2"
		createDate="2005-02-16T10:00:00"
		updateDate="2006-02-16T12:00:00"
		nodeName="About us"
		urlName="about-us"
		writerName="Administrator"
		creatorName="Administrator"
		path="-1,1051,1120,1312"
		isDoc=""
	> 
		<!-- Property nodes -->
		<header><![CDATA[My ]]></header>
		<umbracoNaviHide><![CDATA[1]]></umbracoNaviHide>

		<!-- Child pages/documents -->
		
	</Textpage>
	
The `isDoc` attribute is a little special, in that is is always empty and simply works as a *flag* that says "this is a document node" - remember that the name of the node can be any valid XML name, so you need some way of distinguishing documents from their properties. This attribute lets you do just that.


	
	