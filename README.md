<div align="center">

# Sherwin Samuel

**Senior Software Engineer · Tech Lead · Solution Architect**

<img src="https://readme-typing-svg.demolab.com?font=JetBrains+Mono&size=17&duration=2600&pause=900&center=true&vCenter=true&width=760&color=58A6FF&lines=I+take+messy+problems+and+ship+systems+that+survive+production.;First+system+I+ever+worked+on+ran+an+airport.;60-second+API+%E2%86%92+under+2+seconds.+No+new+framework+involved.;Hour-long+releases+%E2%86%92+under+5+minutes.+Nobody+notices.+That's+the+point.;Now+I+also+get+paid+to+break+things." alt="typing intro"/>

<br/>

<a href="https://www.linkedin.com/in/sherwin-samuel-a9a8941a1/"><img src="https://img.shields.io/badge/LinkedIn-say%20hi-0A66C2?style=for-the-badge&logo=linkedin&logoColor=white"/></a>
&nbsp;
<a href="mailto:sherwinlukes@gmail.com"><img src="https://img.shields.io/badge/Email-sherwinlukes%40gmail.com-EA4335?style=for-the-badge&logo=gmail&logoColor=white"/></a>
&nbsp;
<img src="https://img.shields.io/badge/Karachi-UTC%2B5-3fb950?style=for-the-badge&logo=googlemaps&logoColor=white"/>

<sub>Shipped for clients in &nbsp;:us: &nbsp;:de: &nbsp;:finland: &nbsp;:united_arab_emirates: &nbsp;:pakistan:</sub>

<br/><br/>

<img src="./assets/divider.svg" width="900" alt=""/>

</div>

## The short version

I've been building production software since 2019. Seven years, five industries, a lot of 2 a.m. incidents.

Today I lead a team of four at **Quantum Skye**, owning architecture and delivery across two products end to end: requirements, system design, APIs, database performance, cloud infrastructure and the release itself. Since mid-2026 I also own QA for enterprise direct-selling platforms at **Immunotec**, which means I now spend part of my week trying to break the kind of thing I spend the rest of my week building.

I'm at my best when the problem is a bit uncomfortable. Data from seven sources that disagree with each other. An endpoint that takes a minute. A government API that returns errors nobody documented. A release process that only one person understands.

I like finding out what is *actually* happening, fixing that, and leaving the system simpler than I found it.

<br/>

<div align="center">
<img src="./assets/system-layers.svg" width="960" alt="Animated isometric view of a layered system: clients, API, async workers, data. Requests flow down, responses flow up, one fails and retries."/>
</div>

<br/>

## How the story goes

```mermaid
%%{init: {'theme': 'base', 'themeVariables': { 'cScale0': '#6e4fc4', 'cScale1': '#2a5db5', 'cScale2': '#a2691b', 'cScale3': '#1c6a72', 'cScale4': '#b83280', 'cScaleLabel0': '#fff', 'cScaleLabel1': '#fff', 'cScaleLabel2': '#fff', 'cScaleLabel3': '#fff', 'cScaleLabel4': '#fff' }}}%%
timeline
    title Seven years, roughly in order
    2019 : Intern at Alisons Technology, promoted in 30 days
         : Airport operations platforms for Sharjah and Dubai, under Serco
    2020 : Full stack at Grids Hub, Finnish clients
         : The mobile dev leaves. I inherit mobile.
         : Employee of the Year
    2021 : Software Engineer at Quantum Skye
         : Reimeter (PropTech), StyleXchange (NFT marketplace), Islamabad Today (news app)
    2023 : Senior Engineer and Team Lead
         : Reidar and Mason AI, Digitax AI, Napoleon HR
         : 60s API → under 2s. Hour-long releases → under 5 min
    2026 : QA ownership at Immunotec
         : Playwright, Appium, JMeter. Both sides of the bug report.
```

