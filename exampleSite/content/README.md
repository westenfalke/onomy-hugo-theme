---
title: Creating A HUGO Theme westenfalke/onomy-hugo-theme From Scratch
---
## Convention
### Root
Let's start with a clean slate e.g. in our home directory e.g. in a folder named `\~/CAHTFS/`.
Its name dosen't matter and to keep things consistent and easy to replay, 
all paths are relative too this folder and all comands are executes sitting in that folder, too. 

	westenfalke@MiniDEV:~$ mkdir CAHTFS
    westenfalke@MiniDEV:~$ cd CAHTFS/
    westenfalke@MiniDEV:~/CAHTFS$

and `westenfalke@MiniDEV:~/CAHTFS$` is replaced with just `#` just like this:


    westenfalke@MiniDEV:~/CAHTFS$ ls -la
    total 8
    drwxr-xr-x  2 westenfalke westenfalke 4096 Jan  2 15:52 .
    drwxr-xr-x 11 westenfalke westenfalke 4096 Jan  2 15:52 ..


    # ls -la
    total 8
    drwxr-xr-x  2 westenfalke westenfalke 4096 Jan  2 15:52 .
    drwxr-xr-x 11 westenfalke westenfalke 4096 Jan  2 15:52 ..

## [Installation][Installation]

### Madatory Commands
#### [hugo][hugo-cmd]
`hugo` the start of this show

    # sudo apt install hugo

### Optional Commands

#### [tree][tree-cmd]
To display ascii style information regarding the files and the folder structure, 
I introduce the `tree` command to for sake of this tutorial. 

    # sudo apt install tree

#### [git][git-cmd]
I like `git` to do the version controll thingi here,
if version control is not in you scope you can start
[here Creating A HUGO Theme From Scratch][cahtfs]

    # sudo apt install git

#### [gh][gh-cmd]
Hence I like to see you participating in this project I'll publish it on GitHUB via CLI using the `gh` command.
        
    # sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-key C99B11DEB97541F0 
    # sudo apt-add-repository https://cli.github.com/packages
    # sudo apt update
    # sudo apt install gh

## [Preparation][Preparation]
This prepatations are optional, but for convinience I like to have of site version a control in place 
### Login to GitHub 
    # gh auth login
    
    # gh auth login
    ? What account do you want to log into?  [Use arrows to move, type to filter]
    > GitHub.com
      GitHub Enterprise Server
    
    ? What account do you want to log into? GitHub.com
    - Logging into github.com
    ? You're already logged into github.com as westenfalke. Do you want to re-authenticate? (y/N) Y
    
    ? How would you like to authenticate?  [Use arrows to move, type to filter]
    > Login with a web browser
    Paste an authentication token
    
    ! First copy your one-time code: nXlm-kijo
    - Press Enter to open github.com in your browser...  
    ✓ Authentication complete. Press Enter to continue...
    
    ? Choose default git protocol  [Use arrows to move, type to filter]
    > HTTPS
    SSH
    
    - gh config set -h github.com git_protocol https
    ✓ Configured git protocol
    ✓ Logged in as westenfalke
 
### Creating A Repository On GitHUB
    # gh repo create onomy-hugo-theme
    ? Visibility Public
    ? This will create 'onomy-hugo-theme' in your current directory. Continue?  Yes
    ✓ Created repository westenfalke/onomy-hugo-theme on GitHub
    ? Create a local project directory for westenfalke/onomy-hugo-theme? (Y/n) n
    ? Create a local project directory for westenfalke/onomy-hugo-theme? No

### Clone The Empty Repository  
    # git clone  https://github.com/westenfalke/onomy-hugo-theme.git themes/onomy
    Cloning into 'themes/onomy'...
    warning: You appear to have cloned an empty repository.

## Creating A HUGO Theme From Scratch 
Here is the the real thing and from now on all commands are relative to the `~/CAHTFS`.

