# The Software Design Lab WebPage Template

Dear maintainer, this webpage was made using a jekyll theme that can be found [here](https://github.com/uwsampa/research-group-web).

The source code can be found in develop branch. In master branch its only the result of the compilation. We are using a gem that makes easier to add a new publication but it cannot be used in the ci pipelines of github.

You need to have ruby and jekyll installed in your computer. Then you have to clone the repository and change to develop branch.

# Building the webpage

Once you are in the development folder use ```jekyll build``` and ```jekyll serve --host 127.0.0.1 --port 8080``` see the result of the page. When all the changes have been done copy the content of the ```_site``` folder, change to master branch and replace all the content. I strongly recommend to run a local server to make sure all the changes are in the page. Then you can push your changes in both branches to the repo.

# Maintaining this webpage

---
## **Home Page**
---

### **Slider**

The photos that appear in the slider can be modified in the index.html.

The images path are added in the file header.

```
...
image: /img/ICSME18LR.jpg
image2: /img/news/BluehackTSDLSlider.jpeg
image3: /img/DSC_0414_Original.jpg
image4: /img/grace.jpg
image5: /img/google18.jpg
image6: /img/peru18.jpg
...
```

and then you have to had a new carrousel item replacing ```<imageKey>``` and ```<imageCaption>```:

```html
<div class="carousel-item">
  <img class="d-block w-100" src="{{site.base}}{{ <imageKey> }}" alt="Team">
  <div class="carousel-caption d-none d-md-block">
    <h5> <imageCaption> </h5>
  </div>
</div>
```

### **News**

News can be found in ```_posts``` folder. Everytime you create a news the file must be called like 
```
<year>-<month>-<day>-<newsID>.md
```
And its content should be something like this:
```
---
layout: post
title: "ACM SIGSOFT Distinguished Paper Award"
icon: trophy
image: https://upload.wikimedia.org/wikipedia/commons/thumb/8/8e/Association_for_Computing_Machinery_%28ACM%29_logo.svg/300px-Association_for_Computing_Machinery_%28ACM%29_logo.svg.png
shortnews: true
---

Mario Linares-Vásquez received an ACM DPA for his paper "Automatically Assessing Code Understandability: How Far Are We?", in Proceedings of 32nd IEEE/ACM International Conference on Automated Software Engineering (ASE'17), Urbana-Champaign, Illinois, USA, October 30 - November 3, 2017
```

Depending on the type of news the icon can be:
| Type of news | icon key |
|:---:|:---:|
| New published paper | newspaper-o |
| Award | trophy |
| Talk | slideshare |

The amount of news that are shown in the index is defined in the ```_config.yml``` using the key ```front_page_news```.

---
## **People**
---

People is modified in the ```_data/people.yml```. We have 5 posible roles in our research lab:

| Role | Who has this role |
|---|---|
| faculty | Professors |
| grad | Ph.D. and Ms. students |
| ugrad | Undergraduate students |
| collab | External Collaborators |
| alum | Past students of TSDL |

when a person is added to the ```people.yml``` file it must follow the following template:

```
<id>:
    display_name: "<fullName>"
    role: "<role>"
    image: "/img/people/<imageName>.jpg"
    webpage: "<personalPageURL>"
    bio: "<description Of Current position>"
```

Is important to see that if a person do not have a personal page that tag must be ommited. Also, alumni dont use either webpage or bio tag.


---
## **Research Projects**
---

Research projects can be found in ```_rschprojects/```. Each project has its own MarkDown file and usualy follow this template:
```
---
title: "Mutation Testing"
description: Mutation Testing is a type of software testing where we mutate (change) certain statements in the source code and check if the test cases are able to find the errors. It is a type of White Box Testing which is mainly used for Unit Testing. The changes in mutant program are kept extremely small, so it does not affect the overall objective of the program. In this moment, we have open projects in NodeJS and Android Framework


people:
  - marioLinares
  - camiloEscobar
  - diegoRodriguez
  - collGabrieleBavota
  - collMassimiliano
  - collDenysPosh

topic: Software Testing
layout: project
image: /img/project-images/mutation.png

---
```

Right now the topic tag defines how they are group in the web page, currently we have 3 possible values:
- Automated Software Engineering
- Quality Attributes in Mobile Apps
- Software Testing

---
## **Software Development Projects**
---
This projects follow this template:
```
---
title: "FIND: A Software Platform Against Human Trafficking"
description: Technological platform under development. This solution is being financed by the United Nations Office on Drugs and Crime. It includes an AI module based on IBM Watson, mobile applications and a dashboard.


people:
  - dianaSolano
  - lauraBello
  - camiloEscobar
  - santiagoLinan
  - sergioYodeb
  - marioLinares
link: https://thesoftwaredesignlab.github.io/blog/2018/09/01/bluehack.html
layout: project
image: /img/project-images/findBlueHack.jpg
---
```

Here there is no topic and projects are shown directly, but there is a link tag that is important to fill.

---
## **Publications**
---

If you want to add a new publication to the page just copy the paper/journal bibtex content into ```bib/pubs.bib```. Jekyll and Jekyll-scholar will do all the magic and will generate a new entry. 

However, there are some important things to check before pushing your changes:  
1. New publications bibtex key must be meaninfull, we recommend to use: 
```
<firstLastnameOfFirstAuthor><Year><toolName|confName|journalName|meaningfulWor>
---
linan2018rip
linares2017cel
rodriguez2018mutode
```
2. If the bibtex has the keyworks tag and its content its to long its better to remove it because bibtex link in webpage generates a div whose height is based on the number of lines of the bibtex, if the keywords are too long the layout breaks.

The filter over the publications is done in the ```publications.html``` file. In case you want to change something.

---
## **Code**
---


If you want to change the template that

























Research Group Web Site Template
================================

This is a [Jekyll][]-based Web site intended for research groups. Your group should be able to get up and running with minimal fuss.

<p align="center">
<img src="screenshot.png" width="387" height="225" alt="screenshot of the template">
</p>

This project originated at the University of Washington.  You can see the machinery working live at [our site][sampa].

This work is licensed under a [Creative Commons Attribution-NonCommercial 4.0 International License][license].

[sampa]: http://sampa.cs.washington.edu/
[license]: https://creativecommons.org/licenses/by-nc/4.0/


Features
--------

* Thanks to [Jekyll][], content is just text files. So even faculty should be able to figure it out.
* Publications list generated from BibTeX.
* Personnel list. Organize your professors, students, staff, and alumni.
* Combined news stream and blog posts.
* Easily extensible navigation bar.
* Responsive (mobile-ready) design based on [Bootstrap][].

[Bootstrap]: http://getbootstrap.com/


Setup
-----

1. Install the dependencies. You will need [Python][], [bibble][] (`pip install bibble`), and [Jekyll][] (`gem install jekyll`).
2. [Fork][] this repository on GitHub.
3. Clone the fork to your own machine: `git clone git@github.com:yourgroup/research-group-web.git`.
4. Add an "upstream" remote for the original repository so you can stay abreast of bugfixes: `git remote add upstream git://github.com/uwsampa/research-group-web.git`.
5. Customize. Start with the `_config.yml` file, where you enter the name of the site and its URL.
6. Type `make` to build the site and then run `make serve` to view your site.
7. Keep adding content. See below for instructions for each of the various sections.
8. Periodically pull from the upstream repository: `git pull upstream master`.

[Python]: https://www.python.org/
[Fork]: https://github.com/uwsampa/research-group-web/fork


Publication List
----------------

The list of publications is in `bib/pubs.bib`. Typing `make` will generate `pubs.html`, which contains a pretty, sorted HTML-formatted list of papers. The public page, `publications.html`, also has a link to download the original BibTeX.


News Items and Blog Posts
-------------------------

For both long-form blog posts and short news updates, we use Jekyll's blogging system. To post a new item of either type, you create a file in the `_posts` directory using the naming convention `YYYY-MM-DD-title-for-url.md`. The date part of the filename always matters; the title part is currently only used for full blog posts (but is still required for news updates).

The file must begin with [YAML front matter][yfm]. For news updates, use this:

    ---
  `   layout: post
    shortnews: true
    ---

For full blog posts, use this format:

    ---
    layout: post
    title:  "Some Great Title Here"
    ---

And concoct a page title for your post. The body of the post goes after the `---` in either case.

You can also customize the icon that is displayed on the news feed. By default it's `newspaper-o`. We use icons from the [FontAwesome][fa] icon set.

[yfm]: http://jekyllrb.com/docs/frontmatter/
[fa]: http://fontawesome.io/icons/

Projects
--------

To create a project, just create a markdown file in the `_projects` folder. Here are the things you can put in the YAML frontmatter:

- `title:` The project title.
- `notitle:` Set this to `true` if you don't want a title displayed on the project card. Optional.
- `description:` The text shown in the project card. It supports markdown.
- `people:` The people working on the project. This is a list of keys from the `_data/people.yml` file.
- `layout: project` This sets the layout of the actual project page. It should be set to `project`.
- `image:` The URL of an image for the project. This is shown on both the project page and the project card. Optional.
- `last-updated:` Date in the format of `YYYY-MM-DD`. The project cards are sorted by this, most recent first.
- `status: inactive` Set this to `inactive` if don't want the project to appear on the front page. Just ignore it otherwise.
- `link:` Set this to an external URL if this project has a page somewhere else on the web. If you don't have a `link:`, then the content of this markdown file (below the YAML frontmatter) will be this project's page.
- `no-link: true` Set this if you just don't want a project page for your project.

Personnel
---------

People are listed in a [YAML][] file in `_data/people.yml`. You can list the name, link, bio, and role of each person. Roles (e.g., "Faculty", "Staff", and "Students") are defined in `_config.yml`.

[YAML]: https://en.wikipedia.org/wiki/YAML


Building
--------

The requirements for building the site are:

* [Jekyll][]: run `gem install jekyll`
* [bibble][]: available on `pip`
* ssh and rsync, only if you want to deploy directly.

`make` compiles the bibliography and the website content to the `_site`
directory. To preview the site, run `jekyll serve`` and head to
http://0.0.0.0:5000.


Deploying to Your Sever
-----------------------

To set up deployments, edit the Makefile and look for the lines where `HOST` and `DIR` are defined. Change these to the host where your HTML files should be copied to.

To upload a new version of the site via rsync over ssh, type `make deploy`. A web hook does this automatically when you push to GitHub. Be aware that the Makefile is configured to have rsync delete stray files from the destination directory.

[Jekyll]: http://jekyllrb.com/
[bibble]: https://github.com/sampsyo/bibble/
