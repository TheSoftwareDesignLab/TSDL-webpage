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
