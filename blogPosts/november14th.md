# Widgets for the markdown to pdf

##### Date: 11/14/2022
##### Developer: Raquel Abarca Espinoza

## Project name: Markdown to pdf 
This project has the function to convert a markdown file into a PDF, for that, the markdown file is converted to HTML and the new HTML must be converted to PDF (this process is what I'm working on).

In this project, I have the task of transforming the HTML into a PDF file, the challenge here is that there is not exist a package that converts automatically the HTML to pdf (as the markdown to HTML) so I need to create a new code to make that the PDF show correctly all the information with the correct format and functions, to make this I need to use Dart, and different packages.

One of that packages is the `package:pdf/widgets.dart`, which has widgets that would help me to add the correct formatting to the pdf.

Using them is very easy and very complex at the same time.

In my code, you can see them with the `pw.` before them, for example in line 170,172,179 and 182.

<img width="619" alt="Screenshot 2022-12-01 at 11 54 07" src="https://user-images.githubusercontent.com/110420288/205125507-b61113a5-84ae-400f-a3d9-2adc7e1d19d8.png">

I said that they are easy to use because to add one you only have to add it in the class Style (line 31). We are going to use as an example the widget for Text Decoration (I use it to give the strikethrough format), In line 38 you can see how we add the `pw.TextDecotation` to create a type, then in line 45 I add the `this.textDecoration` and also in line 53 we add the `textDecoration` as `s.textDecoration`, and in line 63 that I add `decoration: textdecoration`. All of that will make it possible to add it in the Style (like in line 189)

<img width="618" alt="Screenshot 2022-12-01 at 11 54 19" src="https://user-images.githubusercontent.com/110420288/205125612-36400a1d-8ae4-4d7a-b283-4b8d8003ae2a.png">

It has been all a challenge because as I said before it is not that simple, every widget has its own way to work, as you can see in the first image the code for the `case “a”` (that is links) isn’t the same as the `case “Strong”`.

Here is a Screenshot of how the program uses the three types of file (markdown, HTML, PDF):

<img width="753" alt="Screenshot 2022-12-01 at 11 54 27" src="https://user-images.githubusercontent.com/110420288/205125669-2dcb9ba1-de8a-4010-8f69-ce5212aa935d.png">

Also, I want to share my favorite part of this code, which is the code where I add the specifications for the h1, h2, h3, h4, h5 and h6, I think it was the most exciting part when I saw that it works.


Sample code you'd like to highlight:

```
case "h1":
            return Chunk(
                widget: widgetChildren(
                    e, Style(weight: pw.FontWeight.bold, height: 24)));
          case "h2":
            return Chunk(
                widget: widgetChildren(
                    e, Style(weight: pw.FontWeight.bold, height: 22)));
          case "h3":
            return Chunk(
                widget: widgetChildren(
                    e, Style(weight: pw.FontWeight.bold, height: 20)));
          case "h4":
            return Chunk(
                widget: widgetChildren(
                    e, Style(weight: pw.FontWeight.bold, height: 18)));
          case "h5":
            return Chunk(
                widget: widgetChildren(
                    e, Style(weight: pw.FontWeight.bold, height: 16)));
          case "h6":
            return Chunk(
                widget: widgetChildren(
                    e, Style(weight: pw.FontWeight.bold, height: 14)));
```

## Resources that I found helpful:

https://github.com/datagrovecr/markdown_to_pdf
https://github.com/datagrovecr/MarkdownToPDF
https://github.com/DavBfr/dart_pdf/blob/master/demo/lib/examples/resume.dart

Documentation:
https://pub.dev/documentation/pdf/latest/widgets/widgets-library.html 

List of tags: `Dart` `HTML` `Markdown` `PDF` `Packages` `Widgets` `code`