**2019.** My first real job was an internship at Alisons Technology in Karachi. A month in, they made me a junior engineer and put me on ATMARS and ATLOG, the operations logging platforms for Sharjah and Dubai airports. Air traffic controllers used the screens I built to record what was happening on the ground. That's where I learned that a slow report isn't an inconvenience, it's an operational problem, and that the fix is usually an index and a better join, not a rewrite.

**2020.** At Grids Hub I was the primary developer from the Pakistan side for four Finnish client products. Then our only mobile developer left. Nobody else did mobile. I learned React Native from zero and had apps in both stores within months. I also built Dhobi Aya, the company's on-demand laundry startup, alone: customer app, rider app, admin panel, website. I got Employee of the Year, which I mostly attribute to saying yes to the mobile thing.

**2021.** Joined Quantum Skye. Built the first production version of Reimeter, an AI real estate deal analysis platform, including the ingestion layer that turned inconsistent third-party property data into one model. Built an NFT marketplace for a German client that had to stay usable when OpenSea was slow or down. Shipped a React Native news app solo, architecture through store release.

**2023.** Promoted to Senior Engineer and Team Lead. Reimeter became Reidar. I designed the core platform, a pipeline consolidating property data from seven-plus institutional sources with confidence scoring, and Mason, an in-product agent that watches usage and risk signals and intervenes before a user churns. On the side: Digitax, direct integration with Pakistan's tax authority for end-to-end e-filing, and Napoleon, an HR platform with AI-assisted candidate evaluation.

**2026.** Took on QA ownership at Immunotec for platforms built on Exigo: commissions, checkout, enrollment, genealogy. Playwright for web, Appium for mobile, JMeter for load. After years of being the engineer whose code got tested, being the person writing the tests has changed how I design APIs. Every error path I used to skip is now a test case I have to write.

<div align="center"><img src="./assets/divider.svg" width="900" alt=""/></div>

## How I approach a problem

I don't have a favourite architecture I try to fit every project into. I have a loop.

```mermaid
%%{init: {'theme': 'base', 'themeVariables': { 'primaryColor': '#161b22', 'primaryTextColor': '#e6edf3', 'primaryBorderColor': '#58a6ff', 'lineColor': '#8b949e', 'secondaryColor': '#1c6a72', 'tertiaryColor': '#0d1117', 'fontFamily': 'JetBrains Mono, Consolas, monospace' }}}%%
flowchart LR
    A(["What is actually broken?<br/><i>not what the ticket says</i>"]) --> B["Constraints<br/>time · budget · team · data quality"]
    B --> C{"Simplest thing<br/>that could work?"}
    C -->|"not yet"| B
    C -->|"yes"| D["Walk every failure path<br/>timeouts · retries · bad data · partial writes"]
    D --> E["Build the thin slice"]
    E --> F["Measure it in production"]
    F -->|"surprised"| A
    F -->|"boring"| G(["Ship the next slice"])
    G --> A
    style A fill:#6e4fc4,stroke:#bc8cff,color:#fff
    style G fill:#1c6a72,stroke:#3ddbd9,color:#fff
    style C fill:#a2691b,stroke:#e3b341,color:#fff
```

The questions I actually ask in the first meeting:

- **Who is waiting on this, and what happens if it's late?** A tax return and a news feed have very different failure budgets.
- **What data do we trust, and how much?** On Reidar, seven sources disagreed about the same house. The answer wasn't picking one. It was a confidence score that told the user how much to trust the number.
- **What already exists that we're replacing?** The airport systems replaced paper and spreadsheets. The first version had to be at least as easy as the spreadsheet or nobody would use it.
- **What will change in six months?** Not to build for it now, but to avoid painting ourselves into a corner.
- **How will we know it's broken before the customer tells us?**

And the chart I mentally consult before adding anything to a system:

