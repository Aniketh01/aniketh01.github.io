---
layout: page
title: "Home"
class: home
---




# Hi, I'm Aniketh Girish

<div class="columns" markdown="1">

<div class="intro" markdown="1">

<!-- <p style="color:red;"><i>From January 2020 onwards, I'm actively looking for Research Associate/Assitant/Internship position to exploring the general areas of networking, measurements, internet protocols and it's security extensions. <b>Email me</b> if you find an overlap of interests!</i></p> -->

I am a first year CS PhD student in [Internet Analytics group](http://people.networks.imdea.org/~narseo_vallina/research.html) at the IMDEA Networks Institute and University Carlos III de Madrid, Madrid, Spain advised by [Dr. Narseo Vallina-Rodriguez](http://www1.icsi.berkeley.edu/~narseo/). I emperically measure and analysis the privacy and security risks of IoT and Mobile eco-system with a focus on data use.

Prior to joining IMDEA, I was a Remote Research Intern at Rochester Institute of Technology, USA collaborating with the awesome [Tijay](https://taejoong.github.io) and also a Research Associate Intern at the IIJ Innovation Institute (IIJ-II), collaborating with the amazing [Hajime](https://www.iij-ii.co.jp/members/tazaki.html). My work was focused on Email and DNS Security extensions, and Process-based Isolation with Linux Unikernels.

<!-- I'm a Final year bachelor student at [Amrita Vishwa Vidyapeetham](https://www.amrita.edu/), working on Internet protocols, security and privacy. My research interests lie in the intersection of systems and networks in the broadest sense with a particular focus on QoE, security, privacy, measurement and deployment of Internet protocols. -->

<!-- During my bachelor, I spend most of my time in [amFOSS](https://amfoss.in) advised by [Vipin P](https://www.linkedin.com/in/vipin-pavithran?originalSubdomain=in). amFOSS, a student-run community where like-minded people gather together to learn, solve and have tonnes of fun working on computer science problems and on exciting projects.  -->
</div>

<div class="me" markdown="1">
<picture>
  <!-- <source srcset='/images/dominik_berlin.webp' type='image/webp' /> -->
  <img
    src='/images/aniketh2.jpg'
    alt='Aniketh Girish'/>
</picture>

{:.no-list}
* <a href="mailto:{{ site.email }}">{{ site.email }}</a>
</div>

</div>
<!-- I have been a Google Summer of Code student twice with KDE in 2017 and GNU Linux in 2018. As a Google summer of code project in 2018, I implemented DNS over HTTPS into GNU Wget2 resolvers. Being an open-source fanatic, My bachelor thesis which comprises of a QoE study to see if QUIC-enabled video yields to perceivable differences or not. Hence, to bring perceivable differences in streaming with QUIC, introducing a custom version of QUIC which reduces HoL blocking and significantly more. All this into VLC, nevertheless! Moreover, I'm working on an implementation of Record Layer separation in gnuTLS to serve as QUIC TLS API. -->

<!-- I have been lucky to collaborate with awesome researchers around the globe. [Tijay](https://taejoong.github.io), [Hajime](https://www.iij-ii.co.jp/members/tazaki.html) being the few of them. Thankyou for being the wonderful mentors :) -->

I graduated from [Amrita Vishwa Vidyapeetham](https://www.amrita.edu/) in 2020, with a major in Computer Science. I was selected twice as a Google Summer of Code student, with KDE (2017) and GNU Linux (2018). Parallel to my second GSoC, I spend my summer at Ben Gurion University, Israel as a summer exchange student studying the use of Machine Learning with cyber security and business intelligence.

I was also an active member of [amFOSS](https://amfoss.in) club advised by [Vipin P](https://www.linkedin.com/in/vipin-pavithran?originalSubdomain=in). amFOSS is a student-run community where like-minded people gather together to learn, solve and have tonnes of fun working on computer science problems and on exciting projects.

<!-- More Details are enclosed in my [CV]({{ "/assets/Aniketh_CV.pdf" | relative_url }}). Detailed description of my interest could be found in [here]({{ "/assets/Cover_letter.pdf" | relative_url }}). -->


## Featured Publications

<div class="featured-publications">
  {% for pub in site.data.publications %}
    {% if pub.highlight %}
      <a href="{{ pub.pdf }}" class="publication">
        <strong>{{ pub.title }}</strong>
        <span class="authors">{% for author in pub.authors %}{{ author }}{% unless forloop.last %}, {% endunless %}{% endfor %}</span>.
        <i>{{ pub.venue }}, {{ pub.year }}</i>.
        {% for award in pub.awards %}<br/><span class="award"><i class="fas fa-{% if award == "Best Paper Award" %}trophy{% else %}award{% endif %}" aria-hidden="true"></i> {{ award }}</span>{% endfor %}
      </a>
    {% endif %}
  {% endfor %}
</div>

<a href="{{ "/publications/" | relative_url }}" class="button">
  <i class="fas fa-chevron-circle-right"></i>
  Show All Publications
</a>

## Featured Projects

<div class="featured-projects">
  {% assign sorted_projects = site.data.projects | sort: 'highlight' %}
  {% for project in sorted_projects %}
    {% if project.highlight %}
      {% include project.html project=project %}
    {% endif %}
  {% endfor %}
</div>
<a href="{{ "/projects/" | relative_url }}" class="button">
  <i class="fas fa-chevron-circle-right"></i>
  Show More Projects
</a> 


<div class="news-travel" markdown="1">

<div class="news" markdown="1">
## News

<ul>
{% for news in site.data.news %}
  {% include news.html news=news %}
{% endfor %}
</ul>

</div>

<!-- <div class="travel" markdown="1">
## Travel

<table>
<tbody>
{% assign future_travel = site.data.travel | where_exp:'item','item.start == null' %}
{% for travel in future_travel %}
  {% include travel.html travel=travel %}
{% endfor %}
{% assign sorted_travel = site.data.travel | where_exp:'item','item.start' | sort: 'start' | reverse %}
{% for travel in sorted_travel limit:14 %}
  {% include travel.html travel=travel %}
{% endfor %}
</tbody>
</table>

</div> -->

</div>
