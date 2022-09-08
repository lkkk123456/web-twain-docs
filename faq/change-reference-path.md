---
layout: default-layout
noTitleIndex: true
needAutoGenerateSidebar: true
title: How can I change the reference path to the Dynamsoft’s resources in my project?
keywords: Dynamic Web TWAIN, Project Deployment and End-user Installation, reference path
breadcrumbText: How can I change the reference path to the Dynamsoft’s resources in my project?
description: How can I change the reference path to the Dynamsoft’s resources in my project?
permalink: /faq/change-reference-path.html
---

# Project Deployment and End-user Installation

## How can I change the reference path to the Dynamsoft’s resources in my project?

<strong>Scenario: </strong> For customers who are using Dynamic Web TWAIN, to change the location of the 'Resources' folder, or to rename it, please following the steps below:

<strong>Steps:</strong> In the below example we will assume the original Resources folder is located at '<strong>../{Project Directory}/Resources</strong>', and you want to change it to '<strong>../{Project Directory}/Newfolder/ResourcesTest</strong>'.

1. Please make sure the structure inside 'Resources' folder stay unchanged.
2. Change the relative path in your page where you reference the js files, for example:

```javascript
<script src="Resources/dynamsoft.webtwain.initiate.js"></script>
// or your own operation js file
<script src="Scripts/DWTSample_BasicScan.js"></script>
<script src="Resources/dynamsoft.webtwain.config.js"></script>
```

Modify as below:

```javascript
<script src="Newfolder/ResourcesTest/dynamsoft.webtwain.initiate.js"></script>
// or your own operation js file
<script src="Scripts/DWTSample_BasicScan.js"></script>
<script src="Newfolder/ResourcesTest/dynamsoft.webtwain.config.js"></script>
```

3. The same change needs to be done in dynamsoft.webtwain.config.js file. Add/uncomment the following line, then change 'Resources' (to 'New folder/ResourcesTest' as in this case):

```javascript
Dynamsoft.DWT.ResourcesPath = "Resources";
```

Modify as below:

```javascript
Dynamsoft.DWT.ResourcesPath = "Newfolder/ResourcesTest";
```

### Setting ResourcePath in Main Page JavaScript tag

You can also set `ResourcesPath` in the JavaScript tag:

```javascript
<script type="text/javascript"> Dynamsoft.DWT.ResourcesPath = "Newfolder/Resources";</script>
```
or

```javascript
<script type="text/javascript"> Dynamsoft.DWT.ResourcesPath = "https://www.dynamsoft.com/dwt/demo/resources";</script>
```

The complete code has shown as below. (change the path to your own path instead)

```
<html>
	
<head>
	    <title>Hello World</title>
	    <script src="Newfolder/Resources/dynamsoft.webtwain.initiate.js"></script>
	    <script src="Newfolder/Resources/dynamsoft.webtwain.config.js"></script>
	</head>
	
	<body>
	    <input type="button" value="Scan" onclick="AcquireImage();" />
	    <div id="dwtcontrolContainer"></div>
	
	    <script type="text/javascript">
	        Dynamsoft.DWT.ResourcesPath = 'Newfolder/Resources';
          var DWObject;
	        function Dynamsoft_OnReady() {
	            DWObject = Dynamsoft.DWT.GetWebTwain('dwtcontrolContainer');
	        }
	
		function AcquireImage() {
		   if (DWObject) {
			    DWObject.SelectSource(
				function() {
				    DWObject.OpenSource();
				    DWObject.AcquireImage();
				},
				function() {
				    console.log("SelectSource failed!");
				});
		       }
		   }
	    </script>
	</body>
	
	</html>

```
