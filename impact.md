---
layout: page
title: Impact
permalink: /impact/
class: impact
---

<div class="impact-hero">
  <p class="impact-tagline">Research that changes platforms, policies, and protections for billions of users.</p>
</div>

<div class="impact-stats">
  <div class="stat-card">
    <div class="stat-number" data-target="100">0</div>
    <div class="stat-label">Media outlets</div>
  </div>
  <div class="stat-card">
    <div class="stat-number" data-target="20">0</div>
    <div class="stat-label">IoT vendors patched</div>
  </div>
  <div class="stat-card">
    <div class="stat-number" data-target="3">0</div>
    <div class="stat-label">Countries with lawsuits</div>
  </div>
  <div class="stat-card">
    <div class="stat-number" data-target="6">0</div>
    <div class="stat-label">Browser/OS mitigations</div>
  </div>
</div>

<!-- Topic selector -->
<div class="topic-nav">
  <button class="topic-btn active" data-topic="all">All Impact</button>
  <button class="topic-btn" data-topic="localhost">
    <span class="topic-dot dot-localhost"></span> Localhost Tracking
  </button>
  <button class="topic-btn" data-topic="iot">
    <span class="topic-dot dot-iot"></span> Smart Home / IoT
  </button>
  <button class="topic-btn" data-topic="wireless">
    <span class="topic-dot dot-wireless"></span> Wireless SDKs
  </button>
  <button class="topic-btn" data-topic="childapps">
    <span class="topic-dot dot-childapps"></span> Child-Directed Apps
  </button>
</div>

<!-- ============================================ -->
<!-- LOCALHOST TRACKING -->
<!-- ============================================ -->
<div class="topic-block" data-topics="localhost">

<div class="topic-header localhost-header">
  <div class="topic-header-content">
    <h2>Localhost Tracking</h2>
    <p class="topic-subtitle">Silent web-to-app tracking on mobile via localhost &mdash; exposing how Meta and Yandex covertly tracked Android users' browsing across apps.</p>
    <div class="topic-paper">
      <span class="venue-badge">USENIX Security 2026</span>
      <span class="paper-title">Bridges to Self: Silent Web-to-App Tracking on Mobile via Localhost</span>
      <a href="https://localmess.github.io/" class="paper-link"><i class="fa-solid fa-arrow-up-right-from-square"></i></a>
    </div>
  </div>
</div>

<div class="topic-impact-sections">

<div class="impact-col">
<h4><i class="fa-solid fa-landmark"></i> Regulatory &amp; Legislative</h4>
<ul class="impact-list">
  <li class="impact-highlight"><span class="flag">Spain</span> The <strong>Spanish Prime Minister</strong> cited the research to announce a parliamentary investigation into Meta. We <strong>testified</strong> before the Spanish Congress commission.</li>
  <li class="impact-highlight"><span class="flag">U.S.</span> Members of the <strong>U.S. House of Representatives</strong> cited the research in a formal inquiry to Meta leadership.</li>
  <li><span class="flag">U.S.</span> Class actions: <a href="https://www.pacermonitor.com/public/case/58359378/Rose_v_Meta_Platforms,_Inc">Rose v. Meta</a>, Carroll, Zaveeri.</li>
  <li><span class="flag">Canada</span> <span class="flag">Germany</span> Additional class actions filed.</li>
  <li><span class="flag">EU</span> Disclosures to CNIL, EDPS, AEPD, EDPB, UK CMA, and the European Commission.</li>
</ul>
</div>

<div class="impact-col">
<h4><i class="fa-solid fa-shield-halved"></i> Platform &amp; Technical</h4>
<ul class="impact-list">
  <li><span class="pill pill-os">Android 17</span> New localhost permission to prevent platform-wide abuse.</li>
  <li><span class="pill pill-browser">Chrome 137</span> Access restrictions blocking localhost abuse.</li>
  <li><span class="pill pill-browser">Firefox</span> <a href="https://bugzilla.mozilla.org/show_bug.cgi?id=1969916">Localhost access restrictions</a>.</li>
  <li><span class="pill pill-browser">WebKit</span> <a href="https://bugs.webkit.org/show_bug.cgi?id=171934#c111">Engaged with findings</a>.</li>
  <li><span class="pill pill-std">W3C</span> Advanced the Local Network Access (LNA) standard. Disclosed bypass vectors.</li>
  <li><span class="pill pill-std">IETF</span> Invited to present at IETF PEARG 123.</li>
  <li><span class="pill pill-tool">Privacy Tools</span> <a href="https://github.com/uBlockOrigin/uAssets/blob/f7b32ede2447603d889685925d2be05cc505f0f1/filters/privacy.txt#L1544-L1545">uBlock Origin</a>, <a href="https://adguard.com/en/blog/meta-yandex-abuse-localhost-to-track-users.html">AdGuard</a>, DuckDuckGo enhanced blocklists.</li>
