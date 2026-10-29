---
layout: post
title: "Alpine Linux: the distro we use and don't use"
date: 2025-02-20 13:00:00 +0000
categories: [docker, linux]
tags: [docker, alpine, linux, kubernetes, kind, devops, home-lab]
description: "Why Alpine Linux is more than a small Docker base image, explained in Arabic: image size, build time and running it as a real OS."
image:
  path: /assets/images/posts/alpine/cover.jpg
  alt: Alpine Linux and Docker logos
---

*This post is in Egyptian Arabic, as I first wrote it on LinkedIn.*

<div dir="rtl" class="rtl-post" markdown="1">

🔥 **هتكلم النهارده عن حاجة بنستخدمها، وفي نفس الوقت... مش بنستخدمها!** 🔥

📌 الحاجة دي هي **Alpine Linux**.

إنت كـ DevOps أو مبرمج، أي كان الـ Stack اللي شغال بيه أو الدومين اللي شغال فيه، بتحتك بالـ Docker، ولأنه بقى الـ standard way of packaging applications، فلازم يكون عندك معرفة بالكونتينرز عمومًا. مش شرط تتعمق، لكن معرفة كفاية إنك تشغّل الأبلكيشن بتاعك من غير مشاكل أو مجهود كبير.

طيب نيجي لموضوع النهارده: إزاي بنستخدمه، وإزاي في نفس الوقت مش بنستخدمه؟!

## إزاي بنستخدمه؟

خلينا الأول أقولك إن علشان يبقى عندك Docker image، فإنت عندك Dockerfile بتعمله build، والناتج بيكون الـ Docker image اللي بتشغّله كـ container.

هنركز على الـ Dockerfile، وده باختصار للي ميعرفش: ملف له تسمية خاصة، وهو عبارة عن ملف Text عادي جدًا، لكن جواه شوية أوامر لما بتتنفذ بتطلّعلك الـ Docker image.

أول هذه الأوامر هو `FROM`، ويأتي بعدها الـ OS اللي الأبلكيشن بتاعك هيشتغل عليه، وده بيتسمى الـ **Base Image**. وفيه ناس كتير شوفتهم بيخلوها Ubuntu أو حاجة شبيهة، وبيكون الأمر كالتالي:

</div>

```dockerfile
FROM ubuntu:latest
# or
FROM debian:latest
```

<div dir="rtl" class="rtl-post" markdown="1">

الفكرة هنا إن لما بستخدم base image كبيرة في الحجم، فالـ Docker image الناتجة هيكون حجمها كبير هي كمان، وده بيزود وقت الـ Build والـ Deployment وحاجات تانية كتير، لكن دول اللي يهمونا حاليًا.

طيب هل فيه حل؟ أه، الحل إني أشوف OS يكون حاجة lite أقدر أشغّل عليه الدنيا، وفي نفس الوقت يديني حجم صغير. وأنا هنا بتكلم على **Alpine** 💡

وهي عبارة عن توزيعة Linux خفيفة جدًا، ومتشال منها حاجات كتير مش محتاجها علشان أرن الأبلكيشن بتاعي.

خلينا نديك مثال:

- لو أنا مستعمل Ubuntu as base image، فحجم الـ Docker image هيكون مثلًا 900 MB.
- ولو مستعمل Alpine as base image، فحجم الـ Docker image هيكون مثلًا 30 MB.

أعتقد الفرق واضح.

## إزاي مش بنستخدمه؟

نيجي للجزئية التانية، وهي إزاي مش بنستخدمها 🤔

أقولك إن 90% من الناس اللي شوفتها واشتغلت معاها ومتابعها بيقتصر استخدامها لـ Alpine Linux في الـ Dockerfile وبس.

أنا مؤخرًا بدأت أستخدمه كـ OS على VM وعلى Bare metal، واللي لاحظته إن الأداء روعة، والـ Resources اللي واخدها تكاد لا تُذكر. وحاليًا بنيت بيه **Multi-Node Kubernetes cluster** كـ Home Lab، وده هيكون الموضوع القادم بإذن الله.

لو كملت قراءة لحد هنا، حابب أشكرك وأطلب منك تشاركني: لو استخدمت Alpine قبل كده وفادك إزاي، ولو عندك Docker Image كبيرة وعايز تصغّر حجمها، قولي وهنحلها سوا!

أي سؤال أو حاجة مش واضحة، سيبلي تعليق وأنا هحاول أبسّط الأمور أكتر.

</div>
