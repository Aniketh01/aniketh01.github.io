---
layout: page
title: Impact
permalink: /impact/
class: impact
---

<div class="ripple-opening">
  <p class="ripple-narrative">We exposed how Meta and Yandex covertly tracked Android users' browsing via localhost, and how smart home protocols leak device metadata that bypasses platform permissions. The findings triggered a cascade of real-world changes&nbsp;&mdash; from code patches to congressional hearings.</p>
</div>

<div class="impact-stats">
  <div class="stat-card">
    <div class="stat-number" data-target="100" data-suffix="+">0</div>
    <div class="stat-label">Media outlets</div>
  </div>
  <div class="stat-card">
    <div class="stat-number" data-target="20" data-suffix="+">0</div>
    <div class="stat-label">IoT vendors patched</div>
  </div>
  <div class="stat-card">
    <div class="stat-number" data-target="3" data-suffix="">0</div>
    <div class="stat-label">Countries with lawsuits</div>
  </div>
  <div class="stat-card">
    <div class="stat-number" data-target="6" data-suffix="">0</div>
    <div class="stat-label">Browser/OS mitigations</div>
  </div>
</div>

<!-- Ring 1 — Code Changes (innermost, darkest) -->
<section class="ripple-ring ring-1">
  <div class="ring-inner">
    <div class="ring-label"><span class="ring-num">01</span> Code Changes</div>
    <p class="ring-subtitle">Immediate technical fixes triggered by disclosure</p>
    <div class="ring-items">
      <div class="ring-item">
        <i class="fa-solid fa-ban"></i>
        <div><strong>Meta &amp; Yandex</strong> terminated the localhost abuse on the day of public disclosure.</div>
      </div>
      <div class="ring-item">
        <i class="fa-solid fa-shield-halved"></i>
        <div><strong>uBlock Origin, AdGuard, DuckDuckGo</strong> enhanced blocklists to protect users.</div>
      </div>
      <div class="ring-item">
        <i class="fa-solid fa-microchip"></i>
        <div><strong>20+ IoT vendors</strong> (Philips, Google, TP-Link, Apple) redesigned identifier schemes.</div>
      </div>
      <div class="ring-item">
        <i class="fa-solid fa-lock"></i>
        <div><strong>VPN vulnerability</strong> and cross-profile tracking vectors disclosed.</div>
      </div>
    </div>
  </div>
</section>

<!-- Ring 2 — Platform Policy -->
<section class="ripple-ring ring-2">
  <div class="ring-inner">
    <div class="ring-label"><span class="ring-num">02</span> Platform Policy</div>
    <p class="ring-subtitle">OS and browser-level changes protecting billions of users</p>
    <div class="ring-items">
      <div class="ring-item">
        <i class="fa-brands fa-android"></i>
        <div><strong>Android 16</strong> &mdash; dedicated local network permission (IoT work).</div>
      </div>
      <div class="ring-item">
        <i class="fa-brands fa-android"></i>
        <div><strong>Android 17</strong> &mdash; dedicated localhost permission (localhost work).</div>
      </div>
      <div class="ring-item">
        <i class="fa-brands fa-chrome"></i>
        <div><strong>Chrome 137</strong> &mdash; access restrictions blocking localhost abuse (influences all Chromium browsers).</div>
      </div>
      <div class="ring-item">
        <i class="fa-brands fa-firefox-browser"></i>
        <div><strong>Firefox</strong> &mdash; <a href="https://bugzilla.mozilla.org/show_bug.cgi?id=1969916">deployed localhost access restrictions</a>.</div>
      </div>
      <div class="ring-item">
        <i class="fa-brands fa-safari"></i>
        <div><strong>WebKit</strong> &mdash; <a href="https://bugs.webkit.org/show_bug.cgi?id=171934#c111">engaged with findings</a> for Safari protections.</div>
      </div>
      <div class="ring-item">
        <i class="fa-solid fa-globe"></i>
        <div><strong>W3C</strong> &mdash; advanced Local Network Access (LNA) standard; disclosed bypass vectors.</div>
      </div>
      <div class="ring-item">
        <i class="fa-solid fa-diagram-project"></i>
        <div><strong>IETF</strong> &mdash; invited to present at IETF PEARG 123.</div>
      </div>
      <div class="ring-item">
        <i class="fa-brands fa-google-play"></i>
        <div><strong>Google Play</strong> &mdash; dozens of privacy-invasive apps and SDKs removed.</div>
      </div>
    </div>
  </div>
</section>

