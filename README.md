# Awesome Enterprise API Gateway [![Awesome](https://awesome.re/badge.svg)](https://awesome.re)

> A curated list of production-grade Enterprise API Gateways, API Management (APIM) platforms, and cloud-native traffic routing engines across SaaS solutions and open-source projects.

**Top Enterprise API Gateway (Open Source & Managed SaaS) 🌟 Star if you like it! 🌟**

*Focused on API Management, Traffic Routing, Rate Limiting, Security, Observability, Plugin Extensibility & Self-Hosted Infrastructure.*

**Last updated: November 2026**

---

This repository tracks notable **SaaS platforms** and **open-source projects** for **Enterprise API Gateways**. These tools enable engineering teams to route, secure, govern, and observe API traffic—handling authentication (OAuth2, OIDC, mTLS), rate limiting, traffic shaping, distributed tracing, protocol mediation (REST, GraphQL, gRPC, WebSocket), and modern AI Gateway LLM proxying.

Whether you need a fully managed cloud control plane or a high-throughput, self-hosted data plane, this list helps platform engineers, cloud architects, and enterprise leaders make data-driven infrastructure decisions.

---

## Table of Contents

- [Sector Overview & Market Dynamics](#sector-overview--market-dynamics)
- [Enterprise SaaS & Hosted Platforms](#enterprise-saas--hosted-platforms)
- [Open-Source GitHub Projects](#open-source-github-projects)
- [Architecture & Evaluation Trade-offs](#architecture--evaluation-trade-offs)
- [How to Contribute](#how-to-contribute)
- [Disclaimer](#disclaimer)

---

## Sector Overview & Market Dynamics

The global API Management market is estimated at **$7.0B to $8.8B in 2024–2025** and is projected to reach **$11B to $13.5B+ by 2026–2027**, compounding at an annual growth rate (CAGR) of over **20% to 25%**. 

The sector is **moderately fragmented**: hyper-scale cloud providers (AWS, Microsoft Azure, Google Cloud) command substantial market share via bundled cloud infrastructure, yet independent, specialized vendors (Kong, MuleSoft/Salesforce, Tyk, Gravitee) continuously capture enterprise workloads requiring multi-cloud federation, Kubernetes-native ingress controllers, and dedicated AI gateway governance. Rather than a "winner-take-all" monopoly, enterprises increasingly deploy hybrid topologies combining hyper-scaler edge entry points with open-source and vendor-agnostic gateways on-premises and across multiple clouds.

---

## Enterprise SaaS & Hosted Platforms

The table below lists leading commercial enterprise API gateways and management suites, sorted in descending order by parent company size (market valuation / enterprise market capitalization):

| Platform / Product | Parent Company | Size / Valuation (Market Cap) | Starting Tier Pricing | Free Tier / Trial Limits | Key Strengths & Trade-offs |
| :--- | :--- | :--- | :--- | :--- | :--- |
| **[Azure API Management](https://azure.microsoft.com/en-us/products/api-management/)** | Microsoft (NASDAQ: MSFT) | ~$3.1 Trillion | Consumption tier: **$3.50 per million calls** (after free allowance); Developer tier: **~$48/month** (dedicated sandbox) | **1 Million calls/month free forever** on Consumption tier; 3,000 API operations limit; no SLA on free allowance | Native Azure & Entra ID integration; serverless auto-scaling. Trade-off: advanced VNet injection and full portal require higher-cost dedicated tiers. |
| **[Google Cloud Apigee](https://cloud.google.com/apigee)** | Alphabet / Google (NASDAQ: GOOGL) | ~$2.1 Trillion | Pay-As-You-Go: **$20 per million standard calls** (~$100/M for extensible proxies) + hourly environment infrastructure charge | **60-Day Free Evaluation Trial** with full enterprise features in a Google Cloud sandbox environment (auto-expires after 60 days) | Best-in-class full lifecycle API governance, advanced analytics, and monetization. Trade-off: premium enterprise cost and deep GCP tie-in. |
| **[AWS API Gateway](https://aws.amazon.com/api-gateway/)** | Amazon (NASDAQ: AMZN) | ~$2.0 Trillion | HTTP APIs: **$1.00 per million calls**; REST APIs: **$3.50 per million calls**; WebSockets: **$1.00 per million messages** | **1 Million API calls/month free for 12 months** (REST & HTTP APIs) plus 1M WebSocket messages & 750,000 connection minutes | Ultimate serverless synergy with AWS Lambda, IAM, and CloudWatch. Trade-off: limited multi-cloud portability and simpler policy mediation compared to standalone APIM. |
| **[MuleSoft Anypoint Platform](https://www.mulesoft.com/)** | Salesforce (NYSE: CRM) | ~$280 Billion | MuleSoft Integration Starter: starts at **~$1,000 to $2,000/month** (annual contract commitments typically start from $25,000+/year) | **30-Day Free Trial** with full Anypoint Platform design, runtime, and governance capabilities (no credit card required) | Industry standard for enterprise API-led connectivity and complex legacy system integration. Trade-off: high contract commitment and steep learning curve. |
| **[webMethods.io API](https://www.ibm.com/products/webmethods)** | IBM (NYSE: IBM) / Software AG | ~$200 Billion | Custom enterprise quote; hybrid integration bundles starting around **$1,500+/month** based on transaction pools | **30-Day Free Trial** on webMethods.io cloud environment with full access to API gateway, runtime policies, and portal | Enterprise-grade B2B integration and governance for complex legacy landscapes. Trade-off: quote-only pricing; less tailored for cloud-native microservices. |
| **[Cloudflare API Gateway](https://www.cloudflare.com/application-services/products/api-gateway/)** | Cloudflare (NYSE: NET) | ~$30 Billion | Workers Paid / Edge API Gateway starts at **$5/month base fee** (+$0.30 per million requests beyond standard allowance) | **Free Plan forever**: up to 10 AI Gateways, basic rate limiting (1 rule), up to 10 mTLS client certs, and edge DDoS protection | Ultra-low-latency edge security, WAF, schema validation, and DDoS mitigation across 300+ edge locations. Trade-off: best as an edge protection layer rather than an internal backend service mesh. |
| **[Kong Konnect](https://konghq.com/products/kong-konnect)** | Kong Inc. | ~$2.0 Billion (Private) | Konnect Plus: starts at **$25/month** (Serverless control plane), **$200/month** (Hybrid runtime), or **$500/month** (Dedicated Cloud); includes 1M requests/mo | **30-Day Free Trial** with full SaaS Konnect control plane access, enterprise plugin catalog, and analytics credits | Market-leading cloud-native gateway ecosystem with hundreds of community/commercial plugins and AI Gateway support. Trade-off: full Konnect control plane is proprietary SaaS. |
| **[Tyk Cloud](https://tyk.io/pricing/)** | Tyk Technologies | ~$150 Million (Private) | Core Tier starts at **~$350/month** (consumption/data plane based model); Professional flat rate plans available | **48-Hour Full SaaS Trial** with unlimited APIs, unlimited gateway calls, dashboard access, and developer portal (no credit card required) | Rich out-of-the-box management suite with built-in developer portal, MCP gateway for AI tools, and zero vendor lock-in. Trade-off: short trial period; GUI dashboard is proprietary. |
| **[Gravitee Cloud](https://www.gravitee.io/pricing)** | Gravitee.io | ~$120 Million (Private) | Planet Tier starts at **$2,500/month** (flat-rate production tier covering 1 prod gateway, 1 non-prod gateway, and unlimited users) | **14-Day Free Enterprise Trial** with full access to Gravitee Cloud control plane, event brokers, and alert engines; free tier limited to 2 environments | Event-native API management supporting Kafka, MQTT, and Solace alongside REST/GraphQL. Trade-off: entry price for production tier requires enterprise budget. |

---

## Open-Source GitHub Projects

The table below lists open-source enterprise API gateways and traffic proxies, ranked in descending order by GitHub Stars:

| Repository / Project | GitHub Stars | Tech Stack | License | Core Capabilities & Architecture |
| :--- | :--- | :--- | :--- | :--- |
| **[Traefik](https://github.com/traefik/traefik)** | [![Traefik Stars](https://img.shields.io/github/stars/traefik/traefik?style=social&color=white)](https://github.com/traefik/traefik/stargazers) | Go | MIT | Modern HTTP reverse proxy and ingress controller designed specifically for microservices, Docker, and Kubernetes with automatic discovery and Let's Encrypt SSL automation. |
| **[Kong Gateway](https://github.com/Kong/kong)** | [![Kong Stars](https://img.shields.io/github/stars/Kong/kong?style=social&color=white)](https://github.com/Kong/kong/stargazers) | OpenResty, Lua | Apache-2.0 | The most adopted cloud-native API gateway. Extensive plugin hub for auth (OAuth2/JWT/Key), rate limiting, traffic shaping, observability, and Kubernetes Ingress Controller. |
| **[Envoy Proxy](https://github.com/envoyproxy/envoy)** | [![Envoy Stars](https://img.shields.io/github/stars/envoyproxy/envoy?style=social&color=white)](https://github.com/envoyproxy/envoy/stargazers) | C++ | Apache-2.0 | High-performance edge/middle/service proxy created by Lyft. Serves as the foundational data plane for modern service meshes (Istio) and Kubernetes Gateway API implementations. |
| **[Apache APISIX](https://github.com/apache/apisix)** | [![APISIX Stars](https://img.shields.io/github/stars/apache/apisix?style=social&color=white)](https://github.com/apache/apisix/stargazers) | Lua, NGINX | Apache-2.0 | Dynamic, high-performance API gateway with etcd-backed real-time configuration sync (zero-restart hot reloads). Native support for Wasm plugins, gRPC, and multi-protocol routing. |
| **[Netflix Zuul](https://github.com/Netflix/zuul)** | [![Zuul Stars](https://img.shields.io/github/stars/Netflix/zuul?style=social&color=white)](https://github.com/Netflix/zuul/stargazers) | Java | Apache-2.0 | Battle-tested edge gateway service developed by Netflix. Provides dynamic routing, monitoring, resiliency, and security at massive cloud scale across JVM ecosystems. |
| **[Tyk Gateway](https://github.com/TykTechnologies/tyk)** | [![Tyk Stars](https://img.shields.io/github/stars/TykTechnologies/tyk?style=social&color=white)](https://github.com/TykTechnologies/tyk/stargazers) | Go | MPL-2.0 | Fast, lightweight Go-based API gateway. Features native support for REST, GraphQL, gRPC, MCP (Model Context Protocol for AI agents), rate limiting, and hitless reloads. |
| **[Lura Project / KrakenD CE](https://github.com/luraproject/lura)** | [![Lura Stars](https://img.shields.io/github/stars/luraproject/lura?style=social&color=white)](https://github.com/luraproject/lura/stargazers) | Go | Apache-2.0 | Ultra-fast, stateless API gateway engine powering KrakenD. Single binary deployment, zero external database requirements, declarative configuration, and extreme throughput. |
| **[Spring Cloud Gateway](https://github.com/spring-cloud/spring-cloud-gateway)** | [![Spring Cloud Gateway Stars](https://img.shields.io/github/stars/spring-cloud/spring-cloud-gateway?style=social&color=white)](https://github.com/spring-cloud/spring-cloud-gateway/stargazers) | Java | Apache-2.0 | Non-blocking API Gateway built on top of Spring Framework 5, Project Reactor, and Spring Boot 2/3. Native choice for Spring Boot microservice architectures. |
| **[Emissary-Ingress](https://github.com/emissary-ingress/emissary)** | [![Emissary Stars](https://img.shields.io/github/stars/emissary-ingress/emissary?style=social&color=white)](https://github.com/emissary-ingress/emissary/stargazers) | Go, Python | Apache-2.0 | Open-source Kubernetes-native API Gateway and Ingress Controller built on Envoy Proxy. Provides declarative routing, OAuth filters, and self-service configuration. |
| **[Envoy Gateway](https://github.com/envoyproxy/gateway)** | [![Envoy Gateway Stars](https://img.shields.io/github/stars/envoyproxy/gateway?style=social&color=white)](https://github.com/envoyproxy/gateway/stargazers) | Go | Apache-2.0 | Official Envoy project simplifying Envoy Proxy adoption as an ingress gateway, exposing an idiomatic implementation of the Kubernetes Gateway API. |
| **[Express Gateway](https://github.com/ExpressGateway/express-gateway)** | [![Express Gateway Stars](https://img.shields.io/github/stars/ExpressGateway/express-gateway?style=social&color=white)](https://github.com/ExpressGateway/express-gateway/stargazers) | JavaScript (Node.js) | Apache-2.0 | Fully featured microservices API gateway built entirely on Express.js. Perfect for Node.js environments seeking familiar middleware and plugin extensions. |
| **[WSO2 API Manager](https://github.com/wso2/product-apim)** | [![WSO2 Stars](https://img.shields.io/github/stars/wso2/product-apim?style=social&color=white)](https://github.com/wso2/product-apim/stargazers) | Java | Apache-2.0 | Complete open-source full-lifecycle API management platform featuring API design, publisher portal, developer store, key management, and traffic analytics. |
| **[Gravitee APIM](https://github.com/gravitee-io/gravitee-api-management)** | [![Gravitee Stars](https://img.shields.io/github/stars/gravitee-io/gravitee-api-management?style=social&color=white)](https://github.com/gravitee-io/gravitee-api-management/stargazers) | Java | Apache-2.0 | Flexible, lightweight open-source APIM platform with an intuitive management UI, developer portal, traffic policy engine, and MongoDB/Elasticsearch persistence. |

---

## Architecture & Evaluation Trade-offs

When choosing between cloud-hosted SaaS platforms and self-hosted open-source gateways, consider the following technical dimensions:

1. **State & Storage Architecture:**
   - **Stateless Gateways (KrakenD/Lura, Envoy):** No persistent backing database. Configuration is injected via declarative YAML/JSON files or control-plane xDS gRPC APIs. Unmatched throughput and zero database operations.
   - **Dynamic / Stateful Gateways (Kong, Apache APISIX):** Kong traditionally leverages PostgreSQL (or declarative DB-less mode). Apache APISIX uses an `etcd` cluster to distribute updates instantly across all nodes without reload downtime.
2. **Control Plane vs. Data Plane Separation:**
   - Modern enterprise stacks isolate the **data plane** (the high-performance proxy routing client requests) from the **control plane** (the GUI, policy registry, and credential store). Platforms like Kong Konnect, Tyk Cloud, and Envoy Gateway standardize this separation.
3. **Protocols & Emerging AI Gateways:**
   - Leading gateways in 2026 now natively inspect JSON-RPC 2.0 (Model Context Protocol / MCP) and LLM endpoints to enforce token rate limiting, multi-model fallback, cost telemetry, and prompt guardrails directly at the network boundary.

---

## How to Contribute

We welcome community contributions! To add a new enterprise gateway or update existing benchmarks:

1. **Fork** the repository.
2. Create a new branch: `git checkout -b add-new-gateway`.
3. Add your entry to `README.md` maintaining alphabetical or sorted table standards. Ensure factual pricing, verified free tiers, and official website links.
4. Open a **Pull Request** detailing the addition and relevant use cases.

---

## Disclaimer

- This is an independent, community-curated repository and does not represent an endorsement of any commercial platform or vendor.
- Pricing metrics, product features, and star counts reflect public availability and vendor documentation as of November 2026. Always confirm terms with respective vendors prior to production procurement.

---

**Made with ❤️ for platform engineers, infrastructure architects, and API teams worldwide.**
