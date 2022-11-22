# What are Regular Expressions?

A regular expression, best known as "RegEx", is just a sequence of character to build a pattern that will help us to look for matches in a text and then, extract, replace or validate something according to the pattern built before. 
This is something useful for those cases where we need for example extract characters, something that we did in the package to translate Markdown to .docx, package that first needs to translate markdown to html, and then, processing every html tag in the package we have the possibility to stylize the paragraphs according to the tag that wraps it. Those html tags sometimes have a lot of attributes that could complicate the code when it's needed to validate them, that's the moment where ReGex appears and help us to simplify it extracting just what we need to check in that tag.
Below you can see two Regular Expression I built for that package.
```
            Regex tagCheck = new Regex(@"^<\/?[a-z]+[1-6]?\s?.*?\/?>$");
```
So, with the previous regular expression I could extract, for example, the tag **\<div>** from **\<div width="500" height="600">** so I can compare only what I needed.
#How to write and understand a Regular Expression
Write regular expressions isn’t something complex at all, the only thing you need to understand is the meaning of every Regular Expression and just experiment with them building a pattern.
The following link (https://regex101.com/) is really helpful to test every Regular Expression we’ll write before set them into our code, so let’s see very quickly how to use it!

####	To write our regular expression we will need to type in the Regular Expression input box<br>
 ![Expression](https://user-images.githubusercontent.com/110683318/202988813-625cd96f-a666-4ef0-b11d-2ec5ff153305.png)

####	The text that will be matched have to be typed in the Test String input box<br>
![TestText](https://user-images.githubusercontent.com/110683318/202988865-fa7ae9be-7eb5-4986-8af4-4817eb0f994e.png)

####	In the left side we’ll find the Regex Debugger, something that will help us to see how’s the regex flow when it’s trying to match something in our text.<br>
![Debugger](https://user-images.githubusercontent.com/110683318/202989050-7cc62f67-08a8-45eb-acbe-2cb32fea9282.png)

####	And in the right part we can see the Match Information box to see every match for the regular expression typed. <br>
![matchInformation](https://user-images.githubusercontent.com/110683318/202988991-d9279ab8-eaf9-4a0f-8231-e1dc47c4176e.png)


This web page will help you to check every regular expression and also try to understand how each one works doing your own examples!

To continue, here you can find a link to download a document that will help you to build your own expression, download it and let’s move forward:
https://download.microsoft.com/download/D/2/4/D240EBF6-A9BA-4E4F-A63F-AEB6DA0B921C/Regular%20expressions%20quick%20reference.pdf

Well, probably after seeing all those characters you felt overwhelmed, and I understand that because it’s a lot and quite random, so I’ll try to make sense what I consider the most important information there and what I used for the package. For the example part, you can see what was matched in bold. <br>


#### Single Characters:<br>
These regular expression looks to match just a character one by one and not as a String. As you could see, you can choose to match only one character, any of them with a dot, or a set of characters to wrapping them between square brackets.<br>

|Example|
|---|
|Testing string: We will try to match the character z and every.|
|Testing pattern: [az] (or just a character completely alone, play with it)|
|Testing result: We will try to m*a*tch the ch**a**r**a**cter **z** **a**nd every.|<br>

#### Control Characters:<br>
As you could guess, this will allow you to match tabs, spaces, new lines and all those expressions that usually works to make the document readable.

|Example|
|---|
|Testing string: 1.Example2  2.There’s implicitly a \t exactly after Example2 3.We are testing the last 3 character before a new line 123 |
|Testing Pattern: .{3}\t|
|Testing result: 1.Example2  2.There’s implicitly a \t exactly after Example2  3.We are testing the last 3 character before a new line 123  |<br>

#### Quantifiers:<br>
These expressions will help you to quantify the number of characters that will match.

|Example|
|---|
|Testing string: We’d like to match if there’s a number 1 or more times, could be 23 times.|
|Testing Pattern:[0-9]+ (also this one works: \d+)|
|Testing result: We’d like to match if there’s a number **1** or more times, could be **23** times. (Try it without the quantifier and check the the Match Information box to see how works)|<br>

#### Anchors:<br>
This will help you to define the position where will start to match your pattern.

|Example|
|---|
|Testing string: abc following text isn't the start of the string abc|
|Testing Pattern: (.+)(@.+\.com)|
|Testing result:**abc** following text isn't the start of the string abc|<br> 

#### Alternation:<br>
This will help you to give alternatives to match using the operator “OR” 

|Example|
|---|
|Testing string: Will be a match if before 3 numbers there's a "g" or "f", like this f123 or g123|
|Testing Pattern: (g|f)[0-9]{3}|
|Testing result: Will be a match if before 3 numbers there's a "g" or "f", like this **f123** or **g123**|

#### Groups:<br>
This is quite simple, just helps to have subexpressions in the pattern, so you can look for a match normaly, but then, you could have other expression inside a parenthesis to separate them and even could have a quantifier to look for many matches along the string.

|Example|
|---|
|Testing string: regular expressions.|
|Testing Pattern: .{7}(si)+|
|Testing result: **regular** expres**si**ons.|

# Principal uses

### Extract
As we mentioned in the introduction, Regular Expressions are useful for those cases where we need to look for a word or a specific group of characters into a String avoiding what we don’t need, and extract what we really want. The method Regex.Match(string input, string pattern) will return matches.
### Replace
As we can extract the useful information, with the right method we could replace what we matched. For example, in C# that method is Regex.Replace(string input, string pattern, string replacement).
### Validate
To do a validation we only need to check if there’s a match with Regex.Match(string input, string pattern).
Of course, every language has their own methods and classes, but regular expressions are the same

# Dangers of using Regex (Evil Regex)
ReGex is an useful tool, I think there's no doubt about it, but there's an important disadvange and I'm not talking about the bad readability it has and all the sacrifice we have to take to only understand a little what could be the functionality of a expression, I'm talking about a concept called ReDoS (Regular Expressions Denial of Service). ReDoS is a Denial of Service atack that takes advantage of the ReGex flow for some expressions (specially for those that includes quantifiers regular expressions) leading to a very long matching process. 

Investigating about it, seems that for expression like the following **^(a+)+$** will force a match if it's needed (if there's not a match), trying every posible combination.

You could ask youself, what combinations if there are a lot of a's? Just go to the web page https://regex101.com/ put the regular expression from above and test the following string "aaax", then just debbug it.

Did you see how it's coming and coming back? It's trying new combinations using a feature called backtraking, that will store previous matches and will go back to try other ways to force a match. In this case, this feature is present for those nested quantifiers expressions.

To understand what I mean when I say that there are many paths just see the next picture

![Backtracking](https://user-images.githubusercontent.com/110683318/203249819-4e3dbae6-7e4f-42ae-ba76-177814d59dc6.png)

As you can see, we have a 3 a's matching because of the expression "a+" (that's why everything is in color red like the "a+" expression) but then we see that there could be other option, and it's the expression "a+" matching 2 a's and the nested + quantifier out the parenthesis matching the remaining a, and we can also see how the nested + quantifier out the parenthesis match all those 3 a's at the end. Now, just imagine what could happen if wasn't just 3 characters but only 16 of them, only for 16 there are 65536 possible paths.

Having said all that, it's important to mention that those attacks usually happens for those programs that are validating coming text from an input box, so in our OpenXml Integration Feature should be no problem.

There're some examples of Evil Regex if you'd like to play
- (a+)+
- ([a-zA-Z]+)*
- (a|aa)+
- (a|a?)+
- (.*a){x} for x \> 10

If you're interested to know more about this last topic (ReDoS) check the resources where I investigate about all this right below!

#### Documents

https://learn.microsoft.com/en-us/dotnet/standard/base-types/backtracking-in-regular-expressions

https://owasp.org/www-community/attacks/Regular_expression_Denial_of_Service_-_ReDoS

#### Videos

https://youtu.be/iihd7lo6Ui8

https://youtu.be/u01jb8YN2Lw