### Create A New Theme
    # hugo new theme onomy
    Creating theme at /home/westenfalke/CAHTFS/themes/onomy
    
    # tree
    .
    ├── resources
    │   └── _gen
    │       ├── assets
    │       └── images
    └── themes
        └── onomy
            ├── LICENSE
            ├── archetypes
            │   └── default.md
            ├── layouts
            │   ├── 404.html
            │   ├── _default
            │   │   ├── baseof.html
            │   │   ├── list.html
            │   │   └── single.html
            │   ├── index.html
            │   └── partials
            │       ├── footer.html
            │       ├── head.html
            │       └── header.html
            ├── static
            │   ├── css
            │   └── js
            └── theme.toml

    13 directories, 11 files
    
#### A Bit Of House Keeping
While creating the theme `hugo` creates some file in the `resources/` folder we no longer need.

    # rm -rf resources/

### Create An Exmple Website

The example website in the theme will be used to sowcase off its features and will contains this tutorial as a reference implementaion.

    # hugo new site exampleSite
    Congratulations! Your new Hugo site is created in /home/westenfalke/CAHTFS/themes/onomy/exampleSite.

    Just a few more steps and you're ready to go:

    1. Download a theme into the same-named folder.
       Choose a theme from https://themes.gohugo.io/ or
       create your own with the "hugo new theme <THEMENAME>" command.
    2. Perhaps you want to add some content. You can add single files
       with "hugo new <SECTIONNAME>/<FILENAME>.<FORMAT>".
    3. Start the built-in live server via "hugo server".

    Visit https://gohugo.io/ for quickstart guide and full documentation.

    # tree themes/onomy/exampleSite/
    themes/onomy/exampleSite/
    ├── archetypes
    │   └── default.md
    ├── config.toml
    ├── content
    ├── data
    ├── layouts
    ├── static
    └── themes

### Update the LICENSE
Currently HUGO creates a LICENSE file using "_The MIT License (MIT)_" as default. 

You can change this e.g. by using the [CC License Chooser][cc-license-chooser], or create a LICENCE file right now on [GitHUB][gitgub], hence here is a standard suggestion (on empty repositories) which offers several different licenses during file creation. 

[link to a page about LICENSE selection on gitgub][tbd]
[link to a page about LICENSE selection with CC License Chooser][tbd]

If you are cool with "_The MIT License (MIT)_"  just keep it, I'll switch silently to _Creative Commons Attribution-ShareAlike 4.0 International Public License_.

	# head themes/onomy/LICENSE
	Creative Commons Attribution-ShareAlike 4.0 International Public License

	By exercising the Licensed Rights (defined below), You accept and agree to be bound by the terms and conditions of this Creative Commons Attribution-ShareAlike 4.0 International Public License ("Public License"). To the extent this Public License may be interpreted as a contract, You are granted the Licensed Rights in consideration of Your acceptance of these terms and conditions, and the Licensor grants You such rights in consideration of benefits the Licensor receives from making the Licensed Material available under these terms and conditions.

	Section 1 – Definitions.
	a.Adapted Material means material subject to Copyright and Similar Rights that is derived from or based upon the Licensed Material and in which the Licensed Material is translated, altered, arranged, transformed, or otherwise modified in a manner requiring permission under the Copyright and Similar Rights held by the Licensor. For purposes of this Public License, where the Licensed Material is a musical work, performance, or sound recording, Adapted Material is always produced where the Licensed Material is synched in timed relation with a moving image.
	b.Adapter's License means the license You apply to Your Copyright and Similar Rights in Your contributions to Adapted Material in accordance with the terms and conditions of this Public License.
	c.BY-SA Compatible License means a license listed at  creativecommons.org/compatiblelicenses, approved by Creative Commons as essentially the equivalent of this Public License.
	d.Copyright and Similar Rights means copyright and/or similar rights closely related to copyright including, without limitation, performance, broadcast, sound recording, and Sui Generis Database Rights, without regard to how the rights are labeled or categorized. For purposes of this Public License, the rights specified in Section 2(b)(1)-(2) are not Copyright and Similar Rights.
	e.Effective Technological Measures means those measures that, in the absence of proper authority, may not be circumvented under laws fulfilling obligations under Article 11 of the WIPO Copyright Treaty adopted on December 20, 1996, and/or similar international agreements.

