Java XML Helper Utilities is a set of utilites written in Java that can help you manipulate, edit or extract XML attributes..

Here a a couple of examples against the XML Payload below:

**Example 1 - Modify the multiple items using a TreeMap.**
		long newTime = System.currentTime();
		String xmlPayLoad = readFileAsString(payLoadPath + "/payLoad.xml");
		TreeMap<String, String> header = new TreeMap<String, String>();
		XPathHelperCommon xph = new XPathHelperCommon();
		header = xph.findMultipleXMLItems(xmlPayLoad, "//header/*");
		header.put("type", "newProcess");
		newTime += Long.parseLong(header.get("taskElapsedTime"));
		header.put("taskElapsedTime", Long.toString(newTime));
		xmlPayLoad = xph.modifyMultipleXMLItems(xmlPayLoad, "//header/*", header);
.

**Example 2 - Modify a single attribute**
		long notAfter = System.currentime();
		itemPath = "//payload/joinAttribute/notAfter/text()";
		xmlpayLoad = XPathHelper.modifyXMLItem(xmlpayLoad, itemPath, Long.toString(notAfter));
    

**XML Payload**

	<header>
		<type>process</type>
		<ruleBaseVersion>0</ruleBaseVersion>
		<ruleBaseCommitment>0</ruleBaseCommitment>
		<sequenceId>0</sequenceId>
		<priortiseSID>0</priortiseSID>
		<monitorIncomingEvents>0</monitorIncomingEvents>
		<activityCount>0</activityCount>
		<taskElapsedTime>0</taskElapsedTime>
		<processStartTime>0</processStartTime>
		<processElapsedTime>0</processElapsedTime>
		<eventElapsedTime>0</eventElapsedTime>
		<status>0</status>
	</header>

	<joinAttribute>
		<attributeName>0</attributeName>
		<attributeValue>0</attributeValue>
		<notBefore>0</notBefore>
		<notAfter>0</notAfter>
	</joinAttribute>

	<service>
		<serviceName>null</serviceName>
		<operation>null</operation>
	</service>
	
	<canonicalData>
		<processStartTime>null</processStartTime>
		<processCompleteTime>null</processCompleteTime>
	</canonicalData>
</payload>



