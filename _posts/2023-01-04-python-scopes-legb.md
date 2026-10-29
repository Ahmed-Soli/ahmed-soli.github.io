---
layout: post
title: "Python scopes: built-in, global, enclosing and local"
date: 2023-01-04
categories: [python, deep-dive]
tags: [python, scope, global, nonlocal, closures, decorators, deep-dive-with-ahmed]
description: "Deep Dive with Ahmed, in Arabic: the four Python scopes, why you can read but not modify an outer variable, and the global and nonlocal keywords."
image:
  path: /assets/images/posts/python-threads/scopes.png
  alt: Nested circles showing the Python scopes - built-in, global, enclosing and local
---

*This post is in Egyptian Arabic, as I first wrote it on LinkedIn. It is part of my "Deep Dive with Ahmed" series.*

<div dir="rtl" class="rtl-post" markdown="1">

ده رابع بوست ليا أتكلم عن حاجة أنا بتعلمها: **Python Scopes**.

ساعات كده تبقى جوه فانكشن وتيجي تعدّل على variable إنت حاطه برا الفانكشن، وتلاقي طلعلك error بيقولك الـ variable ده undefined. طيب وهو مش المفروض يعني إن الـ variable ده موجود في حتة الكود كله بيشوفها؟ هقولك أه، اسمها global scope. هتقولي أمال إزاي بقى الكود مش شايفها؟ هقولك عشان الموضوع له سيناريوهات كتير.

خلينا الأول نشوف عندنا كام scope في اللغة:

## 1. Built-in scope

ودي فيها كل الفانكشنز التابعة للغة نفسها، زي مثلًا `print`. دي مش محتاج تكون إنت معرفها عشان تشتغل لأنها بالفعل متعرفة.

## 2. Global scope (أو Module scope)

ودي من اسمها: أي حاجة بتعرفها جوه ملف البايثون بتاعك، فهو ده يعتبر جلوبال لكل الكود بتاعك. يعني لو معرّف مثلًا متغير اسمه `name = 'ahmed'` وجيت جوه دالة تستعمل المتغير اللي اسمه `name` ده، الدالة مش هتعترض. لكن هتعترض لما تيجي تعدل عليه، لأنه مش جوه الدالة نفسها.

فعشان أعدل عليه لازم أقول للدالة إن أه، أنا عاوز أعدل على المتغير اللي في الجلوبال، عن طريق استخدام كلمة `global` ثم أحط بعدها اسم المتغير، ولازم تكون أول سطر في الدالة. يعني بعد ما أعرّف الدالة بتاعتي `def func():` هاجي على طول حاطط السطر الجميل ده `global name`، ثم أقدر أعدل على الـ `name` براحتي.

## 3. Local scope

وده من اسمه بردو خاص بالدالة نفسها. يعني لو عندي دالة وعرفت جواها متغير سميته `name`، بردو الكود بتاعي مش هيشوف الـ `name` اللي في الجلوبال وهيشوف اللي جوه الدالة فقط. وبالمناسبة الـ local scope بيروح من الميموري بمجرد ما الدالة تنتهي.

## 4. Enclosing scope (أو nonlocal scope)

ده بقى مهم جدًا جدًا جدًا لأنه مبني عليه حاجة فخمة زي الـ **closures** والـ **decorators**، وهو بيحصل لما يكون عندي دالتين جوه بعض. خلينا نقول إن الأولى اسمها `outer` واللي جواها `inner`. لو جيت عرفت متغير جوه الـ `outer`، ده معناه إنه بقى local لـ outer.

طيب هل ينفع أقرا المتغير ده من جوه الـ inner؟ هقولك أه، لأنه بقى جلوبال ليه. ولكن مش هقدر أعدل عليه من جوه inner. طيب ليه؟ لأنه برّاه.

طيب نحلها إزاي؟ أقولك بسيطة: زي ما فيه كلمة اللغة عاطيهالنا عشان نعدل على الجلوبال، فيه بردو كلمة اللغة عاطيهالنا عشان نعدل على الـ nonlocal variable، وهي `nonlocal`. ونفس الكلام لو عاوز أعدل في المتغير اللي جوه outer، هروح في دالة inner وأول حاجة هعملها إني هقوله `nonlocal x` بفرض إن الـ x هو اسم المتغير.

خلي بالك بقى من حاجة: مفهوم الدالة جوه دالة ده، وإني أقدر أصلًا أمرر دالة كـ parameter لدالة تانية (**Higher Order Functions**)، بيخلينا نعمل حاجات متطورة أوي، وده هنشوفه في البوستات الجاية عن الـ closures والـ decorators.

</div>