</ul>
</div>

<div class="impact-col">
<h4><i class="fa-solid fa-building"></i> Industry Response</h4>
<ul class="impact-list">
  <li>Meta and Yandex <strong>terminated the abuse on the day of public disclosure</strong>.</li>
  <li>VPN vulnerability and cross-profile tracking vectors disclosed.</li>
</ul>
</div>

</div>

<details class="press-details">
<summary><i class="fa-solid fa-newspaper"></i> Press Coverage &amp; Commentary <span class="press-count">15+ outlets</span></summary>
<div class="press-grid">
<a class="press-item" href="https://www.washingtonpost.com/technology/2025/06/06/meta-privacy-facebook-instagram/"><span class="press-outlet">Washington Post</span><span class="press-title">Meta found a new way to violate your privacy</span></a>
<a class="press-item" href="https://arstechnica.com/security/2025/06/meta-and-yandex-are-de-anonymizing-android-users-web-browsing-identifiers/"><span class="press-outlet">Ars Technica</span><span class="press-title">Meta and Yandex are de-anonymizing Android users</span></a>
<a class="press-item" href="https://elpais.com/tecnologia/2025-06-03/este-es-el-metodo-oculto-con-el-que-meta-rastrea-sin-permiso-la-navegacion-en-moviles-tambien-en-modo-incognito-o-con-vpn.html"><span class="press-outlet">El Pa&iacute;s</span><span class="press-title">The hidden method Meta uses to track mobile browsing</span></a>
<a class="press-item" href="https://www.schneier.com/blog/archives/2025/06/new-way-to-track-covertly-android-users.html"><span class="press-outlet">Schneier on Security</span><span class="press-title">New Way to Covertly Track Android Users</span></a>
<a class="press-item" href="https://daringfireball.net/linked/2025/06/04/meta-and-yandexs-local-mess-exploit-seemingly-only-works-on-android"><span class="press-outlet">Daring Fireball</span><span class="press-title">Meta and Yandex's LocalMess exploit on Android</span></a>
<a class="press-item" href="https://www.demorgen.be/nieuws/het-sluwe-achterpoortje-waarmee-u-online-gevolgd-wordt-meta-deed-er-alles-aan-om-dit-verborgen-te-houden~ba3bb620/"><span class="press-outlet">De Morgen</span><span class="press-title">Het sluwe achterpoortje waarmee u online gevolgd wordt</span></a>
<a class="press-item" href="https://www.deutschlandfunk.de/app-attacke-europaeische-forscher-decken-groben-privacy-verstoss-von-meta-auf-100.html"><span class="press-outlet">Deutschlandfunk <i class="fa-solid fa-microphone"></i></span><span class="press-title">Forscher decken Privacy-Versto&szlig; von Meta auf</span></a>
<a class="press-item" href="https://www.techdirt.com/2025/06/13/meta-busted-spying-on-android-users-in-extremely-creepy-new-way-then-lies-about-it/"><span class="press-outlet">Techdirt</span><span class="press-title">Meta busted spying on Android users in creepy new way</span></a>
<a class="press-item" href="https://tweakers.net/nieuws/235760/meta-had-vanaf-september-inzage-in-surfgedrag-van-android-gebruikers.html"><span class="press-outlet">Tweakers</span><span class="press-title">Meta had inzage in surfgedrag van Android-gebruikers</span></a>
<a class="press-item" href="https://securityboulevard.com/2025/06/meta-local-mess-richixbw/"><span class="press-outlet">Security Boulevard</span><span class="press-title">Meta's LocalMess tracking technique</span></a>
<a class="press-item" href="https://www.cpomagazine.com/data-privacy/meta-and-yandex-accused-of-using-android-loophole-for-surreptitious-user-tracking/"><span class="press-outlet">CPO Magazine</span><span class="press-title">Meta and Yandex accused of using Android loophole</span></a>
<a class="press-item" href="https://datanews.knack.be/nieuws/security/privacy/facebook-en-yandex-apps-weten-welke-sites-je-bezoekt-ook-incognito/"><span class="press-outlet">Knack Data News</span><span class="press-title">Facebook en Yandex apps weten welke sites je bezoekt</span></a>
<a class="press-item" href="https://www.abc.es/tecnologia/meta-yandex-consiguen-datos-concretos-sobre-tus-20250604174148-nt.html"><span class="press-outlet">ABC</span><span class="press-title">Meta y Yandex consiguen datos concretos sobre tus h&aacute;bitos</span></a>
<a class="press-item" href="https://www.dailykos.com/stories/2025/7/4/2331483/-Want-Meta-to-stop-spying-on-you-Getting-off-Facebook-is-NOT-enough"><span class="press-outlet">Daily Kos</span><span class="press-title">Getting off Facebook is NOT enough</span></a>
</div>

