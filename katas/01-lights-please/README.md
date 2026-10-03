# Kata 01: Lights, Please

> **Status:** In progress · **Timebox:** 2–3 hours · **Original brief:** [Neal Ford's Architectural Katas](https://nealford.com/katas/list.html)

## 1. The brief

A large home-electronics company wants to enter the home-automation market with a new product line: devices that turn lights on and off, lock and unlock doors, show live camera images and control the thermostat, with more device types to come later.

- **Users:** consumers, mostly small families. The company expects to sell thousands of units in the first three years.
- **Requirements:**
  - As close to plug-and-play as possible, but sold as separate modules (camera, lock, thermostat, etc.) that customers can buy one at a time.
  - Devices must be reachable over the Internet for remote monitoring and control, using the customer's existing Wi-Fi.
  - Customers can program how the modules behave, to fit their own needs.
  - Another team builds the hardware. The communication protocol is up to me: they'll implement the device side once I specify it.
- **Business context:**
  - The company is ready to invest heavily to launch this line of business.
  - It wants to collect data from customers who opt in, for wider statistics.
  - It's an international company.

## 2. Questions for the client

<!-- Some areas worth thinking about: what happens when the home Internet connection
     drops; how fast a lock or light must respond; security and certification for door
     locks; video storage and retention; data protection rules in different countries
     (GDPR); firmware updates; how long devices are supported; integration with existing
     ecosystems (voice assistants, Matter); and the business model (one-off purchase vs.
     subscription), which changes how much cloud cost is acceptable. -->

There's no client to answer these, so each question comes with the assumption I designed around.

| # | Question | Why it matters | My assumption |
| --- | --- | --- | --- |
| 1 | Can we ask customers to change their home network settings (for example, open ports on their router), or must the devices work with a standard home router out of the box? | It decides how commands reach a device inside a home network from the Internet. | No network changes. Customers won't open their home network to the Internet, so devices only make outgoing connections, and commands are pushed to them over those connections. |
| 2 | How up to date do the opt-in statistics for the company need to be? | It decides whether statistics are computed in real time or in periodic batches, which changes cost and complexity. | A delay of a few hours is fine. Statistics are computed in batches, not in real time. |
| 3 | How many customers and devices do you expect, and how many will use remote access at the same time? | It drives capacity, load balancing and failover. | Thousands of units in the first three years, as the brief says, but the design should grow to hundreds of thousands of homes without a rewrite. |
| 4 | What availability do you expect for remote access? | It decides how much redundancy and backup the platform needs. | 99.9% for remote access, about 9 hours of downtime a year. That's enough because core functions keep working locally when the cloud is down (see question 6). |
| 5 | How quickly must a device react to a command? Within a second, or is a short delay acceptable? | It decides how the platform and the devices communicate. | Commands like locking a door or switching a light should take effect within a couple of seconds. |
| 6 | Must locks, lights and customers' rules keep working when the home Internet connection or our cloud platform is down? | It decides what runs locally in the home and what runs in the cloud. | Yes. Core functions keep working locally. Only remote access needs the Internet. |
| 7 | Which security standards and certifications must the locks and cameras meet? | Door locks and cameras are high-risk devices, and the EU has cybersecurity rules for connected devices. | Security is a top priority, and the devices must meet EU requirements for connected devices. |
| 8 | Where is camera video stored, for how long, and who pays for the storage? | Video is by far the most expensive data in the system, in both bandwidth and storage. | Live view is included. Cloud recording is an optional subscription with limited retention. |
| 9 | How complex are the "programs" customers create? Simple rules, or something closer to scripting? | It decides whether we need a simple rules engine or a much larger automation platform. | Simple rules and scenes, created in the app (for example, "at sunset, turn on the lights"). |
| 10 | In which countries will the product be sold, and are there rules about where customer data must be stored? | "International" brings GDPR and similar laws, which affect where servers run and how the opt-in statistics are anonymized. | Data from EU customers stays in the EU, and the statistics only use anonymized data. |

## 3. Architecture characteristics

<!-- Candidates to choose from: availability, security, privacy, interoperability,
     extensibility, scalability, elasticity, reliability when offline, deployability
     (over-the-air updates), cost. Pick the top three and say why. -->

| Characteristic | Why it matters here |
| --- | --- |
|  |  |
|  |  |
|  |  |

**Also considered:**

## 4. Components

<!-- Think about where things run: on the device, in the home (is there a hub?),
     in the cloud, and in the customer's app. Which component owns device registration,
     the rules customers program, remote commands, video, telemetry, firmware updates
     and the opt-in statistics? -->

| Component | Responsibility |
| --- | --- |
|  |  |

## 5. Architecture style

<!-- Which style fits, and why? Link the ADR that records the choice. -->

## 6. Diagrams

### System context

```mermaid
flowchart LR
    owner([Home owner]) --> app[Mobile / web app]
    app --> platform[Home automation platform]
    platform --> devices[Devices in the home]
    platform --> ext[External services]
```

### Containers

```mermaid
flowchart LR
    subgraph Cloud
        api[API] --> db[(Database)]
    end
    subgraph Home
        device[Device]
    end
    device <--> api
```

## 7. Decisions

<!-- Likely candidates for ADRs: hub vs. no hub in the home; the device protocol
     (e.g. MQTT, CoAP, Matter or your own); where customer rules run (device, hub or
     cloud); how video is streamed and stored; how firmware updates are rolled out;
     how opt-in data is separated from personal data. -->

| ADR | Decision | Status |
| --- | --- | --- |
| [0001](adr/0001-title.md) |  | Proposed |

## 8. Risks and trade-offs

## 9. With more time