## Create Minimal Documantation 

    # touch themes/onomy/README.md
    # echo "# Creating A HUGO Theme westenfalke/onomy-hugo-theme From Scratch" >> themes/onomy/README.md

## Update Theme Declaration 
Hence the content of this theme is straigt from the hugo documentation I'll skip the `original` section and you can find a list auf websites or authors who enabled/inpired me to write this tutorial in the [credits section][credits] of this [README][readme-md].

    # cat themes/onomy/theme.toml  

    ### theme.toml template for a Hugo theme
    ### See https://github.com/gohugoio/hugoThemes#themetoml for an example
    
    name = "onomy"
    license = "Attribution-ShareAlike 4.0 International"
    licenselink = "https://creativecommons.org/licenses/by-sa/4.0?ref=chooser-v1"
    description = "onomy (hugo taxonomy template)"
    homepage = "https://github.com/westenfalke/onomy-hugo-theme"
    tags = [gdpr selfcontaint learning tutorial]
    features = [taxonomy pagination cookie-free]
    min_version = "0.41"
    
    [author]
    name = "westenfalke"
    homepage = "https://github.com/westenfalke"
    
    ### If porting an existing theme
    ###[original]
    ###  name = ""
    ###  homepage = ""
    ###  repo = ""


### A First Mile Stone 

#### Lauching hugo
One could think, this is it, and yes firing up hugo right now will give us a working [sitemap][sitemap-xml] and three empty pages and hence content creation is our task, this is pretty much what to expect.  
![hugo start parameter aligned with folder](/img/screenshot/hugo-parameter.png "hugo parameter and folder")


    # hugo server  --source ./themes/onomy/exampleSite/ --themesDir ../../../themes/ --theme  onomy 
    
                       | EN
    -------------------+-----
      Pages            |  3
      Paginator pages  |  0
      Non-page files   |  0
      Static files     |  0
      Processed images |  0
      Aliases          |  0
      Sitemaps         |  1
      Cleaned          |  0

    Built in 3 ms
    Watching for changes in /home/westenfalke/CAHTFS/themes/onomy/{archetypes,exampleSite,layouts,static}
    Watching for config changes in themes/onomy/exampleSite/config.toml
    Environment: "development"
    Serving pages from memory
    Running in Fast Render Mode. For full rebuilds on change: hugo server --disableFastRender
    Web Server is available at http://localhost:1313/ (bind address 127.0.0.1)
    Press Ctrl+C to stop

#### Haveing A Look At The Sitemap

    http://localhost:1313/sitemap.xml

    <?xml version="1.0" encoding="utf-8" standalone="yes"?>
    <urlset xmlns="http://www.sitemaps.org/schemas/sitemap/0.9"
      xmlns:xhtml="http://www.w3.org/1999/xhtml">
      <url>
        <loc>http://localhost:1313/categories/</loc>
      </url>
      <url>
        <loc>http://localhost:1313/</loc>
      </url>
      <url>
        <loc>http://localhost:1313/tags/</loc>
      </url>
    </urlset>

### Make Us Self A Home
`hugo` creates all templates for us and besites the <em>baseof</em> template, all are empty.
Before we can see some thing on our new created theme, by running the exampleSite with `hugo`, we'll simply copy and paste the stuff fom the [hugo template documentation][hugo-templates-doc] into the templates. 

    # tree -s themes/onomy/layouts/
    themes/onomy/layouts/
    ├── [  0]  404.html
    ├── [   ]  _default
    │   ├── [250]  baseof.html
    │   ├── [  0]  list.html
    │   └── [  0]  single.html
    ├── [  0]  index.html
    └── [   ]  partials
        ├── [  0]  footer.html
        ├── [  0]  head.html
        └── [  0]  header.html
    2 directories, 8 files

