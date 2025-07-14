---
layout: cv
title: Istvan Hoka - CV - Staff Engineer, Startup CTO - Jul 2025
---

# `Istvan Hoka`
{: .text-6xl .font-mono .text-gray-800 .mb-8 .text-center .flex .items-center .justify-center .min-h-[200px]}

<div class="text-center text-gray-600 mb-8 space-x-4">
    <a href="mailto:istvan.hoka@gmail.com" class="text-blue-600 hover:text-blue-800">istvan.hoka@gmail.com</a>
    <span class="text-gray-400">|</span>
    <a href="https://linkedin.com/in/ihoka" class="text-blue-600 hover:text-blue-800">linkedin.com/in/ihoka</a>
    <span class="text-gray-400">|</span>
    <a href="tel:+447424665097" class="text-blue-600 hover:text-blue-800">+44 (0)7424 665097</a>
    <span class="text-gray-400">|</span>
    <span>London, UK</span>
</div>

## Professional Summary
{: .text-2xl .font-semibold .text-gray-700 .mb-4 .border-b-2 .border-blue-500 .pb-2}

<div class="mb-6">
<p class="text-lg leading-relaxed mb-4"><strong>Staff Engineer & Startup CTO</strong> with 20+ years building scalable systems and leading technical transformation. Architected platforms serving 50M+ monthly users, designed frameworks managing 500+ software components, and established engineering practices that improved developer productivity across multiple organizations. Expert in "building the machine that builds the machine" - creating systems, processes, and teams that deliver exceptional products while avoiding over-engineering.</p>

<div class="bg-blue-50 p-4 rounded-lg">
<p class="font-semibold text-gray-700 mb-2">Core Expertise:</p>
<ul class="grid grid-cols-2 gap-2 text-gray-600">
<li class="flex items-center"><span class="w-2 h-2 bg-blue-500 rounded-full mr-2"></span>Software Architecture</li>
<li class="flex items-center"><span class="w-2 h-2 bg-blue-500 rounded-full mr-2"></span>Technical Leadership</li>
<li class="flex items-center"><span class="w-2 h-2 bg-blue-500 rounded-full mr-2"></span>Developer Productivity</li>
<li class="flex items-center"><span class="w-2 h-2 bg-blue-500 rounded-full mr-2"></span>GenAI Engineering</li>
<li class="flex items-center"><span class="w-2 h-2 bg-blue-500 rounded-full mr-2"></span>Full-Stack Development</li>
</ul>
</div>
</div>

## Technical Leadership Philosophy
{: .text-2xl .font-semibold .text-gray-700 .mb-4 .border-b-2 .border-blue-500 .pb-2}

Passionate about elegant solutions that solve real problems without over-engineering. Focus on:

* **Developer Productivity**: Building tools and frameworks that multiply team effectiveness
* **Sustainable Architecture**: Designing systems for maintainability and long-term growth
* **Engineering Excellence**: Establishing practices that balance speed with quality
* **Problem-First Thinking**: Technology choices driven by business needs, not technology trends

## Key Achievements
{: .text-2xl .font-semibold .text-gray-700 .mb-4 .border-b-2 .border-blue-500 .pb-2}

* **System Architecture at Scale**: Designed dependency management systems and CI/CD pipelines serving 500+ Ruby/Rails & React components, reducing build times by 90% and enabling hundreds of deployments per day (as opposed to one every several weeks).
* **GenAI Innovation**: Spearheaded adoption of GenAI/Copilot tools across engineering teams, building BlockSmith framework for automated maintenance that reduced manual work by 90%
* **High-Traffic Platform Development**: Built web APIs and real-time systems serving up to 50M monthly visitors with 200ms response times and 99.999% uptime
* **Team Building & Leadership**: Hired and trained development teams of 20 engineers, establishing coding standards and architectural frameworks adopted company-wide
* **Business-Critical Problem Solving**: Identified and fixed compound precision errors in tax systems, reducing company tax liability by £500k annually.

## Work experience
{: .text-2xl .font-semibold .text-gray-700 .mb-4 .border-b-2 .border-blue-500 .pb-2}

`May 2023 - May 2025`
**Builder.ai**, Principal Engineer (IC5)

Led technical transformation across 4 engineering teams focused on Application Assembly and Building Blocks platform serving hundreds of SME customers.

Strategic Architecture & Standards:

* Designed new platform architecture supporting stack-agnostic backends (`Python/Django/FastAPI`, `Node.js/Next.js`) with `React & React Native` frontends, moving away from single stack support, while reducing the complexity of stack upgrades by proper employment of separation of concerns.
* Defined versioning and maintenance policies for 500+ software components, enabling adoption of `SemVer`, and ensuring compatibility between components.
* Established error handling and testing standards, improving components reliability and security.
* Participated in Architecture Review Board, defining an Architectural Framework (inspired by `TOGAF`) for the BX Org Unit: Architecture Repository, templates for Baseline Architecture, Solution Designs, defined Governance process.

Developer Productivity & Innovation:

* Built Blocksmith GenAI framework for batch maintenance of Blocks, reducing manual work by 90%: automatic documentation generation, application of error handling and unit testing standards, stack upgrades. Learned `Python` from scratch in the process, using GenAI dev tools (`Github Copilot`, `Cline / Memory Bank`).
* Designed and implemented Blocks Workspace, enabling turn-key local full-stack development, cutting developer onboarding time from days to minutes. `Python`, `Node.js`, `[mise](http://mise.jdx.dev/)`, `uv`.
* Implemented BVM (Blocks Version Manager) filling gaps in platform package managers, improving dependency resolution of Blocks. This allowed the rollout of SemVer for Blocks, taking into account their compatibility with the stack version as well (Ruby, Node.js, React, React Native).