```mermaid
%%{init: {'theme': 'base', 'themeVariables': { 'quadrant1Fill': '#3d2708', 'quadrant2Fill': '#0f3d43', 'quadrant3Fill': '#161b22', 'quadrant4Fill': '#3a1a1a', 'quadrant1TextFill': '#e3b341', 'quadrant2TextFill': '#3ddbd9', 'quadrant3TextFill': '#8b949e', 'quadrant4TextFill': '#f85149', 'quadrantPointFill': '#58a6ff', 'quadrantPointTextFill': '#e6edf3', 'quadrantXAxisTextFill': '#8b949e', 'quadrantYAxisTextFill': '#8b949e', 'quadrantTitleFill': '#e6edf3', 'quadrantInternalBorderStrokeFill': '#30363d', 'quadrantExternalBorderStrokeFill': '#30363d' }}}%%
quadrantChart
    title Do we actually need it yet?
    x-axis Adds little complexity --> Adds a lot of complexity
    y-axis Might need it someday --> Need it today
    quadrant-1 Earn it with evidence first
    quadrant-2 Do it now
    quadrant-3 Cheap, park it
    quadrant-4 Resume driven development
    A database index: [0.10, 0.92]
    Retries and timeouts: [0.34, 0.84]
    Redis on the hot path: [0.22, 0.70]
    Zero downtime deploys: [0.44, 0.93]
    A queue for the slow work: [0.36, 0.58]
    Feature flags: [0.16, 0.40]
    GraphQL: [0.56, 0.24]
    Event driven everything: [0.66, 0.38]
    Microservices on day one: [0.72, 0.22]
    Kubernetes for three services: [0.62, 0.10]
    An AI feature nobody asked for: [0.80, 0.32]
```

Good engineering is mostly knowing when you don't need something.

<div align="center"><img src="./assets/divider.svg" width="900" alt=""/></div>

## Two systems, drawn honestly

### Reidar and Mason: property data from seven sources into one answer

The hard part of PropTech isn't the UI. It's that every data source describes the same property slightly differently, and some of them are wrong.

```mermaid
%%{init: {'theme': 'base', 'themeVariables': { 'primaryColor': '#161b22', 'primaryTextColor': '#e6edf3', 'primaryBorderColor': '#30363d', 'lineColor': '#8b949e', 'clusterBkg': '#0d1117', 'clusterBorder': '#30363d', 'titleColor': '#e6edf3', 'fontFamily': 'JetBrains Mono, Consolas, monospace' }}}%%
flowchart TB
    subgraph SRC["institutional property data · 7+ sources"]
        direction LR
        s1[("source A")] ~~~ s2[("source B")] ~~~ s3[("source C")] ~~~ s4[("… ×7")]
    end
    SRC --> ING["ingestion workers<br/>normalise · dedupe · reconcile conflicts"]
    ING --> CS["confidence scoring<br/><i>how much should you trust this valuation?</i>"]
    CS --> DB[("unified property model")]
    DB --> DA["deal analysis"]
    DB --> BM["buyer matching"]
    DA --> API
    BM --> API
    API["NestJS API<br/>REST · WebSockets · Redis cache"]
    API --> WEB["Next.js app"]
    API --> ADM["admin tooling"]
    API -. "usage · engagement · risk events" .-> SIG

    subgraph MASON["Mason · the agent that notices you leaving"]
        direction LR
        SIG["signals"] --> SCORE["score the user"] --> DEC{"disengaging?"}
        DEC -->|"yes"| ACT["intervene<br/>email · SMS · in-app"]
        DEC -->|"no"| WAIT["keep watching"]
    end

    style CS fill:#a2691b,stroke:#e3b341,color:#fff
    style API fill:#2a5db5,stroke:#58a6ff,color:#fff
    style DB fill:#1c6a72,stroke:#3ddbd9,color:#fff
    style ACT fill:#6e4fc4,stroke:#bc8cff,color:#fff
```

The API in that diagram is the one that used to take about a minute. It now responds in under two seconds. Nothing was rewritten. I profiled it, fixed the queries, added the indexes that should have been there, cached the expensive lookups in Redis and streamed the response instead of buffering it.