<h5>Civil Society &amp; Commentary</h5>
<div class="press-grid">
<a class="press-item" href="https://www.eff.org/deeplinks/2025/06/protect-yourself-metas-latest-attack-privacy"><span class="press-outlet">EFF</span><span class="press-title">Protect Yourself from Meta's Latest Attack on Privacy</span></a>
<a class="press-item" href="https://privacyinternational.org/long-read/5621/meta-and-yandex-break-security-save-their-business-model"><span class="press-outlet">Privacy International</span><span class="press-title">Meta and Yandex break security to save their business model</span></a>
<a class="press-item" href="https://medium.com/enrique-dans/its-time-to-shut-down-meta-and-prosecute-mark-zuckerberg-5a8d22031426"><span class="press-outlet">Enrique Dans</span><span class="press-title">It's time to shut down Meta</span></a>
<a class="press-item" href="https://www.zeropartydata.es/p/localhost-tracking-explained-it-could"><span class="press-outlet">Zero Party Data</span><span class="press-title">Localhost tracking &mdash; est. &euro;32B in fines</span></a>
<a class="press-item" href="https://www.youtube.com/watch?v=q6BKgOJD7fU&t=1295s"><span class="press-outlet"><i class="fa-brands fa-youtube"></i> Podcast</span><span class="press-title">In-depth discussion (40 min)</span></a>
<a class="press-item" href="https://www.youtube.com/watch?v=-dBYjA-v4XQ"><span class="press-outlet"><i class="fa-brands fa-youtube"></i> Video</span><span class="press-title">Video coverage</span></a>
</div>
</details>

</div>

<!-- ============================================ -->
<!-- SMART HOME / IoT -->
<!-- ============================================ -->
<div class="topic-block" data-topics="iot">

<div class="topic-header iot-header">
  <div class="topic-header-content">
    <h2>Smart Home &amp; IoT Privacy</h2>
    <p class="topic-subtitle">Exposing how local network protocols in smart homes violate platform access control assumptions &mdash; apps bypass Android's permission model to harvest device metadata.</p>
    <div class="topic-paper">
      <span class="venue-badge">IMC 2023</span>
      <span class="paper-title">In the Room Where It Happens: Characterizing Local Communication and Threats in Smart Homes</span>
      <a href="https://doi.org/10.1145/3618257.3624830" class="paper-link"><i class="fa-solid fa-arrow-up-right-from-square"></i></a>
    </div>
  </div>
</div>

<div class="topic-impact-sections">

<div class="impact-col">
<h4><i class="fa-solid fa-shield-halved"></i> Platform Changes</h4>
<ul class="impact-list">
  <li><span class="pill pill-os">Android 16</span> Dedicated local network permission introduced.</li>
  <li><span class="pill pill-enforcement">Play Store</span> Dozens of privacy-invasive apps and SDKs removed.</li>
  <li>20+ IoT vendors (Philips, Google, TP-Link, Apple) <strong>redesigned identifier schemes</strong>.</li>
</ul>
</div>

<div class="impact-col">
<h4><i class="fa-solid fa-newspaper"></i> Media &amp; Awareness</h4>
<ul class="impact-list">
  <li>Covered by El Pa&iacute;s, Wired, CBS News, ABC, and more.</li>
  <li>Presented at RIPE 89 Plenary (Prague) and RediMadrid Conference.</li>
</ul>
</div>

</div>

<details class="press-details">
<summary><i class="fa-solid fa-newspaper"></i> Press Coverage <span class="press-count">5+ outlets</span></summary>
<div class="press-grid">
<a class="press-item" href="https://elpais.com/tecnologia/2023-10-smart-devices-spy.html"><span class="press-outlet">El Pa&iacute;s</span><span class="press-title">How smart devices spy on us and reveal information about our homes</span></a>
<a class="press-item" href="https://www.wired.com/story/smart-home-devices-privacy/"><span class="press-outlet">Wired</span><span class="press-title">Los dispositivos de tu hogar inteligente te esp&iacute;an</span></a>
<a class="press-item" href="https://www.cbsnews.com/calgary/smart-devices-leaking-private-data/"><span class="press-outlet">CBS News</span><span class="press-title">Are your home's smart devices leaking private data?</span></a>
</div>
</details>

</div>

