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
    <div class="stat-number" data-target="20">0</div>
    <div class="stat-label">IoT vendors patched</div>
  </div>
  <div class="stat-card">
    <div class="stat-number" data-target="6">0</div>
    <div class="stat-label">Browser/OS mitigations</div>
  </div>
  <div class="stat-card">
    <div class="stat-number" data-target="3">0</div>
    <div class="stat-label">Countries with lawsuits</div>
  </div>
  <div class="stat-card">
    <div class="stat-number" data-target="100">0</div>
    <div class="stat-label">Media outlets</div>
  </div>
</div>

<!-- Topic selector (auto-generated from data) -->
<div class="topic-nav">
  <button class="topic-btn active" data-topic="all">All Impact</button>
  {% for topic in site.data.impact %}
  <button class="topic-btn" data-topic="{{ topic.id }}">
    <span class="topic-dot dot-{{ topic.color }}"></span> {{ topic.title }}
  </button>
  {% endfor %}
</div>

{% for topic in site.data.impact %}
  {% include impact-topic.html topic=topic %}
{% endfor %}

<script>
document.addEventListener('DOMContentLoaded', function() {
  // Animated counters
  const counters = document.querySelectorAll('.stat-number');
  const animateCounter = (counter) => {
    const target = +counter.getAttribute('data-target');
    const suffix = '+';
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