<!-- Ring 3 — Regulation & Law -->
<section class="ripple-ring ring-3">
  <div class="ring-inner">
    <div class="ring-label"><span class="ring-num">03</span> Regulation &amp; Law</div>
    <p class="ring-subtitle">Government and legal action across three continents</p>
    <div class="ring-items">
      <div class="ring-item">
        <i class="fa-solid fa-landmark-dome"></i>
        <div><strong>Spanish Prime Minister</strong> cited the research, launching a parliamentary investigation into Meta. We <strong>testified before the Spanish Congress</strong>.</div>
      </div>
      <div class="ring-item">
        <i class="fa-solid fa-landmark"></i>
        <div><strong>U.S. House of Representatives</strong> members cited the research in a formal inquiry to Meta leadership.</div>
      </div>
      <div class="ring-item">
        <i class="fa-solid fa-gavel"></i>
        <div><strong>Class actions</strong> filed in the U.S. (<a href="https://www.pacermonitor.com/public/case/58359378/Rose_v_Meta_Platforms,_Inc">Rose v. Meta</a>, Carroll, Zaveeri), Canada, and Germany.</div>
      </div>
      <div class="ring-item">
        <i class="fa-solid fa-building-columns"></i>
        <div>Disclosures to <strong>CNIL, EDPS, AEPD, EDPB, UK CMA, European Commission</strong> &mdash; enforcement discussions ongoing.</div>
      </div>
    </div>
  </div>
</section>

<!-- Ring 4 — Public Discourse (outermost, lightest) -->
<section class="ripple-ring ring-4">
  <div class="ring-inner">
    <div class="ring-label"><span class="ring-num">04</span> Public Discourse</div>
    <p class="ring-subtitle">Media, civil society, and public debate</p>

    <h4 class="ring-sub-heading">Press Coverage</h4>
    <div class="press-grid">
      <a class="press-card" href="https://www.washingtonpost.com/technology/2025/06/06/meta-privacy-facebook-instagram/"><span class="press-outlet">Washington Post</span></a>
      <a class="press-card" href="https://arstechnica.com/security/2025/06/meta-and-yandex-are-de-anonymizing-android-users-web-browsing-identifiers/"><span class="press-outlet">Ars Technica</span></a>
      <a class="press-card" href="https://elpais.com/tecnologia/2025-06-03/este-es-el-metodo-oculto-con-el-que-meta-rastrea-sin-permiso-la-navegacion-en-moviles-tambien-en-modo-incognito-o-con-vpn.html"><span class="press-outlet">El Pa&iacute;s</span></a>
      <a class="press-card" href="https://www.schneier.com/blog/archives/2025/06/new-way-to-track-covertly-android-users.html"><span class="press-outlet">Schneier on Security</span></a>
      <a class="press-card" href="https://daringfireball.net/linked/2025/06/04/meta-and-yandexs-local-mess-exploit-seemingly-only-works-on-android"><span class="press-outlet">Daring Fireball</span></a>
      <a class="press-card" href="https://www.demorgen.be/nieuws/het-sluwe-achterpoortje-waarmee-u-online-gevolgd-wordt-meta-deed-er-alles-aan-om-dit-verborgen-te-houden~ba3bb620/"><span class="press-outlet">De Morgen</span></a>
      <a class="press-card" href="https://www.deutschlandfunk.de/app-attacke-europaeische-forscher-decken-groben-privacy-verstoss-von-meta-auf-100.html"><span class="press-outlet">Deutschlandfunk</span></a>
      <a class="press-card" href="https://www.techdirt.com/2025/06/13/meta-busted-spying-on-android-users-in-extremely-creepy-new-way-then-lies-about-it/"><span class="press-outlet">Techdirt</span></a>
      <a class="press-card" href="https://tweakers.net/nieuws/235760/meta-had-vanaf-september-inzage-in-surfgedrag-van-android-gebruikers.html"><span class="press-outlet">Tweakers</span></a>
      <a class="press-card" href="https://www.cpomagazine.com/data-privacy/meta-and-yandex-accused-of-using-android-loophole-for-surreptitious-user-tracking/"><span class="press-outlet">CPO Magazine</span></a>
      <a class="press-card" href="https://securityboulevard.com/2025/06/meta-local-mess-richixbw/"><span class="press-outlet">Security Boulevard</span></a>
      <a class="press-card" href="https://datanews.knack.be/nieuws/security/privacy/facebook-en-yandex-apps-weten-welke-sites-je-bezoekt-ook-incognito/"><span class="press-outlet">Knack Data News</span></a>
      <a class="press-card" href="https://www.abc.es/tecnologia/meta-yandex-consiguen-datos-concretos-sobre-tus-20250604174148-nt.html"><span class="press-outlet">ABC</span></a>
      <a class="press-card" href="https://www.dailykos.com/stories/2025/7/4/2331483/-Want-Meta-to-stop-spying-on-you-Getting-off-Facebook-is-NOT-enough"><span class="press-outlet">Daily Kos</span></a>
      <a class="press-card" href="https://risky.biz/risky-bulletin-security-firms-will-attempt-to-clean-up-their-own-mess-apt-name-taxonomies/"><span class="press-outlet">Risky Business</span></a>
    </div>

    <h4 class="ring-sub-heading">Civil Society &amp; Commentary</h4>
    <div class="press-grid">
      <a class="press-card civil" href="https://www.eff.org/deeplinks/2025/06/protect-yourself-metas-latest-attack-privacy"><span class="press-outlet">EFF Blog</span></a>
      <a class="press-card civil" href="https://www.eff.org/effector/37/7"><span class="press-outlet">EFF Newsletter</span></a>
      <a class="press-card civil" href="https://privacyinternational.org/long-read/5621/meta-and-yandex-break-security-save-their-business-model"><span class="press-outlet">Privacy International</span></a>
      <a class="press-card civil" href="https://medium.com/enrique-dans/its-time-to-shut-down-meta-and-prosecute-mark-zuckerberg-5a8d22031426"><span class="press-outlet">Enrique Dans</span></a>
      <a class="press-card civil" href="https://www.zeropartydata.es/p/localhost-tracking-explained-it-could"><span class="press-outlet">Zero Party Data</span></a>
      <a class="press-card civil" href="https://www.youtube.com/watch?v=q6BKgOJD7fU&t=1295s"><span class="press-outlet"><i class="fa-brands fa-youtube"></i> Podcast (40 min)</span></a>
      <a class="press-card civil" href="https://www.youtube.com/watch?v=-dBYjA-v4XQ"><span class="press-outlet"><i class="fa-brands fa-youtube"></i> Video</span></a>
    </div>
  </div>
