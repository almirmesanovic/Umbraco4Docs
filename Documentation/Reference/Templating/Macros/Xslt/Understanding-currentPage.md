#Understanding "currentPage"

As mentioned on the previous page, the currentPage parameter is important for us in Umbraco.  It is the complete XML document of the published site, and is how we reference the data stored in each document.  By default, the context of the XML document is set to the requested page.

In XSLT, to reference a parameter or a variable, we prefix the name of the variable/parameter with a $-sign, thus `$currentPage`.  However, before we use this parameter, we need to know what is in the XML document, and how to reference the content.

XML is referenced in XSLT through the use of XPath, a query syntax that resembles that of a file system. Since XML has the ability to contain various levels of information, XPath has means to traverse these levels, and retrieve data based upon the current context.  But again, before we can use XPath, we must know what is in the XML document.

The XML document contains all the content of the published documents. This data is stored in the XML document structured in the same manner as your tree is laid out in Umbraco. So, documents are nested to create the hierarchy that we can easily use. Each document in Umbraco consists of several common pieces of data, and they are:

- id
- isDoc
- version
- parentID
- level
- writerID
- creatorID
- nodeType
- template
- sortOrder
- createDate
- updateDate
- nodeName
- urlName
- writerName
- creatorName
- path

These are stored as attributes of the node, which is named after the Document Type alias, e.g. `<Textpage>`. The properties that are added to the document in Umbraco which are editable, are added as childnodes, so a single document would look like this:

	<Textpage
		isDoc=""
		id="numeric-version"
		version="guid-value"
		parentID="numeric-value"
		level="numeric-value"
		writerID="numeric-value"
		creatorID="numeric-value"
		nodeType="numeric-value"
		template="numeric-value"
		sortOrder="numeric-value"
		createDate="datetime-value"
		updateDate="datetime-value"
		nodeName="text-value"	
		urlName="text-value"
		writerName="text-value"
		creatorName="text-value"
		path="csv-numeric-value"
	> 
		<header><![CDATA[]]></header>
		<umbracoNaviHide><![CDATA[1]]></umbracoNaviHide>
		
	</Textpage>
	
The `isDoc` attribute is a little special, in that is is always empty and simply works as a *flag* that says "this is a document node" - remember that the name of the node can be any valid XML name, so you need some way of distinguishing documents from their properties. This attribute lets you do just that.


	
	