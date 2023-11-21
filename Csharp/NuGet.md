---
tags:
  - NuGet
  - VisualStudio
---
NuGet is effectively a package manager for C#, allowing users to easily share .NET code. To browse you can either go to the [NuGet](https://www.nuget.org/) website or browse directly through VS:
RMB either your project or solution and select *Manage NuGet packages*
![[Pasted image 20231121220809.png | 400]]

That should open a tab. It usually defaults to the “Installed” section, this’ll show what you have installed (and also dependencies that have been downloaded).
![[Pasted image 20231121220915.png | 700]]

Switching over to “Browse” (it may take a bit to load):
![[Pasted image 20231121220958.png | 700]]

You can see a selection to choose from and a search bar. You can look through and find (usually) what you need.
Lets say I need the MongoDB driver, I can easily search it up:
![[Pasted image 20231121221040.png | 700]]

Clicking on it will fill the panel to the right with information about the package, what .NET versions it works with, the project’s URL and usually a dropdown to select which version of the package to download:
![[Pasted image 20231121221102.png | 400]]

Once you’ve chosen the version you’d like, you can click “Install” at the top and it’ll attempt to install the package.

Depending on the package, a popup about licenses may appear for you to read and accept/decline:
![[Pasted image 20231121221142.png]]

Jumping back over to “Installed”:
![[Pasted image 20231121221153.png | 700]]

The package we just downloaded is at the top, and all the “transitive” packages (packages the main one depends on) are also listed.

If you uninstall a package and it’s left behind packages, or if you have packages installed that you aren’t using but can’t remember _which_ you aren’t using, you can ask VS to remove them:

RMB on your project in the _Solution Explorer_:
![[Pasted image 20231121221245.png | 300]]

And select “Remove Unused References”, it should show a popup allowing you to select what to do with any unused references VS finds:
![[Pasted image 20231121221308.png | 500]]

(For this example I downloaded Newtonsoft.JSON). It also shows the library I added at the start of the doc because I removed any code it uses.

Clicking “Apply” uninstalls the unused NuGet packages and removed the project’s reference to the library. This _didn’t_ remove the library from the project, it’s still in the _Solution Explorer_:
![[Pasted image 20231121221349.png | 300]]

But to use it again, I would need to [re-add it as a reference](Multiple%20projects%20per%20solution).

[Return to Home](Home)