</section>

<!-- Underlying Research -->
<section class="ripple-research">
  <h2 class="ring-label research-label"><span class="ring-num"><i class="fa-solid fa-flask"></i></span> Underlying Research</h2>
  <div class="research-cards">
    <div class="research-card">
      <div class="research-venue">USENIX Security 2026</div>
      <div class="research-title">Bridges to Self: Silent Web-to-App Tracking on Mobile via Localhost</div>
      <div class="research-authors">T. Vlummens*, <strong>A. Girish*</strong>, N. Weerasekara, F. Zuiderveen Borgesius, G. Acar, N. Vallina Rodriguez</div>
      <a href="https://localmess.github.io/" class="research-link"><i class="fa-solid fa-arrow-up-right-from-square"></i> localmess.github.io</a>
    </div>
    <div class="research-card">
      <div class="research-venue">PoPETs 2025</div>
      <div class="research-title">The Effect of Platform Policies on App Privacy Compliance</div>
      <div class="research-authors">N. Alomar, J. Reardon, <strong>A. Girish</strong>, N. Vallina-Rodriguez, S. Egelman</div>
      <a href="https://petsymposium.org/popets/2025/popets-2025-0094.pdf" class="research-link"><i class="fa-solid fa-file-pdf"></i> Paper</a>
    </div>
    <div class="research-card">
      <div class="research-venue">PoPETs 2025</div>
      <div class="research-title">Your Signal, Their Data: An Empirical Privacy Analysis of Wireless-Scanning SDKs in Android</div>
      <div class="research-authors"><strong>A. Girish</strong>, J. Reardon, J. Tapiador, S. Matic, N. Vallina-Rodriguez</div>
      <a href="https://petsymposium.org/popets/2025/popets-2025-0103.pdf" class="research-link"><i class="fa-solid fa-file-pdf"></i> Paper</a>
    </div>
    <div class="research-card">
      <div class="research-venue">IMC 2023</div>
      <div class="research-title">In the Room Where It Happens: Characterizing Local Communication and Threats in Smart Homes</div>
      <div class="research-authors"><strong>A. Girish*</strong>, T. Hu*, V. Prakash et al.</div>
      <a href="https://doi.org/10.1145/3618257.3624830" class="research-link"><i class="fa-solid fa-arrow-up-right-from-square"></i> DOI</a>
    </div>
  </div>
</section>

<div class="impact-footer-note">
  All research artifacts are publicly released following open science principles. Achieved within a PhD completed <em>Cum Laude</em> at IMDEA Networks / UC3M.
</div>

<script>
document.addEventListener('DOMContentLoaded', function() {
  // Animate stat counters on scroll
  var counters = document.querySelectorAll('.stat-number');
  var speed = 60;

  function animateCounter(counter) {
    var target = +counter.getAttribute('data-target');
    var suffix = counter.getAttribute('data-suffix') || '';
    var increment = Math.max(1, Math.floor(target / speed));
    var current = 0;

    function updateCount() {
      current += increment;
      if (current >= target) {
        counter.innerText = target + suffix;
        return;
      }
      counter.innerText = current;
      requestAnimationFrame(updateCount);
    }
    updateCount();
  }

  var counterObserver = new IntersectionObserver(function(entries) {
    entries.forEach(function(entry) {
      if (entry.isIntersecting) {
        animateCounter(entry.target);
        counterObserver.unobserve(entry.target);
      }
    });
  }, { threshold: 0.5 });

  counters.forEach(function(counter) { counterObserver.observe(counter); });

  // Fade-in rings on scroll
  var rings = document.querySelectorAll('.ripple-ring, .ripple-research');
  var ringObserver = new IntersectionObserver(function(entries) {
    entries.forEach(function(entry) {
      if (entry.isIntersecting) {
        entry.target.classList.add('ring-visible');
        ringObserver.unobserve(entry.target);
      }
    });
  }, { threshold: 0.15 });

  rings.forEach(function(ring) { ringObserver.observe(ring); });
});
</script>
