---
title: Code samples
permalink: /docs/code_samples/
---

[Provide a few complete code samples or snippets that users can copy and paste for common use cases. The idea is that your code samples will help users understand how to write their own code for your API.

You can start with cURL command line code samples, but you should add samples in other languages to address common needs, such as JavaScript for web browser code and Java and Swift for mobile developers.


<!--
{% assign path = "/token" %}
{{ site.data.CovaAPIDocumentation.paths[path].post.summary }}

{{ site.data.CovaAPIDocumentation.paths[path].post.parameters[0].name }}

{{ site.data.CovaAPIDocumentation.paths[0] }}

{{ site.data.CovaAPIDocumentation.paths[path].post.parameters[0].name }}
-->


{% assign api_categories = "" %}
{% assign api_categories = "" | split: ',' %}


{% for item in site.data.CovaAPIDocumentation.paths %}

{% assign path = item[0] %}

{% if site.data.CovaAPIDocumentation.paths[path].post.tags  %}
  {% assign category = site.data.CovaAPIDocumentation.paths[path].post.tags %}
{% elsif site.data.CovaAPIDocumentation.paths[path].get.tags %}
 {% assign category = site.data.CovaAPIDocumentation.paths[path].get.tags %}
 {% elsif site.data.CovaAPIDocumentation.paths[path].delete.tags %}
 {% assign category = site.data.CovaAPIDocumentation.paths[path].delete.tags %}
 {% elsif site.data.CovaAPIDocumentation.paths[path].put.tags %}
 {% assign category = site.data.CovaAPIDocumentation.paths[path].put.tags %}
{% else %}
 {% assign category = "Misc %}
{% endif %}

{% assign  api_categories =  api_categories | push: category | sort %} 

{% endfor %}


{% assign  api_categories =  api_categories | sort %} 


{% assign api_category = "" %}
{% assign api_category = "" | split: ',' %}
{% assign current_category = "" %}


{% for item in api_categories %}

{% if item != current_category %}
{% assign  api_category =  api_category | push: item | sort %} 
{% assign current_category = item %}
{% endif %}
{% endfor %}




<h1> Grouping </h1>


{% for group in api_category %}
<h3>{{  group }}</h3>

{% for item in site.data.CovaAPIDocumentation.paths %}

{% assign path = item[0] %}

{% if site.data.CovaAPIDocumentation.paths[path].post.tags  %}
  {% assign category = site.data.CovaAPIDocumentation.paths[path].post.tags %}
{% elsif site.data.CovaAPIDocumentation.paths[path].get.tags %}
 {% assign category = site.data.CovaAPIDocumentation.paths[path].get.tags %}
 {% elsif site.data.CovaAPIDocumentation.paths[path].delete.tags %}
 {% assign category = site.data.CovaAPIDocumentation.paths[path].delete.tags %}
 {% elsif site.data.CovaAPIDocumentation.paths[path].put.tags %}
 {% assign category = site.data.CovaAPIDocumentation.paths[path].put.tags %}
{% else %}
 {% assign category = "Misc %}
{% endif %}

{% if category == group %}
<ul>
<li>{{ path }}</li>
</ul>
{% endif %}

{% endfor %}
{% endfor %}


<!--

{% for item in api_category %}
{{ api_category[forloop.index0] }}
{{ item }}
{% for entry in item.subitems %}
{{ entry }}
{% endfor %}
{% endfor %}

-->
<!--
<table>
    <thead>
    <tr><th>Name</th><th>Type</th><th>Description</th><th>Required?</th></tr>
    </thead>
    {% for parameter in site.data.CovaAPIDocumentation.paths.post.parameters %}
        {% if parameter.in == "query" %}
        <tr>
            <td><code>{{ parameter.name }}</code></td>
            <td><code>{{ parameter.type }}</code></td>
            <td>
            {% assign found = false %}
            {% for param in site.data.swagger.paths.get.parameters %}
                {% if parameter.name == param.name %}
                    {{ param.description }}
                    {% assign found = true %}
                {% endif %}
            {% endfor %}
            {% if found == false %}
                ** New parameter **
            {% endif %}
            </td>
            <td><code>{{ parameter.required }}</code></td>
        </tr>
        {% endif %}
    {% endfor %}
</table>
-->

<!--

<script src="https://cdn.rawgit.com/JS-DevTools/swagger-parser/dist/swagger-parser.js"></script>
<script>
var myAPI = site.dist.CovaAPIDocumentation
  SwaggerParser.validate(myAPI, function(err, api) {
    if (err) {
      console.error(err);
    }
    else {
      console.log("API name: %s, Version: %s", api.info.title, api.info.version);
    }
  });
</script> 
-->

## Code syntax

To specify language for your code blocks, follow the [Markdown code and syntax highlighting](https://github.com/adam-p/markdown-here/wiki/Markdown-Cheatsheet#code-and-syntax-highlighting) section in Adam Pritchard's Markdown cheatsheet.]
