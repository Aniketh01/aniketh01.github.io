---
layout: page
title: "Home"
class: home
---

<div class="columns" markdown="1">

<div class="intro" markdown="1">

# Hi, I'm Aniketh Girish

<p class="hiring-note"><b>I'm open to full-time opportunities in the next 6~12 months, feel free to <a href="mailto:aniketh.girish@imdea.org">contact me</a> if you think I'd be a fit!</b></p>

I'm a Postdoctoral Researcher at the [IMDEA Networks Institute](https://networks.imdea.org/) in Madrid, Spain. I completed my Ph.D. *Cum Laude* at IMDEA Networks Institute in 2025, advised by [Dr. Narseo Vallina-Rodriguez](https://networks.imdea.org/team/imdea-networks-team/people/narseo-vallina-rodriguez/).
My research falls at the intersection of (1) hybrid black-box testing, (2) empirical analysis of covert privacy risks in smart home and mobile ecosystems, and (3) regulatory compliance. I have published in top peer-reviewed venues (e.g., PETS, IMC, USENIX Security), and Q1 journals (IEEE Transactions on Software Engineering). I got the Best Poster Award at the TMA'22 Ph.D. school for my novel approach to IoT testing.

During my Ph.D., I was a visiting researcher at Northeastern University's Cybersecurity and Privacy Institute (USA), advised by Prof. David Choffnes. Prior to that, I held research positions at the Rochester Institute of Technology (USA) and IIJ Innovation Institute (Japan). I was selected twice for Google Summer of Code, contributing to KDE and GNU Linux, and spent a summer at Ben-Gurion University (Israel) exploring applications of machine learning in cybersecurity.

</div>

<div class="me" markdown="1">
<picture>
  <img
    src='/images/aniketh2.jpg'
    alt='Aniketh Girish'/>
</picture>

{:.no-list}
* <a href="mailto:{{ site.email }}">{{ site.email }}</a>
</div>

</div>

<div class="impact-banner" markdown="1">

My measurement-driven research has led to concrete technical impact across platforms and ecosystems. It directly influenced platform practices — Google introduced a local-network permission in Android 16 and a localhost permission in Android 17 as a direct result of my work — and prompted privacy redesigns by major IoT vendors (e.g., Philips, Apple, TP-Link, Google) and the removal of dozens of privacy-invasive apps and SDKs from the Google Play Store. Chrome, Firefox, and DuckDuckGo deployed browser-level mitigations, while uBlock Origin and AdGuard adopted tracking protections based on our findings. The work advanced and expedited deployment of the W3C Local Network Access (LNA) standard.

At the policy and enforcement level, the Spanish Prime Minister cited our research to announce a parliamentary investigation into Meta, before which we testified. U.S. Congress members cited the research in a formal inquiry to Meta leadership. Class action lawsuits were filed in the U.S., Canada, and Germany. Our disclosures to European regulators (EDPS, AEPD, CNIL, EDPB, UK CMA) prompted enforcement discussions. The work has been covered by 100+ international media outlets including the Washington Post, Wired, Ars Technica, El Pa&iacute;s, and Sky News, and engaged by civil society organizations (EFF, Privacy International).

More details are enclosed in my [CV]({{ "/assets/Aniketh_CV.pdf" | relative_url }}).

</div>


## Featured Publications

<div class="featured-publications">
  {% for pub in site.data.publications %}
    {% if pub.highlight %}
      <a href="{{ pub.pdf }}" class="publication">
        <strong>{{ pub.title }}</strong>
        <span class="authors">{% for author in pub.authors %}{{ author }}{% if pub.co_first_authors contains author %}<sup>*</sup>{% endif %}{% unless forloop.last %}, {% endunless %}{% endfor %}</span>{% if pub.co_first_authors %} <span class="co-first-note"><sup>*</sup> Co-first authors</span>{% endif %}.
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


<div class="news" markdown="1">

## News

<ul>
{% for news in site.data.news limit:8 %}
  {% include news.html news=news %}
{% endfor %}
</ul>

<details class="news-more">
<summary>Show older news</summary>
<ul>
{% for news in site.data.news offset:8 %}
  {% include news.html news=news %}
{% endfor %}
</ul>
</details>

</div>