Infrastructure & Tooling:

* Architected highly modular CI/CD pipelines for 500+ components using [`gitlab-ci-local`](https://github.com/firecow/gitlab-ci-local) to enable rapid feedback loop and unit tests for pipelines themselves. `Python`, `Node.js`, `Ruby`.
* Built Neo4j-based dependency graph improving stack upgrade process efficiency and allowing Natasha AI to understand the dependencies between components using `MCP`.
* Drove adoption of GenAI development tools across teams, modernising and improving developers' workflows. `Github Copilot`, `Roo Code`, `Cursor`.

`Apr 2022 - Apr 2023`
**Software Solutions Architect** (permanent), notonthehighstreet.com, London

Transitioned from the role of Principal Engineer after the departure of the Head of Architecture, as it became apparent that the organisation was in need of a more structured architecture function.

* Established a more structured architecture framework for the tech team.
* Continued developing and evolving solution designs for the organisation.
  * Product Catalogue: replatform from legacy system to become the aggregation point of product data - target architecture, solution design, implementation governance.
  * Product Information Management: introduce new capabilities to enable better understanding of product taxonomy when indexing, and allow granular stock management - solution design, implemetation governance.
  * Guest checkout: allow unregistered uses to place orders - solution design and implementation governance.

`Feb 2020 - Apr 2022`
**Principal Engineer** (permanent), notonthehighstreet.com, London

* New payment method ApplePay: target architecture, solution design and implementation governance.
* New stock management capability: target architecture, solution design and implementation governance.
* Rethink approach to asynchronous messaging, from a home-grown solution, to leveraging more of the AWS infrastructure, and reduce coupling.

`Jun 2018 - Jan 2020`
**Senior Software Engineer** (contract), notonthehighstreet.com, London

Hired initially as a senior Ruby engineer to work on payment systems, became de-facto tech lead of the Payment team.

* Lead re-platforming projects for Basket and Checkout - extract systems from monolithic architecture into domain aligned components. Lead design and implementation for APIs, microservices based on Node.js, GraphQL.
* Troubleshooted and fixed a compound precision and rounding problem in the tax system, which reduced the companies tax liability significantly.
* Completed previously started implementation of gift card capability, using GiveX as an external provider.

Skills: Ruby on Rails, Node.js, GraphQL, DynamoDB, CloudFormation, Docker, Ansible.

`Mar 2015 - Mar 2018`
**CTO** (contract, Aissac), Digital Takeover, Dallas, TX (remote)

Media/content startup, leveraging Facebook heaviliy to drive traffic, Digital Takeover owned 2 web properties driving 50 million monthly visitors at its height.

* Online publishing workflow tool with real-time collaboration: architecture, design, implementation. Ruby on Rails, Ember.js, MySQL, Wordpress.
* Real-time KPI dashboard, aggregating multiple sources of data: traffic, revenue, social engagement. Architecture, design, implementation. Ruby on Rails, Ember.js, MySQL, Facebook Graph API, Google Analytics, advertiser APIs.
* Web API serving up to 50MM visitors/month to enhance online magazine with social features: voting, popularity. Architecture, implementation. Ruby on Rails.
* Custom online magazine theme for Wordpress. Implementation.

`Aug 2011 - Mar 2015`
**CTO** (contract, Aissac), ZenCash.com, Dallas, TX (remote)

ZenCash was an "Accounts Receivable CRM", a tool meant to help B2B collect payment from their clients faster, by means of a follow-up plan over email, phone and the post. ZenCash was started as a spin-off by the same owners as Blinksale. Through my consulting company, Aissac, I acted as the leader in technical strategy and development.

* Hired and trained development team.
* High-throughput event based system, custom API bindings for 7 invoicing applications, for highly efficient data synchronisation.
* 3rd party integrations for print, post and phone solution providers.
* Web application frontend for customers and back-office management.
* Provided technical leadership, architecture and implementation (in part) for all systems and capabilities.

Skills: technical leadership, architecture, EventMachine (Ruby), RabbitMQ, Ruby on Rails, Ember.js, Jenkins, Chef (EngineYard), AWS (various services).

`Jan 2011 - Dec 2018`
**CTO** (contract, Aissac), Blinksale.com, Dallas, TX (remote)

Blinksale is an invoicing application, one of the first webapps built with Ruby on Rails.
Through my consulting company, Aissac, I acted as the leader in technical strategy and development.

* Hired and trained additional developers.
* Migrated application from VPS hosting to PaaS (AWS + EngineYard).
* Implemented CI/CD, backfilled integration and unit testing.
* New features added: BlinkPay (Stripe-like merchant solution, complete with underwriting process, zero-configuration for payments), Estimates.
* Provided technical leadership, architecture for all new capabilities.
* Re-built the invoincing platform with an API-first design, and modern Ember.js web frontend.
* Assisted with selling Blinksale to a new owner.

Skills: technical leadership, architecture, Ruby on Rails, Ember.js, Jenkins, Chef (EngineYard), AWS (various services).

`Jan 2010 - Dec 2010`
**Lead Developer** (contract, Aissac), Blinksale.com, Dallas, TX (remote)

First contact with the new owner of Blinksale, hired as lead developer.

* Ruby on Rails development

`Sep 2005`
**Founder**, Aissac

Co-founded Aissac SRL in Cluj-Napoca, Romania, a small development shop focused on web development, using Ruby on Rails as the primary development framework. Overtime I became the sole owner of the business.

## Education
{: .text-2xl .font-semibold .text-gray-700 .mb-4 .border-b-2 .border-blue-500 .pb-2}

`2000 - 2005`
**BSE Automation and Computer Science**, Technical University of Cluj-Napoca, Romania

<!-- ### Footer

Last updated: June 2025 -->
