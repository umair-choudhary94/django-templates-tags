

# 📄 Django Template Tags – README Guide

Django's template system uses **template tags** to add logic inside HTML files. These tags control rendering, layout, and data display from the backend.

---

## 🔁 `{% for %}` — Looping Through Data

Used to iterate over a list or queryset in a template.

```django
<ul>
  {% for todo in todos %}
    <li>{{ todo.title }} - {% if todo.is_completed %}Done{% else %}Pending{% endif %}</li>
  {% endfor %}
</ul>
```

---

## 🔀 `{% if %}` — Conditional Logic

Used to render content based on logic.

```django
{% if user.is_authenticated %}
  <p>Welcome, {{ user.username }}!</p>
{% else %}
  <p>Please <a href="/login/">login</a>.</p>
{% endif %}
```

You can use `elif` and `else` too:

```django
{% if count > 5 %}
  Many items
{% elif count == 5 %}
  Exactly five
{% else %}
  Few items
{% endif %}
```

---

## 🧩 `{% include %}` — Include Other Templates

Used to include smaller templates (like navbar, footer) into larger ones.

```django
{% include 'partials/navbar.html' %}
```

This keeps your layout **modular and reusable**.

---

## 🧱 `{% extends %}` and `{% block %}` — Template Inheritance

Used to **inherit layout** from a base template.

### `base.html`
```django
<!DOCTYPE html>
<html>
<head>
  <title>{% block title %}My Site{% endblock %}</title>
</head>
<body>
  {% include 'partials/navbar.html' %}
  <div class="content">
    {% block content %}{% endblock %}
  </div>
</body>
</html>
```

### `home.html`
```django
{% extends 'base.html' %}

{% block title %}Home{% endblock %}

{% block content %}
  <h1>Welcome to the homepage</h1>
{% endblock %}
```

This is great for **DRY (Don't Repeat Yourself)** layout building.

---

## 🔤 Output Variables with `{{ }}`

Used to print data:

```django
<p>{{ user.username }}</p>
<p>{{ todo.description|truncatewords:10 }}</p>
```

You can also use **filters** like `upper`, `date`, `length`, etc.

---

## 🚫 `{% comment %}` — Template Comments

For hiding code from rendering:

```django
{% comment %}
  This won't be rendered
{% endcomment %}
```

---

## 🧠 Summary of Common Tags

| Tag | Purpose |
|-----|---------|
| `{% for item in list %}` | Loops over data |
| `{% if condition %}` | Conditional logic |
| `{% include 'file.html' %}` | Reuse sub-templates |
| `{% extends 'base.html' %}` | Inherit layout |
| `{% block content %}` | Define overridable sections |
| `{{ variable }}` | Output values |
| `{% comment %}` | Hidden template comments |

