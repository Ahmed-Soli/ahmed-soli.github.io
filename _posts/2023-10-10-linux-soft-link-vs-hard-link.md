---
layout: post
title: "Linux interview question: soft link vs hard link"
date: 2023-10-10
categories: [linux]
tags: [linux, softlink, hardlink, inode, system-administration, interview]
description: "The difference between a soft link and a hard link in Linux, explained in Arabic with inodes, examples and the ln command."
image:
  path: /assets/images/posts/links/cover.jpg
  alt: Soft link vs hard link diagram (Tecadmin.net)
---

*This post is in Egyptian Arabic, as I first wrote it on LinkedIn. Diagram credit: Tecadmin.net.*

<div dir="rtl" class="rtl-post" markdown="1">

سؤال انترفيو في اللينكس ومهم جدًا تكون عارفه وفاهمه:

**إيه الفرق بين الـ soft link و hard link؟**

بص يا سيدي، علشان تفهم الحتة دي محتاج الأول تفهم يعني إيه **Inode** وإزاي الداتا بتتكتب على الهارد، لكن دي هتكلم فيها في بوست تاني.

## الـ Soft Link

خلينا نتكلم الأول عن الـ soft link. ده تقدر تفكر فيه كأنه shortcut لحاجة موجودة على الهارد في مكان ما أو في أي بارتشن. وأعتقد إن كتير مننا واجه الكلام ده في نظام الويندوز، وأشهر الـ shortcuts اللي بتكون موجودة على سطح المكتب بتاعك: برنامج سطبته في C، وتبص تلاقي اتعملك shortcut برا على الـ Desktop علشان يسهّل عليك إنك تفتح البرنامج ده بدل ما تروح للمكان اللي متسطب فيه وتفتحه منه.

طيب خلينا نقول إني مسحت النسخة الأصل اللي عامل منها shortcut، إيه اللي هيحصل؟ طبيعي إن الـ shortcut مش هيشتغل، وهيقولك إن الملف الأصلي اللي أنا بشاور عليه مش موجود. وحط خط تحت "بشاور عليه" دي لأن دي الزتونة.

الـ soft link في اللينكس ببساطة هو إني بعمل ملف وبقوله يشاور على اسم ملف تاني، أي كان البارتشن بتاعه، ولو مسحت الملف الأصلي بالتبعية الـ soft link مش هيشتغل.

طيب إيه فايدته بقى؟ الفوائد كتير، ومنها:

- عندي مسار طويل وعاوز أختصر الدنيا، فبعمله shortcut.
- أقدر أخلي أكتر من فولدر يشاوروا على نفس الـ soft link، زي مثلًا الـ `sr0` اللي بتشاور على مكان الـ cdrom و cd rw و dvdrom و dvdwr و blu-ray. أقدر لما أحط أي اسطوانة في الجهاز، الطبيعي إن كل نوع هيكون له مكان أفتح الاسطوانة منه، لكن باستخدام الـ soft link أنا وحّدت الكلام ده وخليت الـ `sr0` بتشاور عليهم كلهم، فأي كان نوع الاسطوانة اللي هتحطها هتتعامل مع `sr0`.
- مثال تاني: `/usr/bin/` معمولة soft link كالتالي `/bin/`.

وبالمناسبة:

- لو مسحت الـ soft link مش هيأثر على الملف الأصلي.
- لو عملت أي تعديل على الملف اللي معمول له soft link، التغيير هيتم في الملفين.

طيب أعمل الـ soft link إزاي؟ عن طريق الأمر ده، ولازم تستعمل المسار كامل:

</div>

```bash
ln -s /absolute/path/of/source_file /absolute/path/of/link
```

<div dir="rtl" class="rtl-post" markdown="1">

## الـ Hard Link

نيجي للـ hard link. ده بدل ما بشاور على اسم الملف، بشاور على الـ **Inode** بتاعه، والـ Inode تقدر تعتبره الـ data block بتاع الملف. أو بمعنى تاني: بشاور على الداتا نفسها المكتوبة على البارتشن.

كمثال: أنا اسمي أحمد، لكن بيدلعوني يقولولي يا حماده. فهل أحمد وحماده هما نفس الشخص؟ الإجابة أه، إذا ده hard link. ونقدر نقول كمان إن الـ hard link هو اسم جديد لفايل بالفعل موجود، والاتنين بيشاوروا على نفس الداتا (أو الـ Inode number).

وعلشان أنا بشاور على data block وليها رقم معين في بارتشن معين، فمينفعش أعمل hard link على بارتشن تاني، أو بمعنى أدق file system مختلف. وده كمثال، مينفعش أقول إني موجود في مصر وفي السعودية في نفس الوقت.

بالمناسبة، مينفعش أعمل hard link للـ directories.

علشان أعرض الملفات بالـ soft links والـ hard links والـ inode numbers بستعمل الأمر التالي:

</div>

```bash
ls -li
```

<div dir="rtl" class="rtl-post" markdown="1">

بعمل الـ hard link عن طريق نفس الأمر اللي فات، لكن من غير `-s`:

</div>

```bash
ln /absolute/path/of/source_file /absolute/path/of/link
```

<div dir="rtl" class="rtl-post" markdown="1">

## الفرق في الـ Inode

أحد الاختلافات بردو إن الـ soft link بياخد Inode number مختلف عن الملف اللي بيشاور عليه، لكن الـ hard link بياخد **نفس الـ Inode number** بتاع الملف الأصلي.

</div>
