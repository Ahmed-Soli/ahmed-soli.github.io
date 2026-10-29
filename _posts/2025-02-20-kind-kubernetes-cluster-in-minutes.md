---
layout: post
title: "The easiest way to run a Kubernetes cluster on your laptop with KinD"
date: 2025-02-20 12:00:00 +0000
categories: [kubernetes]
tags: [kubernetes, kind, docker, home-lab, devops, cloud]
description: "How to run a single-node or multi-node Kubernetes cluster inside Docker in minutes with KinD, explained in Arabic."
image:
  path: /assets/images/posts/kind/01.jpg
  alt: Kubernetes multi-node cluster in 10 minutes
---

*This post is in Egyptian Arabic, as I first wrote it on LinkedIn.*

<div dir="rtl" class="rtl-post" markdown="1">

🚀 **أسهل طريقة تعمل بيها Kubernetes Cluster على جهازك في دقايق!**

سواء هتستخدمها كـ test environment أو كـ Lab تذاكر عليه للشهادات، كل اللي محتاجينه إن يكون عندك Docker متسطب على جهازك. بعد كده هنستعمل حاجة اسمها **KinD**.

## 🐳 إيه هو KinD؟

KinD هو اختصار لـ Kubernetes In Docker، وزي الاختصار ما بيقول، هو أداة بتسمح لك تشغل Kubernetes جوه Docker Containers بسهولة وبدون الحاجة إلى Virtual Machines أو سيرفرات حقيقية.

✅ **مميزاته:**

- ✔ سهل التثبيت: تشغيل Cluster في دقائق
- ✔ مثالي للاختبار والتطوير: بدون الحاجة إلى موارد ضخمة
- ✔ يعمل على أي بيئة: Windows / Mac / Linux
- ✔ يدعم Multi-Node Clusters

## 📌 1️⃣ تثبيت KinD

تقدر تثبّت KinD عن طريق الأوامر التالية (الـ documentation [هنا](https://kind.sigs.k8s.io/docs/user/quick-start/#installation)):

</div>

```bash
# pick the current version from the KinD installation docs
curl -Lo ./kind https://kind.sigs.k8s.io/dl/<version>/kind-linux-amd64
chmod +x ./kind
mv ./kind /usr/local/bin/
```

<div dir="rtl" class="rtl-post" markdown="1">

## 📌 2️⃣ إنشاء الـ Cluster

تقدر تنشئ Kubernetes Cluster بالأمر التالي:

</div>

```bash
kind create cluster
```

<div dir="rtl" class="rtl-post" markdown="1">

🔥 مبروك! بقى عندك Single Node Kubernetes Cluster شغال جوه Docker.

## 🖥 Multi-node Cluster

طيب لو حابب تشغّل KinD على Virtual Machines أو Bare Metal، بمعنى إنك عايز Cluster أكتر واقعية فيها عدد أكبر من Master و Worker Nodes، فالموضوع بسيط. هنعمل ملف yaml فيه إعدادات الـ Cluster كالتالي:

</div>

```yaml
kind: Cluster
apiVersion: kind.x-k8s.io/v1alpha4
nodes:
- role: control-plane
- role: control-plane
- role: worker
- role: worker
```

<div dir="rtl" class="rtl-post" markdown="1">

ثم هننفذ الأمر التالي:

</div>

```bash
kind create cluster --config cluster.yaml
```

<div dir="rtl" class="rtl-post" markdown="1">

🚀 كده بقى عندك Kubernetes Cluster كامل مع 2 Control Plane و 2 Workers!

وده مثال لملف إعدادات بـ 3 control planes و 3 workers، والـ output اللي بيظهر وانت بتنشئه:

![KinD cluster config with three control-plane nodes and three workers](/assets/images/posts/kind/02.jpg)

![kubectl get nodes showing all nodes Ready](/assets/images/posts/kind/03.jpg)

![kind create cluster output](/assets/images/posts/kind/04.jpg)

## 🙏 شكر

الطريقة دي عرفتها وطبقتها وأنا بآخد كورس المهندس Ahmed ElFakharany، وبنصح أي حد مهتم يفهم k8s ياخد الكورس ده.

وبردو فكرة إن يكون عندي الـ cluster بتاعتي شجعني عليها Mischa van den Burg، تابعوه، هو فعلًا تقيل في الحتة دي. Thanks Mischa van den Burg for fostering the mindset of having your own k8s lab.

**شاركنا إزاي بتطبق على k8s؟ وإيه الصعوبات اللي واجهتك؟**

</div>
