---
layout: cv
title: Istvan Hoka - CV - Resume
description: Experienced Software Engineer & Startup CTO with 20+ years in technical leadership, system architecture, and building scalable platforms
image: /favicon.svg
---

# [Istvan Hoka](/)

London, UK

## Professional Summary

**Software Engineer & Startup CTO** with 20+ years building scalable systems and leading technical transformation. Architected platforms serving 50M+ monthly users, designed frameworks managing 500+ software components, and established engineering practices that improved developer productivity across multiple organizations. Expert in "building the machine that builds the machine" - creating systems, processes, and teams that deliver exceptional products while avoiding over-engineering.

### Core Expertise

- AI Engineering
- Software Architecture
- Technical Leadership
- Developer Productivity
- Full-Stack Development

### Technical Leadership Philosophy

Passionate about elegant solutions that solve real problems without over-engineering. Focus on:

- **Developer Productivity**: Building tools and frameworks that multiply team effectiveness
- **Sustainable Architecture**: Designing systems for maintainability and long-term growth
- **Engineering Excellence**: Establishing practices that balance speed with quality
- **Problem-First Thinking**: Technology choices driven by business needs, not technology trends

### Key Achievements

- **System Architecture at Scale**: Designed dependency management systems and CI/CD pipelines serving 500+ Ruby/Rails & React components, reducing build times by 90% and enabling hundreds of deployments per day (as opposed to one every several weeks).
- **GenAI Innovation**: Spearheaded adoption of GenAI/Copilot tools across engineering teams, building BlockSmith framework for automated maintenance that reduced manual work by 90%
- **High-Traffic Platform Development**: Built web APIs and real-time systems serving up to 50M monthly visitors with 200ms response times and 99.999% uptime
- **Team Building & Leadership**: Hired and trained development teams of 20 engineers, establishing coding standards and architectural frameworks adopted company-wide
- **Business-Critical Problem Solving**: Identified and fixed compound precision errors in tax systems, reducing company tax liability by £500k annually.

## Work experience

### **Founder, CEO**, Aissac (d/b/a ZenCash) `Present`

Leading cryptocurrency trading operations, following guidance from certified investment advisors while managing client portfolios. Utilizing established cryptocurrency trading platforms to execute strategic trades and deliver value for clients.

### **Co-Founder / CTO**, Kensan.ai `Present`

Leading technical development and strategy for AI-powered solutions.

### **Co-Founder / CTO**, FlySwiftTail.com `Present`

Building innovative aviation technology solutions.

### **Builder.ai**, Principal (Staff) Engineer `May 2023 - May 2025`

Led technical transformation across 4 engineering teams focused on Application Assembly and Building Blocks platform serving hundreds of SME customers.

#### Strategic Architecture & Standards

- Designed new platform architecture supporting stack-agnostic backends (`Python/Django/FastAPI`, `Node.js/Next.js`) with `React & React Native` frontends, moving away from single stack support, while reducing the complexity of stack upgrades by proper employment of separation of concerns.
- Defined versioning and maintenance policies for 500+ software components, enabling adoption of `SemVer`, and ensuring compatibility between components.
- Established error handling and testing standards, improving components reliability and security.
- Participated in Architecture Review Board, defining an Architectural Framework (inspired by `TOGAF`) for the BX Org Unit: Architecture Repository, templates for Baseline Architecture, Solution Designs, defined Governance process.

#### Developer Productivity & Innovation

- **Blocksmith**: Built GenAI framework for batch maintenance of Blocks, reducing manual work by 90%: automatic documentation generation, application of error handling and unit testing standards, stack upgrades. Learned `Python` from scratch in the process, using GenAI dev tools (`RAG`, `MCP`, `Github Copilot`, `Cline / Memory Bank`).
- **Blocks Workspace IDE**: Designed and implemented, enabling turn-key local full-stack development, cutting developer onboarding time from days to minutes. `Python`, `Node.js`, `[mise](http://mise.jdx.dev/)`, `uv`.
- **BVM (Blocks Version Manager)** Implemented filling gaps in platform package managers, improving dependency resolution of Blocks. This allowed the rollout of SemVer for Blocks, taking into account their compatibility with the stack version as well (Ruby, Node.js, React, React Native).

#### Infrastructure & Tooling

