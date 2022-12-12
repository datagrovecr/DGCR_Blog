# 3 update about the markdown to PDF project

### Date submitted: 12/12/2022
### Developer: Raquel Abarca

## Project name: markdown to pdf
Project function: This project has the function to convert a markdown file into a PDF, for that, the markdown file is converted to HTML and the new HTML must be converted to PDF (this process is what I'm working on).

In this project, I have the task of transforming the HTML into a PDF file, the challenge here is that there is not exist a package that converts automatically the HTML to pdf (as the markdown to HTML) so I need to create a new code to make that the PDF show correctly all the information with the correct format and functions, to make this I need to use Dart, and different packages.

I work on the links, but here I get stuck because I wasn't able to print the URL text nor could I make it really work as a link because I didn't know how to link a URL to the word.

To solve this and make the links work, I had to use the following code:

<img width="486" alt="Screenshot 2022-12-12 at 13 55 49" src="https://user-images.githubusercontent.com/110420288/207141746-094fdacf-c3f1-4df3-a7cb-cb2039261071.png">

I want to explain this code, so to start, we create the class `_UrlText`, where we define all the information required, returned, and also the Style that we want, in this case, blue color, with an underline.

<img width="282" alt="Screenshot 2022-12-12 at 13 55 55" src="https://user-images.githubusercontent.com/110420288/207141836-701ec39b-2649-4731-9509-bd3c4016fa14.png">

Then, what I need here was to know where was the text that I need to print as a link, for this I used de debugger, and I see that in `e` there is a variable named as `innerHtml` that have the text that I need to be printed. But where is the link address? Well, using the same method, we find `attributes`, that has a map inside it, this map just had one element, our link address. 

<img width="252" alt="Screenshot 2022-12-12 at 13 56 01" src="https://user-images.githubusercontent.com/110420288/207141873-16a19cb1-9ad5-4f0a-a21b-3e6906051ed6.png">

After the link working right, I start with the codeblocks. For this I use the `pw.BoxDecoration` so I can give them a background color grey and a pretty rounded corners.

<img width="358" alt="Screenshot 2022-12-12 at 13 56 08" src="https://user-images.githubusercontent.com/110420288/207141895-6779857f-6b20-4e67-8e0d-d731fda892ad.png">

Resources I found helpful:
- https://www.w3schools.com/html/tryit.asp?filename=tryhtml_formatting_codepre

Tags: `Dart` `HTML` `Markdown` `PDF` `Packages` `Widgets` `code` `UrlLinks` `debugger`
