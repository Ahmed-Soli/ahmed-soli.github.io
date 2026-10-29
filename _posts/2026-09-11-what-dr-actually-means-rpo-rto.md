---
layout: post
title: "Disaster Recovery, Post 01: What DR actually means (RPO and RTO, plainly)"
date: 2026-09-11
categories: [disaster-recovery]
tags: [dr, rpo, rto, sre, kubernetes]
description: "The first post in a series on disaster recovery: what RPO and RTO really mean, and why the data layer usually decides your recovery time."
---

It's been over a year since I last posted publicly, not for lack of things to say. I've been heads-down doing work worth writing about, and I'd rather share something real than post for the sake of it.

This is the start of a series on disaster recovery. Not the vendor-brochure version, the actual moving parts: network, CI/CD, the data layer, DNS, Kubernetes, the boring NAT gateway nobody diagrams. Most of what I've learned about reliability came from watching one of these quietly fail while everyone assumed it was fine.

## Why now

In March 2026, an AWS region in the Gulf went dark for hours after the physical data center was struck amid the regional conflict, with recovery for some services taking months. "The cloud provider will handle it" stopped being a safe assumption the day a whole availability zone lost power over something happening outside the building, not inside it. No provider is immune. That's when DR stops being a checkbox for a lot of teams here.

## RPO and RTO

Every DR conversation I've sat in starts the same way: someone says "we have backups," like that settles it.

It doesn't. Backups tell you data exists somewhere. Not how much of it you can lose, or how long users stare at an error page while you get it back.

- **RPO, Recovery Point Objective:** how much data you're willing to lose. How much of the last few minutes or hours you're okay writing off.
- **RTO, Recovery Time Objective:** how long you're willing to be down. How long the business can actually survive without it.

Nobody answers either honestly in a planning meeting. Everyone wants both at zero. The honest version only happens once, mid-incident, when someone finally says the real number because the alternative is worse.

## Measure it, don't guess

The only way to know your real numbers is to run the exercise: a real backup and restore, timed, not a tabletop discussion. In any decent DR program it's a recurring drill, not a yearly checkbox. Almost every time, the data layer turns out to decide the outcome: assuming compute and networking already come up cleanly in a second region, it alone can eat roughly 80% of total recovery time.

That's also where architecture choice matters: active-active, active-passive, or warm standby. Each trades cost and complexity for a different RTO, and for most companies the right answer isn't "active-active everywhere," it's picking the right pattern per system. More on that once we're deep in the data layer.

## Next up

The cast of characters that has to work together for a region loss to be survivable: network, CI/CD, the data layer, DNS, Kubernetes, and the boring NAT gateway nobody diagrams. Most get ignored until the day one turns out to be the reason failover didn't work.

What's the real number your team would say out loud if I asked your RTO right now, not the one in the doc?