Put [Hugo Templates Homepage][hugo-templates-homepage-doc] into `themes/onomy/layouts/index.html`

    # cat themes/onomy/layouts/index.html
    {{ define "main" }}
        <main aria-role="main">
          <header class="homepage-header">
            <h1>{{.Title}}</h1>
            {{ with .Params.subtitle }}
            <span class="subtitle">{{.}}</span>
            {{ end }}
          </header>
          <div class="homepage-content">
            <!-- Note that the content for index.html, as a sort of list page, will pull from content/_index.md -->
            {{.Content}}
          </div>
          <div>
            {{ range first 10 .Site.RegularPages }}
                {{ .Render "summary"}}
            {{ end }}
          </div>
        </main>
    {{ end }}

Put [Hugo Templates List][hugo-templates-lists-doc] into `themes/onomy/layouts/_default/list.html`

    #  cat themes/onomy/layouts/_default/list.html
    {{ define "main" }}
    <main>
        <article>
            <header>
                <h1>{{.Title}}</h1>
            </header>
            <!-- "{{.Content}}" pulls from the markdown content of the corresponding _index.md -->
            {{.Content}}
        </article>
        <ul>
        <!-- Ranges through content/posts/*.md -->
        {{ range .Pages }}
            <li>
                <a href="{{.Permalink}}">{{.Date.Format "2006-01-02"}} | {{.Title}}</a>
            </li>
        {{ end }}
        </ul>
    </main>
    {{ end }}

Put [Hugo Single Page Templates][hugo-single-page-templates-doc] into `themes/onomy/layouts/_default/single.html`

    #  cat themes/onomy/layouts/_default/single.html
    {{ define "main" }}
    <section id="main">
      <h1 id="title">{{ .Title }}</h1>
      <div>
            <article id="content">
               {{ .Content }}
            </article>
      </div>
    </section>
    <aside id="meta">
        <div>
        <section>
          <h4 id="date"> {{ .Date.Format "Mon Jan 2, 2006" }} </h4>
          <h5 id="wordcount"> {{ .WordCount }} Words </h5>
        </section>
        {{ with .Params.topics }}
        <ul id="topics">
          {{ range . }}
            <li><a href="{{ "topics" | absURL}}{{ . | urlize }}">{{ . }}</a> </li>
          {{ end }}
        </ul>
        {{ end }}
        {{ with .Params.tags }}
        <ul id="tags">
          {{ range . }}
            <li> <a href="{{ "tags" | absURL }}{{ . | urlize }}">{{ . }}</a> </li>
          {{ end }}
        </ul>
        {{ end }}
        </div>
        <div>
            {{ with .PrevInSection }}
              <a class="previous" href="{{.Permalink}}"> {{.Title}}</a>
            {{ end }}
            {{ with .NextInSection }}
              <a class="next" href="{{.Permalink}}"> {{.Title}}</a>
            {{ end }}
        </div>
    </aside>

For the hompage template alias `index.html` to work properly, we have to add one additional template `themes/onomy/layouts/_default/summary.html` to the mix, just to satify the referenced `{{ .Render "summary"}}`. 

    # touch themes/onomy/layouts/_default/summary.html

Put [HUGO Content View Templates][hugo-content-view-templates-doc] into `themes/onomy/layouts/_default/summary.html`

    # cat themes/onomy/layouts/_default/summary.html
    <article class="post">
      <header>
        <h2><a href='{{ .Permalink }}'> {{ .Title }}</a> </h2>
        <div class="post-meta">{{ .Date.Format "Mon, Jan 2, 2006" }} - {{ .FuzzyWordCount }} Words </div>
      </header>
      {{ .Summary }}
      <footer>
      <a href='{{ .Permalink }}'><nobr>Read more →</nobr></a>
      </footer>
    </article>
        
### Let's Create Some Content To Test Our New Theme
I suggest a hompage, two pages (an imprint and a privacy policy) and three posts are enough for starters and to test the pagination, lists and the summary.

#### Create The Hompage
This is where the magic happens, than this file triggers the invocation of the `index.html` template which renered by the `baseof.html`.

    # hugo new "_index.md" --source themes/onomy/exampleSite/
    /home/westenfalke/CAHTFS/themes/onomy/exampleSite/content/_index.md created

#### Create The Shells For Imprint And The Privacy Policy 

    # hugo new "imprint.md" --source themes/onomy/exampleSite/
    /home/westenfalke/CAHTFS/themes/onomy/exampleSite/content/imprint.md created
    # hugo new "privacy policy.md" --source themes/onomy/exampleSite/
    /home/westenfalke/CAHTFS/themes/onomy/exampleSite/content/privacy policy.md created

#### Create Some Empty Posts 

    #hugo new "posts/the first post.md" --source themes/onomy/exampleSite/
    /home/westenfalke/CAHTFS/themes/onomy/exampleSite/content/posts/the first post.md created
    # hugo new "posts/the second post.md" --source themes/onomy/exampleSite/
    /home/westenfalke/CAHTFS/themes/onomy/exampleSite/content/posts/the second post.md created
    # hugo new "posts/the third post.md"  --source themes/onomy/exampleSite/
    /home/westenfalke/CAHTFS/themes/onomy/exampleSite/content/posts/the third post.md created

## Let's Have A Second Look 
Hence this all of our documents are drafts, the flag `--buildDrafts` will do the trick _of rendering all the drafts_ for the moment, so there is no need to change our newly created content yet.

![hugo start parameter aligned with folder](/img/screenshot/hugo-parameter.png "hugo parameter and folder")
                            
	# hugo server  --source ./themes/onomy/exampleSite/ --themesDir ../../../themes/ --theme onomy --buildDrafts

                       | EN
    -------------------+-----
      Pages            | 13
      Paginator pages  |  0
      Non-page files   |  0
      Static files     |  0
      Processed images |  0
      Aliases          |  0
      Sitemaps         |  1
      Cleaned          |  0

    Built in 18 ms
    Watching for changes in /home/westenfalke/CAHTFS/themes/onomy/{archetypes,exampleSite,layouts,static}
    Watching for config changes in themes/onomy/exampleSite/config.toml
    Environment: "development"
    Serving pages from memory
    Running in Fast Render Mode. For full rebuilds on change: hugo server --disableFastRender
    Web Server is available at http://localhost:1313/ (bind address 127.0.0.1)
    Press Ctrl+C to stop


I'm rather keen to see the [http://localhost:1313/sitemap.xml]() and than have a look at [http://localhost:1313/]().

	<?xml version="1.0" encoding="utf-8" standalone="yes"?>
	<urlset xmlns="http://www.sitemaps.org/schemas/sitemap/0.9"
	  xmlns:xhtml="http://www.w3.org/1999/xhtml">
	  <url>
		<loc>http://localhost:1313/posts/</loc>
		<lastmod>2021-01-02T23:30:43+01:00</lastmod>
	  </url>
	  <url>
		<loc>http://localhost:1313/posts/the-third-post/</loc>
		<lastmod>2021-01-02T23:30:43+01:00</lastmod>
	  </url>
	  <url>
		<loc>http://localhost:1313/posts/the-second-post/</loc>
		<lastmod>2021-01-02T23:30:18+01:00</lastmod>
	  </url>
	  <url>
		<loc>http://localhost:1313/posts/the-first-post/</loc>
		<lastmod>2021-01-02T23:29:56+01:00</lastmod>
	  </url>
	  <url>
		<loc>http://localhost:1313/privacy-policy/</loc>
		<lastmod>2021-01-02T23:29:14+01:00</lastmod>
	  </url>
	  <url>
		<loc>http://localhost:1313/imprint/</loc>
		<lastmod>2021-01-02T23:28:55+01:00</lastmod>
	  </url>
	  <url>
		<loc>http://localhost:1313/</loc>
		<lastmod>2021-01-02T23:15:42+01:00</lastmod>
	  </url>
	  <url>
		<loc>http://localhost:1313/categories/</loc>
	  </url>
	  <url>
		<loc>http://localhost:1313/readme/</loc>
	  </url>
	  <url>
		<loc>http://localhost:1313/tags/</loc>
	  </url>
	</urlset>



### Just Go Another Mile
Just to proofe the above assumtion about the invocation of the `index.html` template which renders the `baseof.html` right and to leafe no templates empty (except `themes/onomy/layouts/404.html`), make this few little upates.

    # echo '{{ "<!-- " | safeHTML }}head.html{{ " -->" | safeHTML }}<head><meta charset="utf-8"></head>' >> themes/onomy/layouts/partials/head.html
    # echo '<div>FOOTER</div>' >> themes/onomy/layouts/partials/footer.html
    # echo '<div>HEADER</div>' >> themes/onomy/layouts/partials/header.html




## Almost Half Time
Before any further changes I'm going to commit this piece of work to `git` with some specific preparation, you can [skip](#SecondHalf) if you are not invested in version control [jump direcly to Second Half OF Creating A HUGO Theme From Scratch](#SecondHalf)

### What To Ignore 
Telling git to ignore some files and  folder comcleatly.

    # touch themes/onomy/.gitignore
    # echo ".gitignore
    **/resorces
    **/public
    **/public_html
    **/*.ORI" >> touch themes/onomy/.gitignore

### What to keep
Finding and adding all files we creates so far witout the meta data in `.git` 

	# find . -type f | grep -v '.git' | xargs -n1 -d'\n' echo | cut -d'/' -f 4- |xargs  -d'\n' -n1 git --work-tree=themes/onomy/ --git-dir=themes/onomy/.git/ add
    # git  --work-tree=themes/onomy/ --git-dir=themes/onomy/.git  add -f .gitignore
	
	# git  --work-tree=themes/onomy/ --git-dir=themes/onomy/.git/ status
	On branch master

	No commits yet

	Changes to be committed:
	  (use "git rm --cached <file>..." to unstage)
			new file:   .gitignore
			new file:   LICENSE
			new file:   README.md
			new file:   archetypes/default.md
			new file:   exampleSite/archetypes/default.md
			new file:   exampleSite/config.toml
			new file:   exampleSite/content/README.md
			new file:   exampleSite/content/_index.md
			new file:   exampleSite/content/imprint.md
			new file:   exampleSite/content/posts/the first post.md
			new file:   exampleSite/content/posts/the second post.md
			new file:   exampleSite/content/posts/the third post.md
			new file:   exampleSite/content/privacy policy.md
			new file:   exampleSite/static/img/screenshot/hugo-parameter.png
			new file:   layouts/404.html
			new file:   layouts/_default/baseof.html
			new file:   layouts/_default/list.html
			new file:   layouts/_default/single.html
			new file:   layouts/_default/summary.html
			new file:   layouts/index.html
			new file:   layouts/partials/footer.html
			new file:   layouts/partials/head.html
			new file:   layouts/partials/header.html
			new file:   static/img/screenshot/hugo-parameter.png
			new file:   theme.toml
    
	# git --work-tree=themes/onomy/ --git-dir=themes/onomy/.git commit -m'initial configuration, README, LICENSE and templates'
	[master (root-commit) d8101fb] initial configuration, README, LICENSE and templates
	 25 files changed, 1605 insertions(+)
	 create mode 100644 .gitignore
	 create mode 100644 LICENSE
	 create mode 100644 README.md
	 create mode 100644 archetypes/default.md
	 create mode 100644 exampleSite/archetypes/default.md
	 create mode 100644 exampleSite/config.toml
	 create mode 100644 exampleSite/content/README.md
	 create mode 100644 exampleSite/content/_index.md
	 create mode 100644 exampleSite/content/imprint.md
	 create mode 100644 exampleSite/content/posts/the first post.md
	 create mode 100644 exampleSite/content/posts/the second post.md
	 create mode 100644 exampleSite/content/posts/the third post.md
	 create mode 100644 exampleSite/content/privacy policy.md
	 create mode 100644 exampleSite/static/img/screenshot/hugo-parameter.png
	 create mode 100644 layouts/404.html
	 create mode 100644 layouts/_default/baseof.html
	 create mode 100644 layouts/_default/list.html
	 create mode 100644 layouts/_default/single.html
	 create mode 100644 layouts/_default/summary.html
	 create mode 100644 layouts/index.html
	 create mode 100644 layouts/partials/footer.html
	 create mode 100644 layouts/partials/head.html
	 create mode 100644 layouts/partials/header.html
	 create mode 100644 static/img/screenshot/hugo-parameter.png
	 create mode 100644 theme.toml
	# git --work-tree=themes/onomy/ --git-dir=themes/onomy/.git push
	Enumerating objects: 37, done.
	Counting objects: 100% (37/37), done.
	Delta compression using up to 4 threads
	Compressing objects: 100% (28/28), done.
	Writing objects: 100% (37/37), 20.80 KiB | 1.39 MiB/s, done.
	Total 37 (delta 1), reused 0 (delta 0)
	remote: Resolving deltas: 100% (1/1), done.
	To https://github.com/westenfalke/onomy-hugo-theme.git
	 * [new branch]      master -> master

## Second Half OF Creating A HUGO Theme From Scratch
<div id="tbd"/>
* add tanonomy templates
* link to a page about LICENSE selection on gitgub
* link to a page about LICENSE selection with CC License Chooser


## [Credits][credits] {#credits}
* [Installing gh on Linux and FreeBSD][mislav-gh-linux] by Mislav Marohnić
* [Git Submodules basic explanation][gitaarik-git-submodules] by Rik Gitaarik
* [Markdown: Syntax][daringfireball] by John Gruber
* [The hugo-sandbox][kaushalmodi-hugo-sandbox] by Kaushal Modi
* [GitHUB][gitgub] distributed version control system
* [Git][git] distributed version control system

[readme-md]: # "README.md"
[tbd]: #tbd "To Be Done"

[credits]: #credits "Thank you ALL"
[kaushalmodi-hugo-sandbox]: https://gitlab.com/kaushalmodi/hugo-sandbox/ "The hugo-sandbox "
[mislav-gh-linux]: https://github.com/cli/cli/blob/trunk/docs/install_linux.md  "Installing gh on Linux"
[gitaarik-git-submodules]: https://gist.github.com/gitaarik/8735255 "Submodules basic explanation"
[daringfireball]: https://daringfireball.net/projects/markdown/syntax "Markdown: Syntax"

[tools]: #tools "all the tools you need"
[hugo-cmd]: #hugo-cmd "hugo command"
[tree-cmd]: #tree-cmd "tree command"
[git-cmd]: #git-cmd "git the version control"
[gh-cmd]: #gh-cmd "GitHUB CLI tool"
[cc-license-chooser]: https://creativecommons.org/choose/ "Creative Commons License Chooser"
[git]: https://git-scm.com/ "git distributed version control system --local-branching-on-the-cheap"
[gitgub]: https://github.com/ "GitHUB Version Control - Where the world builds software"

[preparation]: #Preparation "Preparation For Creating A HUGO Theme From Scratch"
[installation]: #Installation "Installation For Creating A HUGO Theme From Scratch"
[cahtfs]: #creating-a-hugo-theme-from-scratch "Creating A HUGO Theme From Scratch" 
[cahtfs-second-half]: #second-half-of-creating-a-hugo-theme-from-scratch "Second Half OF Creating A HUGO Theme From Scratch"
[hugo-templates-doc]: https://gohugo.io/templates/ "hugo templates documentation"
[hugo-templates-homepage-doc]: https://gohugo.io/templates/homepage/ "HUGO Homepage Template"
[hugo-templates-lists-doc]: https://gohugo.io/templates/lists/ "HUGO Lists Template"
[hugo-single-page-templates-doc]: https://gohugo.io/templates/single-page-templates/ "HUGO Single Page Templates"
[hugo-content-view-templates-doc]: https://gohugo.io/templates/views/#summaryhtml "HUGO Content View Templates"

[sitemap-xml]: http://localhost:1313/sitemap.xml "sitemap.xml @ localhost"
