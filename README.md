# ipsc
IPSC(Inter Planet Site Creator) is a tool to create static html site with index pages from md,html and hyperlink

## Background

IPFS (Inter Planet File System [IPFS](https://ipfs.io)) is a peer-to-peer hyperlink protocol which is used to publish content. We can publish a web site  on IPFS as we publish a site on http.

But as IPFS is an p2p system, file published on IPFS cannot be changed, if we changed a file and publish to IPFS again, it is a completely new file from the old one.  Changing files of a IPFS file is not encouraged. So generally sites that are built on ASP.NET Java PHP which have a lot of scripts are not the best option when you want to publish a site to IPFS. Static website based on HTML and CSS is the best option.

IPCS is the tool to create static html site that you can publish to IPFS.

The site created by IPCS looks as follows:

- Site Root Folder
  - index.html
  - more1.html
  - more2.html
  - Pages
    - A1_xxxxxx.html
    - A2_xxxxxx.html

![Output Folder](https://github.com/aStarProgrammer/ipsc/blob/master/Images/outputfolder.png)

index.html is the entry point of the site, it looks like:

![index.html](https://github.com/aStarProgrammer/ipsc/blob/master/Images/index.png)



And the More... links to more1.html which contains links that index.html cannot contains

## Install

Download the release for your platform from Release folder

![Release Folder](https://github.com/aStarProgrammer/ipsc/blob/master/Images/release1.png)



![Release Folder](https://github.com/aStarProgrammer/ipsc/blob/master/Images/release2.png)


## Build
If you can not find a release for your platform, build it from source code as follows:

1. Install go

2. Install git
   
       	Download and install
       		https://git-scm.com/download
       	OR
       		sudo apt-get install git	

3. Install mingw(Windows)

4. Install Liteide (https://github.com/visualfc/liteide)


   ​	*Windows/Linux/MacOSX just download and install

   ​	*Raspbian

   ​		Download source (qt4 Linux 64)code and compile as follows:

   ​		

   ```bash
       sudo apt-get update
       sudo apt-get upgrade
       sudo apt-get install git
       git clone https://github.com/visualfc/liteide.git
       sudo apt-get install qt4-dev-tools libqt4-dev libqtcore4 libqtgui4 libqtwebkit-dev g++
       cd liteide/build
       ./update_pkg.sh
       export QTDIR=/usr
       ./build_linux.sh
       cd ~/liteide/liteidex
       ./linux_deploy.sh
       cd ~/liteide/liteidex/liteide/bin 
       ./liteide
   ```

5. Install pandoc
    pandoc used to convert md to html 
       	If you just want to compile IPSC, pandoc is not needed 
       	If you want to run IPSC, pandoc is needed.
       	https://www.pandoc.com

6. Install go lib
     Run following command in cmd/bash
       go get github.com/aWildProgrammer/fconf
     	go get github.com/shamsher31/goimgtype

7. Open IPSC with liteide 

8. Select the platform you needed, modify current environment according to step 1 and 3
    Modify GOROOT and PATH

9. Compile->Build

## Usage

IPSC(InterPlanet Site Creator) is a tool to create static html site with index pages from md,html and hyperlink

* Get This Help
		    

	```bash
	IPSC -Command "Help" -HelpType
	```

	Get help
		HelpType can be "QuickHelp" or "FullHelp"
		QuickHelp will return this help, and FullHelp will return a help with more information
	
* Create New Empty Site
		
```bash
IPSC -Command NewSite -SiteFolder  -SiteFolder -SiteTitle  -SiteAuthor  -SiteDescription  -OutputFolder
```

Create a new empty site project

	
Note: Run this method with super user or administrator permission
	
	* In Windows, start cmd with Administrator user, then run ipsc -Command "NewSite"
	
	* In Linux/Darwin run this cmd with sudo

Example:

```bash
IPSC -Command "NewSite" -SiteFolder "F:\TestSite" -SiteTitle "Test Site" -SiteAuthor "Chao(sdxianchao@gmail.com)" -SiteDescription "Test Site for IPSC" -OutputFolder "F:\SiteOutputFolder"
```

The site looks lite

![Empty Site Folder](https://github.com/aStarProgrammer/ipsc/blob/master/Images/sitefolder.png)

```bash
IPSC -Command "NewSite" -SiteFolder "F:\TestSite" -SiteTitle "Test Site" -SiteAuthor "Chao(sdxianchao@gmail.com)" -SiteDescription "Test Site for IPSC"
```




* Update Site Property
		
```bash
IPSC -Command "UpdateSite" -SiteFolder -SiteTitle -SiteAuthor -SiteDescription
```

This command will update the properties stored in sp file and, will update the name of sp file as SiteTitle changed

Example:

```bash
IPSC -Command "UpdateSite" -SiteFolder "F:\TestSite" -SiteTitle "Test Site 1" -SiteAuthor "Chao(sdxianchao@gmail.com)" -SiteDescription "Test Site for IPSC"
	
IPSC -Command "UpdateSite" -SiteFolder "F:\TestSite" -SiteAuthor "Chao(sdxianchao@hotmail.com)"
		
IPSC -Command "UpdateSite" -SiteFolder "F:\TestSite" -SiteTitle "Test Site " -SiteAuthor "Chao(sdxianchao@hotmail.com)" -SiteDescription "Test Site for IPSC"
```

* Get Site Properties
		
```bash
IPSC -Command "GetSiteProperty" -SiteFolder  -SiteTitle
```

This command will display site properties of a site project

Example:

```bash
IPSC -Command "GetSiteProperty" -SiteFolder "F:\TestSite" -SiteTitle "Test Site"
```




* List Source Pages
		
```bash
IPSC -Command "ListSourcePages" -SiteFolder -SiteTitle
```

List all the source pages

​	Example	

```bash
IPSC -Command "ListSourcePages" -SiteFolder "F:\TestSite" -SiteTitle "Test Site"
```

* List Output Pages
		
```bash
IPSC -Command "ListOutputPages" -SiteFolder -SiteTitle
```

List all the output pages

Example
	

```bash
IPSC -Command "ListOutputPages" -SiteFolder "F:\TestSite" -SiteTitle "Test Site"
```



* List Page
		
```bash
IPSC -Command "ListPage" -SiteFolder  -SiteTitle  -PageID
```

Display properties of page with specific ID

Example

```bash
IPSC -Command "ListPage" -SiteFolder "F:\TestSite" -SiteTitle "Test Site" -PageID "d0b75300ade9ea73cf45f29c7aac6ffa"
```




* Create Markdown File
		
```bash
IPSC -Command "CreateMarkdown" -SiteFolder -SiteTitle -PagePath -MarkdownType
```

Create Markdown file at PagePath with MarkdownType, copy needed md file from SiteFolder with SiteTitle

Example

```bash
IPSC -Command "CreateMarkdown" -SiteFolder "F:\TestSite" -SiteTitle "Test Site" -PagePath "F:\MarkdownWorkspace\_A1.md" -MarkdownType "News"
```

* Add Page
		
```bash
IPSC -Command "AddPage" -SiteFolder -SiteTitle -PagePath -LinkUrl -PageType -PageTitle -PageAuthor -TitleImage -IsTop
```

Add the Source Page file, with type PageType (MARKDOWN,HTML,LINK) to the SiteFolder\Src\Markdown or SiteFolder\Src\Html, and add metadata to site project file, including PageTitle PageAuthor PageTitleImage

Example

```bash
IPSC -Command "AddPage" -SiteFolder "F:\TestSite" -SiteTitle "Test Site" -PagePath "F:\MarkdownWorkspace\A1.md" -PageType "Markdown" -PageTitle "Test Markdown Page" -PageAuthor "Chao" -TitleImage "F:\MarkdownWorkspace\muxing.png" -IsTop false

IPSC -Command "AddPage" -SiteFolder "F:\TestSite" -SiteTitle "Test Site" -PagePath "F:\MarkdownWorkspace\_A1.html" -PageType "Html" -PageTitle "Test Html Page" -PageAuthor "Chao" -TitleImage "F:\MarkdownWorkspace\muxing.png" -IsTop true
		
IPSC -Command "AddPage" -SiteFolder "F:\TestSite" -SiteTitle "Test Site" -LinkUrl "https://www.google.com" -PageType "Link" -PageTitle "Test Link Page" -PageAuthor "Chao" -TitleImage "F:\MarkdownWorkspace\muxing.png" -IsTop true
```

* Update Page

```bash
IPSC -Command "UpdatePage" -SiteFolder -SiteTitle -PageID -PagePath -LinkUrl -PageTitle -PageAuthor -TitleImage -IsTop
```

Update the Source Page file, Update the file or properties if any of them are assigned.
​Example

```bash
IPSC -Command "UpdatePage" -SiteFolder "F:\TestSite" -SiteTitle "Test Site" -PageID "fc0f8d635ebb04d1c9393a722e8fc185" -PagePath "F:\MarkdownWorkspace\A1.md" -PageTitle "Test Markdown Page 1" -PageAuthor "Chao(sdxianchao@gmail.com)" -TitleImage "F:\MarkdownWorkspace\CNUK.png" -IsTop true

IPSC -Command "UpdatePage" -SiteFolder "F:\TestSite" -SiteTitle "Test Site" -PageID "fc0f8d635ebb04d1c9393a722e8fc185"  -PageTitle "Test Page Title 2"

IPSC -Command "UpdatePage" -SiteFolder "F:\TestSite" -SiteTitle "Test Site" -PageID "15fc19f3766fd7edf1f129018faa29cc" -LinkUrl "https://www.microsoft.com"
```

* Delete Page

```bash
IPSC -Command "DeletePage" -SiteFolder -SiteTitle -PageID -RestorePage
```

Delete the page with PageID from site project , if RestorePage is true, page will be moved to recycled bin. if RestorePage is false, page will be deleted directly. RestorePage defaultly true.

Example

```bash

IPSC -Command "DeletePage"  -SiteFolder "F:\TestSite" -SiteTitle "Test Site" -PageID 


"fc0f8d635ebb04d1c9393a722e8fc185" -RestorePage true
```

* List Recycled Pages
		       
```bash
IPSC -Command "ListRecycledPages" -SiteFolder -SiteTitle
```

List all the pages in the recycled bin	

Example

```bash
IPSC -Command "ListRecycledPages" -SiteFolder "F:\TestSite" -SiteTitle "Test Site"
```

* Restore Recycled Page	
```bash
IPSC -Command "RestoreRecycledPage" -SiteFolder -SiteTitle -PageID
```

Restore page with PageID if page is recycled

Example

```bash
IPSC -Command "RestoreRecycledPage" -SiteFolder "F:\TestSite" -SiteTitle "Test Site" -PageID "fc0f8d635ebb04d1c9393a722e8fc185
```

* Clear Recycled Pages   
	
```bash
IPSC -Command "ClearRecycledPages" -SiteFolder -SiteTitle
```

Remove all the recycled pages
​Example

```bash
IPSC -Command "ClearRecycledPages" -SiteFolder "F:\TestSite" -SiteTitle "Test Site"
```

* Compile the site
```bash
IPSC -Command "Compile" -SiteFolder -SiteTitle -IndexPageSize
```

Compile the site, change md to html and save it to output, copy html to output, create index page and more pages, then covert them to html,and save to output

Example

```bash
IPSC -Command "Compile" -SiteFolder "F:\TestSite" -SiteTitle "Test Site" -IndexPageSize "Normal"
```


For full help, run ipsc -Help FullHelp



## Raise A Issue

Send email to sdxianchao@gmail.com 



## Maintainers

[@aStarProgrammer](https://github.com/aStarProgrammer).


## License

[MIT](LICENSE)