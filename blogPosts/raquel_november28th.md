# Update of the markdown to PDF feature

##### Date: 11/28/2022
##### Developer: Raquel Abarca Espinoza

## Project name: Markdown to PDF

This project has the function to convert a markdown file into a PDF, for that, the markdown file is converted to HTML and the new HTML must be converted to PDF (this process is what I'm working on).

In this project, I have the task of transforming the HTML into a PDF file, the challenge here is that there is not exist a package that automatically converts the HTML to pdf (as the markdown to HTML) so I need to create a new code to make that the PDF show correctly all the information with the correct format and functions, to make this I need to use Dart, and different packages.

Since the last blog I have worked on different things, the first of all was the unordered list, 
To make this possible I use the `pw.Bullet` widget, and then I add the text. 
This is the code:

```
case "li":
            return Chunk(widget: [pw.Bullet(), ...widgetChildren(e, Style())]);
```

But the problem was that it look like this:

<img width="208" alt="Screenshot 2022-12-01 at 12 53 04" src="https://user-images.githubusercontent.com/110420288/205136578-ca16a517-7f3d-493d-9a61-d92b037af7db.png">

A problem that happens because why are using block-level elements instead of using inline elements. this causes the text to appear on the bottom line and not be continuous. Jim is searching for a solution, I hope that for the next blog post I have it.

I also worked on the italic text, I had problems with this one because the HTML did not show any different tag for this type of word, so I had to add an extension called `ExtensionSet.gitHubWeb`, I added it at the end of the file, where the markdown is converting to HTML

<img width="615" alt="Screenshot 2022-12-01 at 12 53 13" src="https://user-images.githubusercontent.com/110420288/205136529-62d04919-9406-498f-8066-7dd9ea51f872.png">

Then, I added the widget `pw.FontStyle.italic` following the process that I explain in my [previous blog](). So the code look like this:

```
case "em":
            return Chunk(
                text: inlineChildren(e, Style(fontStyle: pw.FontStyle.italic)));
```

I also work on the line through, an easy code if you follow the steps from before, add the widget and create the case. But the problem with this was that the line was red

<img width="81" alt="Screenshot 2022-12-01 at 12 53 20" src="https://user-images.githubusercontent.com/110420288/205136627-5e5b1eff-ce1f-4526-afe2-eae00f9ded5b.png">

To solve that I followed these three steps:

So it was three steps:

1. Edit inlineChildren to be able to accept an optional third parameter

2. Add null check to inlineChildren so if the optional parameter had something in it it would add the second style to the style list

3. Add a second style to the case "del":
```
case "del":  
  return Chunk(
    text: inlineChildren(e, Style(color: PdfColors.black), Style(textDecoration: pw.TextDecoration.lineThrough)));
```


### Resources that I find:
https://github.com/DavBfr/dart_pdf/blob/44395ee11753d96e8e90e1f97475811e95e23e13/pdf/lib/src/widgets/basic.dart
https://davbfr.github.io/dart_pdf/#/
https://pub.dev/documentation/pdf/latest/widgets/Divider-class.html
https://dart.dev/guides/packages
https://pub.dev/documentation/markdown/latest/index.html
