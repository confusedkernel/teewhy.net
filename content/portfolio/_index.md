---
title: 'Portfolio'
# cascade:
#     type: blog
toc: false
description: "Some of my tech-related works."
draft: false
layout: wide
---

<div class="mt-4"></div>

<p class="mb-12 text-center text-lg text-gray-500 dark:text-gray-400">
    My tech-related projects.
</p>

<div class="mb-6"></div>

<!-- card screenshot size: 125*35 -->

{{< hextra/feature-grid >}}
  {{< hextra/feature-card
    title="Discord Music Bot"
    subtitle="Java | 2022"
    link="https://github.com/nottyl/EarwormsBot"
    image="/images/port/earworm.png"
    imageClass="dark:opacity-90"
    class="aspect-auto md:aspect-[1.1/1] max-md:min-h-[340px]"
    style="background: radial-gradient(ellipse at 50% 80%,rgba(90,125,147,0.75),hsla(0,0%,100%,0));"
  >}}
  {{< hextra/feature-card
    title="Catan in TUI"
    subtitle="C, Ncurses | 2023"
    link="https://github.com/nottyl/Catan"
    image="/images/port/catan-dark.png"
    imageClass="dark:opacity-90"
    class="aspect-auto md:aspect-[1.1/1] max-md:min-h-[340px]"
    style="background: radial-gradient(ellipse at 50% 80%,rgba(90,125,147,0.75),hsla(0,0%,100%,0));"
  >}}
{{< /hextra/feature-grid >}}
