<h1>
{% if include.title != nil %}
  {{ include.title }}
{% else %}
  {{ page.title }}
{% endif %}
</h1>

{% if page.has_toc != false %}
<details open markdown="block">
  <summary>
    Table of contents
  </summary>
  {: .text-delta }
- TOC
{:toc}

---
</details>
{% endif %}
