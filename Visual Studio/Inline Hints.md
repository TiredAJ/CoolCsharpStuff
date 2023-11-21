---
tags:
  - VisualStudio
  - Settings
---
In VS, there’s a toggleable option to see inline hints (which as you’ll see, I have enabled). There’s many different subsections, but the main thing is it’ll show the parameter name for the argument you’re writing.
![[Pasted image 20231121194743.png]]For example, 

The function _Print()_ has two parameters “*Message*” and “*Newline*". With inline hints toggled on, I can see these names when I’m calling the function:
![[Pasted image 20231121194809.png]]

To enable this, go to *Tools > Options*
![[Pasted image 20231121194930.png]]

Then head to _Text Editor > C# > Advanced_ and scroll down to “Inline Hints”
![[Pasted image 20231121195127.png | 750]]

The two main options are “parameter name hints” and “type hints”. The first is what I just demonstrated and the second is used for things like _Var_ (which’ll be discussed more later), where it hints that _Beep_’s type will be a nullable string (_string?_).
![[Pasted image 20231121195213.png | 500]]

[Return to Home](Home.md)
