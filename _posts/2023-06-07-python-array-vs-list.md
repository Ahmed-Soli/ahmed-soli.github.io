---
layout: post
title: "Python: the difference between an Array and a List"
date: 2023-06-07
categories: [python, data-structures]
tags: [python, list, array, data-structures, interview, big-o]
description: "A common Python interview question explained in Arabic: how a list is built on top of an array, and what that means for time complexity."
image:
  path: /assets/images/posts/python/cover.jpg
  alt: Python array vs list
---

*This post is in Egyptian Arabic, as I first wrote it on LinkedIn.*

<div dir="rtl" class="rtl-post" markdown="1">

هتكلم النهارده عن حاجة اتسألت فيها في انترفيو، وكنا واخدين بايثون كلغة برمجة:

**إيه الفرق ما بين الـ Array والـ List؟**

أولًا، الـ list في بايثون هي built-in data structure، يعني حاجة جاية جاهزة مع اللغة. لكن علشان تقيس كفاءة الكود بتاعك صح، محتاج تعرف الـ list دي مبنية وشغالة إزاي، خصوصًا إن الـ list هي أكتر حاجة أي مبرمج بايثون بيستخدمها، وفيه ناس كتير فاكرة إن الـ list هي هي الـ array، وده مش صح.

خلينا نبدأ من الأول، وده هياخدنا للـ array:

> an array has fixed size, stores the same data type and is a consecutive data structure with set, get operation support to its elements

## الـ Array

الـ array عبارة عن كونتينر أو بوكس، لكن له خصائص محددة جدًا:

- له **حجم ثابت**، يعني مش هعرف أضيف عنصر جديد ولا أمسح عنصر.
- مقدرش أحط فيه غير حاجات من **نفس النوع**، يعني معرفش أحط Text مع integer مثلًا.
- مقدرش أعمل عليه غير عمليتين محددتين: أغير قيمة عنصر، أو أقرا قيمة عنصر.

طيب إيه فايدة الكلام ده طالما الدنيا محكومة أوي كده؟ وإيه معنى كلمة consecutive؟

### المميزات

1. **Random memory access:** كل عنصر بيتحفظ في الذاكرة وله index بيخليني أوصل لقيمته بسهولة.
2. **Efficient memory utilization:** طريقة حفظ العناصر إنها consecutive، يعني uninterrupted، كأنها single block ورا بعض، وده بيخلي الدنيا أكتر كفاءة.
3. **Iteration:** بما إن الـ array فيها شوية حاجات من نفس النوع، أقدر أعمل loop عليها بسهولة.
4. **Parameter passing:** الـ array بتدعم إني أعديها كـ argument لأي function.

### العيوب

1. الحجم ثابت.
2. مقدرش أعمل عمليات زي append و remove و pop و push.
3. محكومة بنوع واحد من الداتا.

## الـ List

من هنا اخترعوا الـ list علشان تحل العيوب دي. نقدر نقول إن الـ list مبنية على الـ array، واخدة مميزاتها، ومتصلح فيها عيوب الـ array:

- بتدعم **dynamic size**، يعني أبدأها فاضية وأضيف عليها بعدين.
- أقدر أعمل عمليات زي append و remove و pop و push.
- أقدر أقرا قيم العناصر عن طريق الـ index زي الـ array.

## الـ Time Complexity

العمليات الخاصة بالـ array كلها O(1)، لأنها قراءة لعنصر واحد أو تغيير قيمة عنصر واحد.

أما في الـ list:

| العملية | Time complexity |
|---|---|
| lookup | O(1) |
| pop | O(1) |
| insert | O(n) |
| search | O(n) |
| delete | O(n) |

</div>
