---
layout: default
title: Overview
nav_order: 1
description: ""
permalink: /
---

# Version Control for your APIs
{: .fs-9 }


[put   a     gif   here]

Optic is a Git-like version control system for API contracts. Optic makes maintaining an accurate API specification as easy as staging changes and making commits.
{: .fs-6 .fw-300 }


[Get started now](/setup){: .btn .btn-primary .fs-5 .mb-4 .mb-md-0 .mr-2 } [View it on GitHub](https://github.com/pmarsceill/just-the-docs){: .btn .fs-5 .mb-4 .mb-md-0 }

---

## FAQs

### What kinds of APIs is this for?
Optic was designed around HTTP/RESTful APIs. It won't help you with websockets, event-driven APIs, GraphQL endpoints or RPC-style APIs. We might add more Optic-for-x-paradigm as the project grows.

### What Languages / API Frameworks does Optic work with?
Optic's CLI monitors the HTTP traffic going in/out of your API process and can work with any API Framework.

### What does Optic replace?
If you are documenting your API manually or adding annotations to your source code to generate an OpenAPI specification, Optic will simplify your process and improve the accuracy of your specification.


### How is Optic different from OpenAPI?
Optic and OpenAPI are compatible with one another and share many of the same goals. What makes Optic different is its focus on building developer-friendly workflows that make it easy to document your API and verify that it is meeting its contract.


---

## About the project

Optic is maintained by [Dev Doshi](https://github.com/devdoshi), [Aidan Cunniffe](https://github.com/acunniffe) and the team at [Optic (YC S18)](https://useoptic.com)

### License

Optic is distributed under the [MIT license](https://github.com/opticdev/optic/blob/master/LICENSE).

### Contributing

When contributing to this repository, please first discuss the change you wish to make via issue,
email, or any other method with the owners of this repository before making a change. Read more about becoming a contributor in [our GitHub repo](https://github.com/pmarsceill/just-the-docs#contributing).

#### Thank you to the contributors of Optic!
<ul class="list-style-none">
{% for contributor in site.github.contributors %}
  <li class="d-inline-block mr-1">
     <a href="{{ contributor.html_url }}"><img src="{{ contributor.avatar_url }}" width="32" height="32" alt="{{ contributor.login }}"/></a>
  </li>
{% endfor %}
</ul>
### Code of Conduct

Just the Docs is committed to fostering a welcoming community.

[View our Code of Conduct](https://github.com/pmarsceill/just-the-docs/tree/master/CODE_OF_CONDUCT.md) on our GitHub repository.
