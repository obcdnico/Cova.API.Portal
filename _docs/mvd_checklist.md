---
title: MVD checklist
permalink: /docs/mvd_checklist/
---

Use this checklist to help you complete your minimum viable API documentation.

Section | Questions to answer | Information to include
------- | ------------------- | ----------------------
Overview | What type of API do you have? | Type of API (RESTful, SOAP, platform-based)
| What can users do with your API? | Brief use cases and examples (2 or 3 sentences)
| Are there any access details or restrictions users need to know about? | Base URL, Rate limits
Authentication | If your API requires an authentication token or key, how do users get one? | Authentication method
| Do tokens/keys expire? | Expiration intervals (if any)
| What should users do if their token/key expires? | Refreshing expired tokens/keys
| How do users pass authentication to your API? | Example authorization header
Workflows | What is the optimal/assumed workflow for the 2 or 3 most useful things users can do with your API? | Link to the reference for each endpoint mentioned in the workflow
Code samples | What does the code look like for common use cases? | Complete code samples and code snippets that users can copy and paste
Reference | What do users need to know to use each endpoint? | For each endpoint:
| | HTTP method (GET, PUT, POST, DELETE)
| | Complete request URL
| | Parameters (path and query): name, type, description, and whether the parameter is requred
| | Example request (including header and body)
| | List of each element in the example request, including the type, description, and whether the element is required
| | Example response
| | List of each element in the example response, including type and description
| | List of error and status codes, including the code, message, and meaning

[Use this page if you prefer to use [Swagger UI](https://github.com/swagger-api/swagger-ui) to render your reference documentation instead of creating Markdown files.

Here's what you'll need to do:
* Replace the file `/dist/swagger_petstore.yml` with your own YAML file in your local copy of the template repo to display your spec in the iframe below
* Delete the Markdown reference example file `/_docs/mdreference.md`
* Delete the code `<li {% if page.sectionid=='docs' %} class="active" {% endif %}><a href="{{ "/docs/mdreference/" | prepend: site.baseurl }}">Reference</a></li>` from the file `/_includes/topnav.html`
* Delete the `- mdreference` menu item from the file `/_data/docs.yml`

To change formatting for the iframe, edit the `.intrinsic-container` and `.intrinsic-container iframe` classes in the file `/_sass/bootstrap/_grid.scss`.

The example spec used here is based on the [petstore-expanded.json](https://github.com/OAI/OpenAPI-Specification/blob/master/examples/v2.0/json/petstore-expanded.json) example from the [OpenAPI Specification Repository](https://github.com/OAI/OpenAPI-Specification).]
