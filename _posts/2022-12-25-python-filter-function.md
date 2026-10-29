---
layout: post
title: "Python's filter function (and how it differs from map)"
date: 2022-12-25
categories: [python, deep-dive]
tags: [python, higher-order-functions, filter, lambda, deep-dive-with-ahmed]
description: "Deep Dive with Ahmed, in Arabic: how filter works, why use it over a loop, the None trick, and the difference between map and filter."
image:
  path: /assets/images/posts/python-threads/filter-cover.jpg
  alt: "filter(): [0, 1, 2, 3, 4] keeps only the even numbers [0, 2, 4]"
---

*This post is in Egyptian Arabic, as I first wrote it on LinkedIn. It follows [map]({% post_url 2022-12-21-python-map-function-and-higher-order-functions %}) and comes before [reduce]({% post_url 2022-12-26-python-reduce-function %}).*

<div dir="rtl" class="rtl-post" markdown="1">

ده تاني بوست ليا أتكلم عن حاجة أنا بتعلمها: **Python filter function**.

اتكلمنا في [البوست ده]({% post_url 2022-12-21-python-map-function-and-higher-order-functions %}) عن الدوال الفخمة وخدنا مثال عليها وهي دالة `map`. النهارده هنتكلم عن دالة فخمة جديدة وهي دالة `filter`.

من اسمها كده، الدالة اللذيذة دي بتفلتر العناصر بتاعتك وبترجعلك العناصر اللي ينطبق عليها شرط معين.

> Filter() is a built-in function in Python. The filter function can be applied to an iterable such as a list or a dictionary and create a new iterator. This new iterator can filter out certain specific elements based on the condition that you provide very efficiently

## مثال

لو أنا عندي لست `lst = [0,1,2,3,4]` وعاوز مثلًا أعرف الأرقام الزوجية، الطبيعي هعمل لوب، وجوه اللوب بتاعتي هحط if condition بيشيك إن الرقم اللي عليه الدور في اللوب باقي القسمة على 2 يساوي صفر. لو الشرط اتحقق هروح أضيفه في لست أنا كريتها قبل ما أبدأ اللوب، وهكذا لحد ما اللست تخلص، ثم هطبع اللست الجديدة.

طيب ما الدنيا حلوة أهو، أنا ليا أشغل دماغي بالدالة الفخمة اللي اسمها فلتر دي؟

- **أولًا:** لأن اللي عملته في 5 أو 6 سطور أقدر أختزله في سطرين، أو سطر واحد كمان لو استعملت lambda expression. وبالتالي الكود بتاعي يكون أنضف.
- **ثانيًا:** لأنها بالفعل built-in في اللغة، وبالتالي صنّاع اللغة نفسهم شالوا عنك كل اللوجيك ده، بشرط تكون فاهمها وعارف أصلها وبتعمل إيه وبديلها بالكود العادي.

## حاجة تانية لطيفة: None

ممكن بدل ما تحط دالة وإنت بتنادي على filter تحط `None`، وساعتها `None` هتشيلك أي حاجة لو عملتلها evaluation تدي `False`، زي مثلًا لست فاضية أو رقم 0 أو `False` نفسها، وترجعلك الليست اللي كل اللي فيها يـ evaluate لـ `True`.

مثلًا الليست دي:

</div>

```python
lst = [0, 1, 2, 3, 4, False, [], {}]
```

<div dir="rtl" class="rtl-post" markdown="1">

لو هطبق عليها دالة filter كالتالي:

</div>

```python
print(list(filter(None, lst)))
```

<div dir="rtl" class="rtl-post" markdown="1">

الناتج هيكون:

</div>

```python
[1, 2, 3, 4]
```

<div dir="rtl" class="rtl-post" markdown="1">

## الفرق بين map و filter

حاجة أخيرة عشان نربط الكلام ببعضه: إيه الفرق بين `map` و `filter`؟ حاول تجاوب قبل ما تشوف الإجابة.

- `map`: بتاخد دالة ليها أكتر من parameter ويكون عدد الـ parameters يساوي عدد الـ iterables.
- `filter`: بتاخد دالة واحدة ليها parameter واحد، وبتاخد iterable واحد فقط.

---

- `map`: بتنفذ الدالة (أو الشرط يعني) على كل العناصر وبترجع iterable له نفس عدد العناصر.
- `filter`: بتنفذ الدالة (أو الشرط يعني) على كل العناصر، ولكن بترجع iterable فيه العناصر اللي ينطبق عليهم الشرط فقط.

## الكود

![Python code examples for the filter function](/assets/images/posts/python-threads/filter.jpg)

<bdi>[02-filter_func.py](https://github.com/Ahmed-Soli/deep_dive_with_ahmed/blob/main/02-filter_func.py)</bdi> في الـ repo بتاع السلسلة.

</div>
