# Template

## 1. how to run locally  

```
cd /my/work/directory/
bundle exec jekyll serve
```

## 2. how to create a subtab  

Create a directory in current working directory. Add a README.md with   

```
---
sort: 1
---

# Test Documentation

\```
{% raw %}{% include list.liquid all=true %}{% endraw %}
\```

{% include list.liquid all=true %}
```

Sort refer to order in tab list. First head title refer to name of this tab.  


## 3. how to create a document  

Create a Markdown file in subtab directory. Add content as below:

```

---
sort: 1
---

# Markdown Elements

content below
......
```

## 4. how to create a diretory tab

Create a diretory tab with more document

```
---
sort: 2
---

# This is an incredibly long caption for a long menu

\```
{% raw %}{% include list.liquid all=true %}{% endraw %}

{% include list.liquid all=true %}
\```

{% include list.liquid all=true %}
```

## Useful reference

> + [Markdown tutorial](https://markdown.com.cn/basic-syntax/)
> + [Rundocs introduction](https://rundocs.io/installing/gem-based.html)