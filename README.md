<div align="center">

# Sherwin Samuel

**Senior Software Engineer · Tech Lead · Solution Architect**

<img src="https://readme-typing-svg.demolab.com?font=JetBrains+Mono&size=17&duration=2600&pause=900&center=true&vCenter=true&width=760&color=58A6FF&lines=I+take+messy+problems+and+ship+systems+that+survive+production.;Measure+first.+Then+fix+the+thing+that+is+actually+slow.;Design+the+failure+path+before+the+happy+path.;Releases+nobody+notices.+That's+the+point.;Now+I+also+get+paid+to+break+things." alt="typing intro"/>

<br/>

<a href="https://www.linkedin.com/in/sherwin-samuel-a9a8941a1/"><img src="https://img.shields.io/badge/LinkedIn-say%20hi-0A66C2?style=for-the-badge&logo=linkedin&logoColor=white"/></a>
&nbsp;
<a href="mailto:sherwinlukes@gmail.com"><img src="https://img.shields.io/badge/Email-sherwinlukes%40gmail.com-EA4335?style=for-the-badge&logo=gmail&logoColor=white"/></a>
&nbsp;
<img src="https://img.shields.io/badge/Karachi-UTC%2B5-3fb950?style=for-the-badge&logo=googlemaps&logoColor=white"/>

<sub>Shipped for teams in &nbsp;:us: &nbsp;:de: &nbsp;:finland: &nbsp;:united_arab_emirates: &nbsp;:pakistan:</sub>

<br/><br/>

<img src="./assets/divider.svg" width="900" alt=""/>

</div>

## The short version

I've been building production software since 2019. Seven years, five industries, a lot of 2 a.m. incidents.

I lead a small team and own architecture and delivery end to end: requirements, system design, APIs, database performance, cloud infrastructure and the release itself. I also own QA on a separate platform, which means I spend part of my week trying to break the kind of thing I spend the rest of my week building. Both halves make the other one better.

I'm at my best when the problem is a bit uncomfortable. Data sources that disagree with each other. An endpoint that takes a minute. A third-party API that returns errors nobody documented. A release process only one person understands.

I like finding out what is *actually* happening, fixing that, and leaving the system simpler than I found it.

<br/>

<div align="center">
<img src="./assets/system-layers.svg" width="960" alt="Animated isometric view of a layered system: clients, API, async workers, data. Requests flow down, responses flow up, one fails and retries."/>
</div>

<br/>

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

Before I draw a single box, this is what I'm actually looking at:

```mermaid
%%{init: {'theme': 'base', 'themeVariables': { 'primaryColor': '#161b22', 'primaryTextColor': '#e6edf3', 'primaryBorderColor': '#30363d', 'lineColor': '#8b949e', 'fontFamily': 'JetBrains Mono, Consolas, monospace', 'cScale0': '#6e4fc4', 'cScale1': '#2a5db5', 'cScale2': '#a2691b', 'cScale3': '#1c6a72', 'cScale4': '#b83280', 'cScaleLabel0': '#fff', 'cScaleLabel1': '#fff', 'cScaleLabel2': '#fff', 'cScaleLabel3': '#fff', 'cScaleLabel4': '#fff' }}}%%
mindmap
  root((a new problem))
    People
      who is waiting on this
      what happens if it is late
      who maintains it after me
    Data
      where it comes from
      how much of it is wrong
      what we do when sources disagree
    Failure
      everything we do not own
      timeouts · retries · fallbacks
      how we find out before the customer does
    Delivery
      the thinnest useful slice
      how it gets to production
      how it gets rolled back
    Cost
      what it adds to the system
      what it lets us delete
```

The questions I actually ask in the first meeting:

- **Who is waiting on this, and what happens if it's late?** A tax return and a news feed have very different failure budgets.
- **What data do we trust, and how much?** When two sources disagree about the same record, the answer usually isn't picking one. It's telling the user how confident we are.
- **What already exists that we're replacing?** If the first version isn't at least as easy as the spreadsheet it replaces, nobody will use it.
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

## Design for the day it breaks

External APIs fail. Queues back up. Data gets weird. Users find edge cases. Production is not the happy path, so I don't design as if it is.

Here's how I treat every call to something I don't own. The happy path is one line. The rest is the job.

