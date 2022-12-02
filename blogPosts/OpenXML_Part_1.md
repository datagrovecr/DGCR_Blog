# Understanding OpenXML SDK

My feature is about an SDK that will help to translate a .md file to the popular .docx format. This has been mostly achieved with the help of the popular
package "Markdig" which helps to translate markdown to html and the "HtmlToDocx" package that is in charge of translate the new html file to the final 
result in docx format.
Now, sounds like everything is done, but the complex part here is return to .md format from a .docx file, and that's what I'm working on and why I needed to learn the use of the OpenXML SDK.

## What's XML?

Likely Html, XML is a markup language that will help us to store and transport data in a readable way

We can see it works in a tree structure, this is really important to understand and code it then. There are elements that contains elements
```
<root>
  <child>
    <subchild>.....</subchild>
  </child>
</root>
```
And there are other elements that contains text, like <title> or <author>
```  
<book category="children">
    <title>Learning XML</title>
    <author>Fabian Valverde</author>
</book>
```
We can also see that those elements can contains attributes that will be probably used by the text editor to give the desired format to the document, so in that case you'll find properties used for MSWord to give color to a table border as you can see in the following example
```
< w:tblBorders >
  < w:left w:val = "single" w: sz = "4" w: space = "0" w: color = "000000" w: themeColor = "text1" />
  < w:right w:val = "single" w: sz = "4" w: space = "0" w: color = "000000" w: themeColor = "text1" />
</ w:tblBorders >
```

## OpenXML SDK 

OpenXML is a set of methods that wants to simplify the manipulation of documents in format .docx. Briefly, we can open documents to edit them, create new document and format them or delete documents, everything having completely control of the XML Structure.

### Manipulation of the structure
The way to edit a new document is creating the basic XML structure using the classes provided by the SDK as Document, Body, Paragraph, Run and Text. As was mentioned, XML works as a tree structure, so what we need to understand is we need to append the child tag to the parent tag using the append method
```
<parent>
   <child>…</child>
</parent>
```
Seeing the previous structure we can say that the way to construct it is doing the following: *parent.AppendChild(“child”);*
### Manipulation of the attributes

For this, we only need to understand that we’re not exactly creating an XML document to our own editor, what we’re doing with this SDK is create or open an existing .docx document, providing the necessary tools that the docx editor needs to understand it, so every attribute in every tag is predefined and we only need to understand why the editor application need it and how it works.
To manipulate an attribute is as easy to see them as what they are, variables.
Following we can see the XML structure
```
< w:tblBorders >
  < w:left w:val = "single" w: sz = "4" w: space = "0" w: color = "000000" w: themeColor = "text1" />
</ w:tblBorders >
```
Now we’ll see the code to build the previous XML
```
var tblBorder = new TableBorders();

var leftBorder = new LeftBorder();
leftBorder.Val = new EnumValue<BorderValues>(BorderValues.Thick);
leftBorder.Size = 8;
leftBorder.Color = borderColor;
```
As you can see, everything we are doing is to create a new LeftBorder class, giving to his variables a new value, and then, seeing the structure we could know that LeftBorder in the Child of TableBorder, so everything we need is to append the LeftBorder class to the TableBorders class as following: *tblBorder.AppendChild(leftBorder);*

## My feature task

For my feature task what I’m doing is translating an .md document to .docx and vice versa, using an SDK named Markdig to translate markdown to html, and then, other SDK to translate html to .docx format named HtmlToDocx. There are just 2 issues by the moment:

- Tables aren’t being displayed well. I can set a size for those tables but can’t size them automatically depending on the text inside them.
- I can’t read new lines in many parts of the document, for example lists, and what happens is when I’m translating from .docx, every list line in .md will be separated by an space, and it’s because of the way the SDK read the document, something a little bit complex and extend to explain.
 
I’ve been working my feature using all the previous knowledge in order to understand behaviors that doesn’t make sense, and fix them while I need to translate .md to docx, or understand that I need to look for specific variables and where can I find them while I’m looping the document in order to reconstruct the .md file, and based on my experience what could I recommend you if you need to work with this SDK? Well, the best you can do is work on understand deeply what you’re doing and learn how to read the documentation, something that could be the most important thing to move forward in your code.

I’ll give you here a briefly tour around the SDK documentation:

#### Here you can find a summary about what the class does and where it should be placed, you can check which should be the parent and possible childs.
<img width="1111" alt="Summary Class" src="https://user-images.githubusercontent.com/110683318/194801696-34ad1079-9da0-403a-bfcc-cb35528b82ee.png">

#### Here you can find constructors, to know what you can declare when you’re creating a new instance.
<img width="725" alt="Constructors" src="https://user-images.githubusercontent.com/110683318/194801813-32f34052-ec37-4d6a-bf3d-0a2152c79f61.png">

#### Here you can find properties, what we call variables of the class.
<img width="720" alt="Properties" src="https://user-images.githubusercontent.com/110683318/194801833-f7146d00-5d82-4588-86ce-ecd9957939d1.png">

#### Here you can find every method you can use, the most usual is the Append() method.
<img width="720" alt="Methods" src="https://user-images.githubusercontent.com/110683318/194801852-21fed7a5-8a45-4a7f-b827-cebd6c161201.png">

#### Also, you can see lot of examples an good tutorials here in order to start your learning path of this SDK!
<img width="1151" alt="Getting started" src="https://user-images.githubusercontent.com/110683318/194803039-bd37170c-8336-441a-b637-934eadc8b3ac.png">

##Last recommendations
Already mentioned all that, my last advice is learn reading the way word creates their documents opening those files in XML format. Doing that is quite simple, we can use the following commands to decompress the .docx file and see what's inside it
```
cd path/to/your/file.docx
unzip file.docx -d file-content
```
And it should look like this
```
fabianvalverde@Fabians-MacBook-Pro ~ % cd Documents/StudyOpenXml/
fabianvalverde@Fabians-MacBook-Pro StudyOpenXml % unzip SampleFile.docx -d file-content
Archive:  SampleFile.docx
  inflating: file-content/word/document.xml  
 extracting: file-content/_rels/.rels  
 extracting: file-content/[Content_Types].xml 
```
#### Then it's just as simple as drag and drop the XML file to your favorite browser!
<img width="1512" alt="XMLBrowser" src="https://user-images.githubusercontent.com/110683318/194930503-ab01c94a-a49f-41ba-8131-094095a1ae29.png">

#### If your XML file need permissions you have to open the Get Info window and change the permissions of the file
<img width="1216" alt="Permissions" src="https://user-images.githubusercontent.com/110683318/194933211-fdd10da9-f271-4f09-92b7-8d75eb9f9f8a.png">

Then you're completely ready to read the file and learn or try new ways to work with your documents!
