---
layout: post
title: "Kubernetes RBAC, simplified"
date: 2025-05-17
categories: [kubernetes]
tags: [kubernetes, rbac, k8s, certificates, kind, devops]
description: "A simple Arabic walkthrough of Kubernetes Role Based Access Control: users, certificates, roles and role bindings."
image:
  path: /assets/images/posts/rbac/cover.jpg
  alt: Gandalf with the Kubernetes logo saying You shall not pass
---

*This post is in Egyptian Arabic, as I first wrote it on LinkedIn.*

<div dir="rtl" class="rtl-post" markdown="1">

🎓 **مراجعة الـ RBAC في Kubernetes، بطريقة مبسطة**

مؤخرًا كنت براجع على حاجة اسمها Role Based Access Control (RBAC) في الـ Kubernetes، وقررت أوثق اللي بعمله وأشاركه على LinkedIn، يمكن يفيد حد زيي بيذاكر أو بيراجع.

## 💡 إيه هي الـ RBAC؟

هي ببساطة طريقة بتخلي كل يوزر يقدر يتعامل بس مع الحاجات اللي مسموحله بيها. يعني الدنيا مش مفتوحة على بعضها، ومفيش حد يقدر "يبوظ حاجة" مش بتاعته 😅

## 🛠️ طيب بعملها إزاي؟

- أول حاجة بعمل Private Key لليوزر.
- بعدين بعمل حاجة اسمها CSR (Certificate Signing Request).
- بعد كده، بأستخدمهم مع الـ Private Key بتاع الـ Cluster علشان أطلّع User Certificate.

## 🤔 طب يعني إيه الكلام ده؟

خلينا نبسطها... أي Cluster في الدنيا بيكون له Private Key و Certificate (يعني شبه بطاقته كده). وأي يوزر علشان الـ Cluster يتعرف عليه، لازم يبعتله بياناته.

فأنا كيوزر بقول للـ Cluster: "أنا اسمي أحمد، ودي بياناتي (CSR) وأنا الوحيد اللي معايا الـ Private Key بتاعي."

الـ Cluster بيقول: "تمام، أنا كمان عندي صلاحية أمضي على بياناتك (كـ Certificate Authority) وهديك بطاقة تعرفني بيك بعد كده (User Certificate)."

📌 وده اسمه **Authentication**: إن اليوزر معروف ومؤكد.

لكن لازم كمان أقول: هو يقدر يعمل إيه؟ وعلى إيه؟ وفين؟ وهنا بييجي دور الـ RBAC.

## 🔐 RBAC = صلاحيات اليوزر جوه الـ Cluster

ببساطة، RBAC بتسمحلي أقول:

- أحمد يقدر يشوف الـ pods بس، لكن ميقدرش يمسحها.
- فاطمة تقدر تعمل deploy وتشوف الـ services.
- علي يقدر يقرأ logs بس من namespace معين.

علشان أطبّق ده، بعمل الآتي:

- ✅ أعمل **Role**: فيها الصلاحيات المطلوبة (زي get أو list أو delete) وعلى أي موارد (زي pods أو services).
- ✅ أعمل **RoleBinding**: أقول فيها اليوزر ده مربوط بالـ Role دي.
- ✅ أستخدم kubeconfig مخصص للـ user علشان أجرب الصلاحيات اللي اديتهاله.

## 🎯 التوثيق على GitHub

والجميل بقى إني بدأت أوثّق كل الخطوات اللي بعملها دي على GitHub في Repo اسمه [k8s-study-guide](https://github.com/Ahmed-Soli/k8s-study-guide).

هتلاقوا فيه خطوات عملية بالظبط عملت بيها Certificate، RBAC، والـ testing باستخدام kubeconfig مختلف.

🚀 لو بتتعلم Kubernetes أو بتراجع زيي، هتلاقي فيه حاجات مفيدة جدًا. ولو عجبك الكلام، قولّي رأيك أو شاركه مع حد مهتم.

أنا عامل عندي Multi-node Cluster على Docker باستخدام KinD، وده [بوست شارح فيه الطريقة]({% post_url 2025-02-20-kind-kubernetes-cluster-in-minutes %}).

وإن شاء الله لسه فيه بوستات تانية كتير من نفس النوعية 💪

</div>