```mermaid
%%{init: {'theme': 'base', 'xyChart': {'width': 700, 'height': 300}, 'themeVariables': { 'xyChart': { 'backgroundColor': 'transparent', 'titleColor': '#e6edf3', 'xAxisLabelColor': '#8b949e', 'xAxisTitleColor': '#8b949e', 'xAxisTickColor': '#30363d', 'xAxisLineColor': '#30363d', 'yAxisLabelColor': '#8b949e', 'yAxisTitleColor': '#8b949e', 'yAxisTickColor': '#30363d', 'yAxisLineColor': '#30363d', 'plotColorPalette': '#58a6ff' } }}}%%
xychart-beta
    title "The same endpoint, before and after (seconds)"
    x-axis ["before: one query per row", "indexes", "+ query rewrite", "+ Redis cache", "+ streamed response"]
    y-axis "response time, seconds" 0 --> 65
    bar [60, 31, 12, 4, 1.8]
```

<sub>The intermediate bars are from memory rather than a saved benchmark. The first and last are the ones I'd put my name on.</sub>

### Digitax: filing a tax return with an API that doesn't always answer

Every state in this diagram exists because it happened in production at least once.

```mermaid
%%{init: {'theme': 'base', 'themeVariables': { 'primaryColor': '#161b22', 'primaryTextColor': '#e6edf3', 'primaryBorderColor': '#30363d', 'lineColor': '#8b949e', 'fontFamily': 'JetBrains Mono, Consolas, monospace' }}}%%
stateDiagram-v2
    direction LR
    [*] --> Drafted: return generated from salary data
    Drafted --> Validated: rules pass
    Drafted --> NeedsFix: rules fail
    NeedsFix --> Drafted: taxpayer corrects
    Validated --> Submitting: send to FBR
    Submitting --> Accepted: acknowledged
    Submitting --> Retrying: timeout or 5xx
    Retrying --> Submitting: backoff, then again
    Retrying --> Failed: retries exhausted
    Submitting --> Rejected: FBR says no
    Rejected --> NeedsFix: show the real reason
    Failed --> Drafted: human looks at it
    Accepted --> [*]
```

The happy path is one line. The other eleven are the job. A failed submission here is a real person with a real deadline, so "it errored" was never an acceptable end state.

<div align="center"><img src="./assets/divider.svg" width="900" alt=""/></div>

## What shipping looks like

Release day used to be an hour of one person carefully doing things in the right order. Now it's this:

<div align="center">
<img src="./assets/deploy.svg" width="900" alt="Animated terminal: git push, CI passes, image built, rolling deploy with zero downtime, health checks green, released in under five minutes."/>
</div>

```mermaid
%%{init: {'theme': 'base', 'gitGraph': {'showBranches': true, 'showCommitLabel': true, 'mainBranchName': 'main'}, 'themeVariables': { 'git0': '#58a6ff', 'git1': '#bc8cff', 'gitBranchLabel0': '#0d1117', 'gitBranchLabel1': '#0d1117', 'commitLabelColor': '#e6edf3', 'commitLabelBackground': '#161b22', 'tagLabelColor': '#0d1117', 'tagLabelBackground': '#3fb950', 'tagLabelBorder': '#3fb950' }}}%%
gitGraph
    commit id: "prod"
    branch feat/buyer-matching
    checkout feat/buyer-matching
    commit id: "thin slice"
    commit id: "tests for the ugly cases"
    commit id: "review notes"
    checkout main
    merge feat/buyer-matching id: "CI green, auto deploy" tag: "v2.14"
    commit id: "watch p95 for a day"
    commit id: "small fix" type: HIGHLIGHT
    commit id: "boring again"
```

I enjoy the whole path: `idea → architecture → code → tests → deploy → production → 2 a.m. → improvement`. The last two are where the interesting stuff lives.

<div align="center"><img src="./assets/divider.svg" width="900" alt=""/></div>

## Toolbox

The stack changes per project. These are the ones I've shipped with, not the ones I've read about.