- Architected highly modular CI/CD pipelines for 500+ components using [`gitlab-ci-local`](https://github.com/firecow/gitlab-ci-local) to enable rapid feedback loop and unit tests for pipelines themselves. `Python`, `Node.js`, `Ruby`.
- Built `Neo4j`-based dependency graph improving stack upgrade process efficiency and allowing Natasha AI to understand the dependencies between components using `MCP`.
- Drove adoption of GenAI development tools across teams, modernising and improving developers' workflows. `Github Copilot`, `Roo Code`, `Cursor`.

### **Solutions Architect**, notonthehighstreet.com, London `Apr 2022 - Apr 2023`

Transitioned from the role of Principal Engineer after the departure of the Head of Architecture, as it became apparent that the organisation was in need of a more structured architecture function.

- Established a more structured architecture framework for the tech team.
- Continued developing and evolving solution designs for the organisation.
  - Product Catalogue: replatform from legacy system to become the aggregation point of product data - target architecture, solution design, implementation governance.
  - Product Information Management: introduce new capabilities to enable better understanding of product taxonomy when indexing, and allow granular stock management - solution design, implemetation governance.
  - Guest checkout: allow unregistered uses to place orders - solution design and implementation governance.

### **Principal Engineer**, notonthehighstreet.com, London `Feb 2020 - Apr 2022`

- New payment method ApplePay: target architecture, solution design and implementation governance.
- New stock management capability: target architecture, solution design and implementation governance.
- Rethink approach to asynchronous messaging, from a home-grown solution, to leveraging more of the AWS infrastructure, and reduce coupling.

### **Senior Software Engineer**, notonthehighstreet.com, London `Jun 2018 - Jan 2020`

Hired initially as a senior Ruby engineer to work on payment systems, became de-facto tech lead of the Payment team.

- Lead re-platforming projects for Basket and Checkout - extract systems from monolithic architecture into domain aligned components. Lead design and implementation for APIs, microservices based on Node.js, GraphQL.
- Troubleshooted and fixed a compound precision and rounding problem in the tax system, which reduced the companies tax liability significantly.
- Completed previously started implementation of gift card capability, using GiveX as an external provider.

Skills: Ruby on Rails, Node.js, GraphQL, DynamoDB, CloudFormation, Docker, Ansible.

### **CTO**, Digital Takeover, Dallas, TX `Mar 2015 - Mar 2018`

Media/content startup, leveraging Facebook heaviliy to drive traffic, Digital Takeover owned 2 web properties driving 50 million monthly visitors at its height.

- Online publishing workflow tool with real-time collaboration: architecture, design, implementation. Ruby on Rails, Ember.js, MySQL, Wordpress.
- Real-time KPI dashboard, aggregating multiple sources of data: traffic, revenue, social engagement. Architecture, design, implementation. Ruby on Rails, Ember.js, MySQL, Facebook Graph API, Google Analytics, advertiser APIs.
- Web API serving up to 50MM visitors/month to enhance online magazine with social features: voting, popularity. Architecture, implementation. Ruby on Rails.
- Custom online magazine theme for Wordpress. Implementation.

### **CTO**, ZenCash.com, Dallas, TX `Aug 2011 - Mar 2015`

ZenCash was an "Accounts Receivable CRM", a tool meant to help B2B collect payment from their clients faster, by means of a follow-up plan over email, phone and the post. ZenCash was started as a spin-off by the same owners as Blinksale. Through my consulting company, Aissac, I acted as the leader in technical strategy and development.

- Hired and trained development team.
- High-throughput event based system, custom API bindings for 7 invoicing applications, for highly efficient data synchronisation.
- 3rd party integrations for print, post and phone solution providers.
- Web application frontend for customers and back-office management.
- Provided technical leadership, architecture and implementation (in part) for all systems and capabilities.

Skills: technical leadership, architecture, EventMachine (Ruby), RabbitMQ, Ruby on Rails, Ember.js, Jenkins, Chef (EngineYard), AWS (various services).

### **CTO**, Blinksale.com, Dallas, TX `Jan 2011 - Dec 2018`

Blinksale is an invoicing application, one of the first webapps built with Ruby on Rails.
Through my consulting company, Aissac, I acted as the leader in technical strategy and development.

- Hired and trained additional developers.
- Migrated application from VPS hosting to PaaS (AWS + EngineYard).
- Implemented CI/CD, backfilled integration and unit testing.
- New features added: BlinkPay (Stripe-like merchant solution, complete with underwriting process, zero-configuration for payments), Estimates.
- Provided technical leadership, architecture for all new capabilities.
- Re-built the invoincing platform with an API-first design, and modern Ember.js web frontend.
- Assisted with selling Blinksale to a new owner.

Skills: technical leadership, architecture, Ruby on Rails, Ember.js, Jenkins, Chef (EngineYard), AWS (various services).

### **Lead Developer**, Blinksale.com, Dallas, TX `Jan 2010 - Dec 2010`

First contact with the new owner of Blinksale, hired as lead developer.

- Ruby on Rails development

### **Founder**, Aissac, Cluj-Napoca, Romania `Sep 2005`

Co-founded Aissac SRL, a small development shop focused on web development, using Ruby on Rails as the primary development framework. Overtime I became the sole owner of the business.

## Education

### **BSE Automation and Computer Science**, Technical University of Cluj-Napoca, Romania `2000 - 2005`
