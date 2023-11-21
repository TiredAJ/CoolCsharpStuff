---
tags:
  - VisualStudio
---
In VS, you can have more than one _Project_ per _Solution_. So, if you were making a library (stored in a separate folder) and wanted to use it in a different program while developing it, you could load it into one solution! This isn’t the only way to use a custom library with a project; it also loads it for development.

> [!info]  This doesn’t _move_ the project to the solution's folder, It just gives VS a reference to the project.

![[Pasted image 20231121192808.png]]

I have the program “HelloWorld” (shown above), and I want to use the “HelloWorldLib” program I’ve been developing separately.
To add it, right-click (RMB) on ![[Pasted image 20231121192923.png | 450]] and select _Add_ > _Existing Project_.
![[Pasted image 20231121193016.png | 600]]

This should bring up a file dialog. Navigate to the folder with the project you want to add, select the .csproj and click “Open”.
![[Pasted image 20231121193157.png |  600 ]]

Now, it should show up in “Solution Explorer”.
![[Pasted image 20231121193256.png | 400]]


Now it’s here; you can edit the contents of the project you’ve just added, but there’s one more step if you want to use the new project with your current project. 

Right-click the original project ![[Pasted image 20231121193634.png]] and select *Add > Project Reference.*
![[Pasted image 20231121193755.png | 600]]

This will bring up a dialog showing what projects are in the current solution (and some other shenanigans). So now, from here you can click the checkbox by the project then “OK”.
![[Pasted image 20231121193903.png | 600]]

> [!info] 
> *If you want to add a project as a reference but not add it to the solution, you can skip all the steps above until the very last, where you can click “Browse…” and select the project that way.*

Now it’s added as a reference, you can write “Using #;” where # is the namespace of the project you just added and use it. And also, because it’s now a project of this solution, you can edit it from the same VS window, which I now need to do because I forgot to set the lib function to static.
![[Pasted image 20231121194125.png | 750]]

Navigating to the .cs file of the library, I can just open it up and change the function to _static_.
![[Pasted image 20231121194214.png | 750]]

[Return to Home](Home.md)