```mermaid
%%{init: {'theme': 'base', 'themeVariables': { 'primaryColor': '#161b22', 'primaryTextColor': '#e6edf3', 'primaryBorderColor': '#30363d', 'lineColor': '#8b949e', 'fontFamily': 'JetBrains Mono, Consolas, monospace' }}}%%
stateDiagram-v2
    direction LR
    [*] --> Calling: request with a deadline
    Calling --> Done: 2xx
    Calling --> Retrying: timeout or 5xx
    Retrying --> Calling: backoff with jitter
    Retrying --> Degraded: retries exhausted
    Calling --> Rejected: 4xx
    Rejected --> Surfaced: show the real reason, not "error"
    Degraded --> Served: cached or partial answer
    Degraded --> Queued: park it, retry later
    Queued --> Calling: worker picks it up
    Served --> Alerted: someone gets paged
    Queued --> Alerted: dead letter after N tries
    Done --> [*]
    Surfaced --> [*]
    Alerted --> [*]
```

The rules behind it:

- **Every call has a timeout.** No exceptions. A call without one is a call that can hang forever.
- **Retries have backoff and a ceiling.** Retrying instantly turns a hiccup into an outage.
- **Degraded beats down.** A cached answer, a partial page or a "we'll email you" is almost always better than a spinner.
- **The user sees the real reason.** "Something went wrong" is a bug report waiting to happen.
- **Someone finds out.** If a failure path ends without a metric or an alert, it's not finished.

<div align="center"><img src="./assets/divider.svg" width="900" alt=""/></div>

## Measure first

I've taken an endpoint from about a minute down to under two seconds. The fix wasn't a new framework or a rewrite. It was profiling it, fixing the queries, adding the indexes that should have been there, caching the expensive lookups and streaming the response instead of buffering it.

That's the pattern nearly every time. The slow thing is rarely the thing people assume is slow.

```mermaid
%%{init: {'theme': 'base', 'themeVariables': { 'primaryColor': '#161b22', 'primaryTextColor': '#e6edf3', 'primaryBorderColor': '#30363d', 'lineColor': '#8b949e', 'fontFamily': 'JetBrains Mono, Consolas, monospace' }}}%%
flowchart LR
    S(["it's slow"]) --> M["measure it<br/><i>p95, not the average</i>"]
    M --> W{"where does<br/>the time go?"}
    W -->|"database"| Q["query plan · indexes · N+1"]
    W -->|"network"| N["timeouts · payload size · round trips"]
    W -->|"compute"| C["cache it · batch it · move it async"]
    W -->|"the client"| U["stream it · paginate it · render less"]
    Q --> R["measure again"]
    N --> R
    C --> R
    U --> R
    R -->|"still slow"| W
    R -->|"fast enough"| F(["stop. don't over-optimise."])
    style S fill:#3a1a1a,stroke:#f85149,color:#fff
    style F fill:#1c6a72,stroke:#3ddbd9,color:#fff
    style W fill:#a2691b,stroke:#e3b341,color:#fff
```

<div align="center"><img src="./assets/divider.svg" width="900" alt=""/></div>

## Make shipping boring

Release day used to be an hour of one person carefully doing things in the right order. I've replaced that with CI and zero-downtime deploys that take under five minutes. Now it looks like this:

<div align="center">
<img src="./assets/deploy.svg" width="900" alt="Animated terminal: git push, CI passes, image built, rolling deploy with zero downtime, health checks green, released in under five minutes."/>
</div>

```mermaid
%%{init: {'theme': 'base', 'gitGraph': {'showBranches': true, 'showCommitLabel': true, 'mainBranchName': 'main'}, 'themeVariables': { 'git0': '#58a6ff', 'git1': '#bc8cff', 'gitBranchLabel0': '#0d1117', 'gitBranchLabel1': '#0d1117', 'commitLabelColor': '#e6edf3', 'commitLabelBackground': '#161b22', 'tagLabelColor': '#0d1117', 'tagLabelBackground': '#3fb950', 'tagLabelBorder': '#3fb950' }}}%%
gitGraph
    commit id: "prod"
    branch feat/the-thing
    checkout feat/the-thing
    commit id: "thin slice"
    commit id: "tests for the ugly cases"
    commit id: "review notes"
    checkout main
    merge feat/the-thing id: "CI green, auto deploy" tag: "v2.14"
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

## Building it and breaking it

For years I was the engineer whose code got tested. Now I also write the tests: Playwright for web, Appium for mobile, JMeter for load, and the kind of API tests that send the wrong thing on purpose.

It changed how I design. Every error path I used to skip is now a test case I have to write, so I stopped skipping them.

## Leading, briefly

I lead a small team and stay hands-on: architecture, code review, requirements, QA, delivery, and whatever is on fire. I've run 15+ technical interviews and spend a lot of time mentoring.

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
