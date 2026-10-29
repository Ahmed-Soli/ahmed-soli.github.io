---
layout: post
title: "Python's map function and higher-order functions"
date: 2022-12-21
categories: [python, deep-dive]
tags: [python, higher-order-functions, map, lambda, deep-dive-with-ahmed]
description: "My first Deep Dive with Ahmed post, in Arabic: what a higher-order function is, and how map replaces index-based loops over several lists."
image:
  path: /assets/images/posts/python-threads/map.jpg
  alt: Python code examples for the map function
---

*This post is in Egyptian Arabic, as I first wrote it on LinkedIn. It is the first post in my "Deep Dive with Ahmed" series. Next: [filter]({% post_url 2022-12-25-python-filter-function %}).*

<div dir="rtl" class="rtl-post" markdown="1">

ده أول بوست ليا أتكلم عن حاجة أنا بتعلمها: **Python map function**.

## الأول: الـ Higher Order Functions

قبل ما نعرف إيه قصة الـ map function لازم أعرف الأول مصطلح مهم جدًا، وهو **higher order functions**. وترجمته الدوال ذات الترتيب الأعلى، أو بالبلدي كده الدوال العليا، أو خلينا نسميها "الدوال الفخمة".

إيه بقى تعريف الدوال الفخمة دي:

> a higher order function => is a function that takes a function as a parameter and/or returns a function as its return value

بيقولك الدوال الفخمة دي هي حاجة من اتنين، أو الاتنين مجتمعين مع بعض:

1. إما بتاخد دالة تانية كـ parameter، يعني وإنت بتنادي على الدالة الفخمة، بدل ما تحط أي variable عادي، لا، بتحط فانكشن.
2. إنها تكون بترجعلك دالة تانية.

> Why do we use higher order functions? Because we want to be able to reuse our code over and over again on different parameters (functions that the code calls), and to simplify the structure/organization/readability of our program by abstracting the implementation of a potentially complicated algorithm away from its use.
>
> … the case for higher order functions is identical to the case for functions themselves!

بيقولك بقى إن الدوال الفخمة دي كتير أوي، ومن فوايدها إنها بتخفي عنك شوية حاجات إنت محتاج تكون فاهمها بس مش بالضرورة تعيد كتابتها، وفيه مثال لدالة filter هيوضح الكلام ده أكتر.

## الـ map function

خدنا لمحة عن الدوال الفخمة، نرجع بقى لدالة الـ map.

خلينا الأول نفترض إن عندي 2 lists وعاوز أعمل عملية جمع عليهم، بحيث الناتج يكون مجموع الأرقام اللي في الاتنين. يعني عندي `lst_1 = [1,2,3]` وعندي `lst_2 = [10,20,30]` وعاوز الناتج يكون `[11, 22, 33]`.

في العادي كنت بعمل لوب مثلًا على لست منهم وأجيب العنصر التاني بالإندكس، حاجة زي أول صورة مثلًا (فيه حلول كتير بس ده كمثال يعني).

ولكن لو فرضنا إن اللست الأولى كان عددها مثلًا 4 والتانية 3، ساعتها هيحصل:

```text
IndexError: list index out of range
```

جت بقى الدالة الفخمة وقالتلك: الحل عندي، إنت ليه تقعد تعمل كل ده؟ أنا هعملك دالة اسمها `map`، وبدل يا ابن الحلال ما بتقعد تعمل لوب على كذا لست بالإندكس، لا، أنا هخليك تستعمل حاجة إنت بتحبها أوي وهي الفانكشن. يعني إيه؟ يعني تعملي فانكشن بتاخد parameters يساوي عدد الـ iterables (اللي هما اللست اللي عندي يعني).

بردو مش فاهم؟ هبسطهالك: بدل ما بتعمل لوب على لست بإيدك، الـ map function هتقوم بالموضوع ده.

ومش بس كده! ده كمان في حالة إن اللست الأولى كان عددها مثلًا 4 والتانية 3، ساعتها اللوب هتنتهي لأنها بتختار أقل لست فيها عدد عناصر الأول ثم بتعمل اللوب عليها، يعني كده مش هيحصل Exception.

وإيه كمان؟ بيقولك طالما الدالة الفخمة اللي اسمها `map` دي بتقبل دوال تانية، يبقى ده معناه إن ممكن أستعمل **lambda expression**، وفي سطر واحد أوفر على نفسي سطور كتير كانت هتتكتب، وكمان مقروء وأفخم.

زي ما قلت، دي أول مرة أكتب بوست بشرح فيه حاجة، فلو حد لقى أي غلط سواء في الفهم أو في التعبير، يا ريت يصححلي لأني ناوي أستمر بإذن الله.

هسيبلكم الأمثلة اللي كنت بتكلم عنها، واللي عنده سؤال يكتبه.

## الكود

<bdi>[01-maping_func.py](https://github.com/Ahmed-Soli/deep_dive_with_ahmed/blob/main/01-maping_func.py)</bdi> في الـ repo بتاع السلسلة.

</div>