<table align="center">
<tr>
<td align="right"><b>backend</b></td>
<td><img src="https://skillicons.dev/icons?i=nodejs,nestjs,ts,js,dotnet,cs,php,laravel,graphql&perline=9" alt="backend"/></td>
</tr>
<tr>
<td align="right"><b>frontend & mobile</b></td>
<td><img src="https://skillicons.dev/icons?i=react,nextjs,reactnative,html,css,bootstrap&perline=9" alt="frontend and mobile"/></td>
</tr>
<tr>
<td align="right"><b>data</b></td>
<td><img src="https://skillicons.dev/icons?i=mysql,mongodb,redis&perline=9" alt="data"/></td>
</tr>
<tr>
<td align="right"><b>cloud & delivery</b></td>
<td><img src="https://skillicons.dev/icons?i=aws,azure,docker,githubactions,git,github,linux&perline=9" alt="cloud and delivery"/></td>
</tr>
<tr>
<td align="right"><b>quality</b></td>
<td><img src="https://skillicons.dev/icons?i=playwright,postman&perline=9" alt="quality"/>&nbsp;
<img src="https://img.shields.io/badge/Appium-mobile-663399?style=flat-square&logo=appium&logoColor=white" alt="Appium"/>
<img src="https://img.shields.io/badge/JMeter-load-D22128?style=flat-square&logo=apachejmeter&logoColor=white" alt="JMeter"/>
<img src="https://img.shields.io/badge/TestRail-cases-65C179?style=flat-square" alt="TestRail"/>
<img src="https://img.shields.io/badge/Jira-defects-0052CC?style=flat-square&logo=jira&logoColor=white" alt="Jira"/></td>
</tr>
</table>

Also MSSQL, WebSockets, serverless, queues, event-driven processing, and the Android and iOS build, signing and store-release pipeline, which is a skill in the way that filing taxes is a skill.

<div align="center"><img src="./assets/divider.svg" width="900" alt=""/></div>

## Leading, briefly

I lead four engineers and stay hands-on: architecture, code review, requirements, QA, delivery, and whatever is on fire. I've run 15+ technical interviews and spend a lot of time mentoring.

The part I enjoy most is watching someone go from

> "I don't know how to solve this."

to

> "I know how to *approach* this."

Fixing it for them is faster today and slower forever.

## A few opinions, held loosely

- Simple systems are underrated. Boring is a feature.
- A database index can be more exciting than a new framework. It was, five times.
- If everything is a microservice, nothing is simple.
- The best abstraction is the one the next engineer understands without a call.
- Shipping teaches you things architecture diagrams can't. Including that your diagram was wrong.
- The person testing your API should be able to break it. If they can't, they aren't trying.

## Currently curious about

`agentic systems that earn their keep` · `event-driven architecture` · `distributed systems` · `developer experience` · `performance` · `testing that actually catches things`

Especially the places where these overlap.

<div align="center"><img src="./assets/divider.svg" width="900" alt=""/></div>

<div align="center">

<picture>
  <source media="(prefers-color-scheme: dark)" srcset="https://raw.githubusercontent.com/Webtech12/Webtech12/output/github-snake-dark.svg"/>
  <source media="(prefers-color-scheme: light)" srcset="https://raw.githubusercontent.com/Webtech12/Webtech12/output/github-snake.svg"/>
  <img src="https://raw.githubusercontent.com/Webtech12/Webtech12/output/github-snake-dark.svg" alt="a snake eating my contribution graph" width="900"/>
</picture>

<sub>most of my commits live in private repos. the snake makes do.</sub>

<br/><br/>

## Let's build something useful

If you're working on an interesting engineering problem, an ambitious product, or a system currently doing something it absolutely should not be doing:

<a href="mailto:sherwinlukes@gmail.com"><img src="https://img.shields.io/badge/Email-say%20hello-EA4335?style=for-the-badge&logo=gmail&logoColor=white"/></a>
&nbsp;
<a href="https://www.linkedin.com/in/sherwin-samuel-a9a8941a1/"><img src="https://img.shields.io/badge/LinkedIn-connect-0A66C2?style=for-the-badge&logo=linkedin&logoColor=white"/></a>

<br/><br/>

<sub>Build something useful. Then make it better.</sub>

</div>