<!-- ============================================ -->
<!-- WIRELESS SDKs -->
<!-- ============================================ -->
<div class="topic-block" data-topics="wireless">

<div class="topic-header wireless-header">
  <div class="topic-header-content">
    <h2>Wireless-Scanning SDKs</h2>
    <p class="topic-subtitle">Empirical privacy analysis of wireless-scanning SDKs in Android &mdash; revealing how apps exploit Wi-Fi, Bluetooth, and other wireless signals for covert location tracking.</p>
    <div class="topic-paper">
      <span class="venue-badge">PoPETs 2025</span>
      <span class="paper-title">Your Signal, Their Data: An Empirical Privacy Analysis of Wireless-Scanning SDKs in Android</span>
      <a href="https://petsymposium.org/popets/2025/popets-2025-0103.pdf" class="paper-link"><i class="fa-solid fa-file-pdf"></i></a>
    </div>
  </div>
</div>

<div class="topic-impact-sections">

<div class="impact-col">
<h4><i class="fa-solid fa-shield-halved"></i> Impact</h4>
<ul class="impact-list">
  <li>Exposed how wireless scanning SDKs enable covert location inference through Wi-Fi, Bluetooth, and other signals.</li>
  <li>Contributed to broader understanding of cross-device and cross-platform tracking vectors in smart ecosystems.</li>
  <li>Covered by La Sexta Noticias and El Pa&iacute;s.</li>
</ul>
</div>

</div>

</div>

<!-- ============================================ -->
<!-- CHILD-DIRECTED APPS -->
<!-- ============================================ -->
<div class="topic-block" data-topics="childapps">

<div class="topic-header childapps-header">
  <div class="topic-header-content">
    <h2>Child-Directed Apps</h2>
    <p class="topic-subtitle">Empirical evidence that platform policy enforcement is insufficient for regulatory compliance &mdash; developers cannot control third-party SDK behavior, revealing structural limitations in how access control policies propagate through the software supply chain.</p>
    <div class="topic-paper">
      <span class="venue-badge">PoPETs 2025</span>
      <span class="paper-title">The Effect of Platform Policies on App Privacy Compliance</span>
      <a href="https://petsymposium.org/popets/2025/popets-2025-0094.pdf" class="paper-link"><i class="fa-solid fa-file-pdf"></i></a>
    </div>
  </div>
</div>

<div class="topic-impact-sections">

<div class="impact-col">
<h4><i class="fa-solid fa-shield-halved"></i> Impact</h4>
<ul class="impact-list">
  <li>Demonstrated that despite Google Play's stricter SDK restrictions and privacy label requirements, developers remain unable to control third-party SDK behavior.</li>
  <li>Revealed a <strong>structural limitation</strong> in how platform access control policies propagate through the software supply chain.</li>
  <li>Informed ongoing policy debates around children's online privacy regulation.</li>
</ul>
</div>

</div>

</div>

<div class="impact-footer-note">
  All research artifacts are publicly released following open science principles. Achieved within a PhD completed <em>Cum Laude</em> at IMDEA Networks / UC3M, now continuing as a postdoctoral researcher at IMDEA Networks Institute.
</div>

<script>
document.addEventListener('DOMContentLoaded', function() {
  // Animated counters
  const counters = document.querySelectorAll('.stat-number');
  const animateCounter = (counter) => {
    const target = +counter.getAttribute('data-target');
    const suffix = target >= 20 ? '+' : '';
    const increment = Math.max(1, Math.floor(target / 60));
    let current = 0;
    const updateCount = () => {
      current += increment;
      if (current >= target) { counter.innerText = target + suffix; return; }
      counter.innerText = current;
      requestAnimationFrame(updateCount);
    };
    updateCount();
  };
  const observer = new IntersectionObserver((entries) => {
    entries.forEach(entry => {
      if (entry.isIntersecting) { animateCounter(entry.target); observer.unobserve(entry.target); }
    });
  }, { threshold: 0.5 });
  counters.forEach(counter => observer.observe(counter));

  // Topic filtering
  const blocks = document.querySelectorAll('.topic-block');
  document.querySelectorAll('.topic-btn').forEach(btn => {
    btn.addEventListener('click', () => {
      document.querySelectorAll('.topic-btn').forEach(b => b.classList.remove('active'));
      btn.classList.add('active');
      const topic = btn.dataset.topic;
      blocks.forEach(block => {
        if (topic === 'all' || block.dataset.topics === topic) {
          block.style.display = '';
          block.classList.add('topic-enter');
          setTimeout(() => block.classList.remove('topic-enter'), 300);
        } else {
          block.style.display = 'none';
        }
      });
    });
  });
});
</script>
