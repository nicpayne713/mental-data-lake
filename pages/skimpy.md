---
templateKey: til
tags: ['python']
title: Skimpy
date: 2022-03-23T00:00:00
status: draft
cover: "/static/skimpy.png"

---

## EDA

I work with data a lot, but the nature of my job isn't to dive super deep into a small amount of datasets,
I'm often jumping between several projects every day and need to just get a super quick glance at some tables to get a high level view.

When I'm doing more interactive exploration I've graduated from Jupyter cells with `df_N.head()` to using an amazing tool called [visidata](https://www.visidata.org/)

However, Visidata is a terminal based application and I'm often in an iPython console... so is there a way to move even faster for my super quick summary views?

__yes!__ 

## Skimpy

First thing to do is `pip install skimpy` and then it's as easy to get some summary stats with `skimpy <data>`

```bash

sandbox  🌱 main 🗑️  ×3🛤️  ×3via 🐍 v3.8.11 (sandbox)  took 3m33s
❯ skimpy cars.csv
╭───────────────────────────────────────────────────────────────────── skimpy summary ─────────────────────────────────────────────────────────────────────╮
│          Data Summary                Data Types                                                                                                          │
│ ┏━━━━━━━━━━━━━━━━━━━┳━━━━━━━━┓ ┏━━━━━━━━━━━━━┳━━━━━━━┓                                                                                                   │
│ ┃ dataframe         ┃ Values ┃ ┃ Column Type ┃ Count ┃                                                                                                   │
│ ┡━━━━━━━━━━━━━━━━━━━╇━━━━━━━━┩ ┡━━━━━━━━━━━━━╇━━━━━━━┩                                                                                                   │
│ │ Number of rows    │ 32     │ │ int64       │ 6     │                                                                                                   │
│ │ Number of columns │ 12     │ │ float64     │ 5     │                                                                                                   │
│ └───────────────────┴────────┘ │ object      │ 1     │                                                                                                   │
│                                └─────────────┴───────┘                                                                                                   │
│                                                                         number                                                                           │
│ ┏━━━━━━━━━━━━┳━━━━━━━━━━━━━━━━━━┳━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━┳━━━━━━━━━━━━┳━━━━━━━━━━━━┳━━━━━━━━━━┳━━━━━━━━━━┳━━━━━━━━━━┳━━━━━━━━━━━━┳━━━━━━━━━━━━━━┓  │
│ ┃            ┃ missing          ┃ complete rate                ┃ mean       ┃ sd         ┃ p0       ┃ p25      ┃ p75      ┃ p100       ┃ hist         ┃  │
│ ┡━━━━━━━━━━━━╇━━━━━━━━━━━━━━━━━━╇━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━╇━━━━━━━━━━━━╇━━━━━━━━━━━━╇━━━━━━━━━━╇━━━━━━━━━━╇━━━━━━━━━━╇━━━━━━━━━━━━╇━━━━━━━━━━━━━━┩  │
│ │ mpg        │                0 │                            1 │         20 │          6 │       10 │       15 │       23 │         34 │    ▃█▇▃▁▃    │  │
│ │ cyl        │                0 │                            1 │        6.2 │        1.8 │        4 │        4 │        8 │          8 │    ▆  ▄ █    │  │
│ │ disp       │                0 │                            1 │        230 │        120 │       71 │      120 │      330 │        470 │    █▆▂▅▄▃    │  │
│ │ hp         │                0 │                            1 │        150 │         69 │       52 │       96 │      180 │        340 │    █▇▇▃▃▁    │  │
│ │ drat       │                0 │                            1 │        3.6 │       0.53 │      2.8 │      3.1 │      3.9 │        4.9 │    █▄▅█▃▁    │  │
│ │ wt         │                0 │                            1 │        3.2 │       0.98 │      1.5 │      2.6 │      3.6 │        5.4 │    ▄▅█▆ ▂    │  │
│ │ qsec       │                0 │                            1 │         18 │        1.8 │       14 │       17 │       19 │         23 │    ▄▅█▅▁▁    │  │
│ │ vs         │                0 │                            1 │       0.44 │        0.5 │        0 │        0 │        1 │          1 │    █    ▆    │  │
│ │ am         │                0 │                            1 │       0.41 │        0.5 │        0 │        0 │        1 │          1 │    █    ▅    │  │
│ │ gear       │                0 │                            1 │        3.7 │       0.74 │        3 │        3 │        4 │          5 │    █  ▆ ▃    │  │
│ │ carb       │                0 │                            1 │        2.8 │        1.6 │        1 │        2 │        4 │          8 │     █▁▅      │  │
│ └────────────┴──────────────────┴──────────────────────────────┴────────────┴────────────┴──────────┴──────────┴──────────┴────────────┴──────────────┘  │
╰────────────────────────────────────────────────────────────────────────── End ───────────────────────────────────────────────────────────────────────────╯


```

This is super nice for seeing missing values in particular as well as the distribution shape of the data.

## iPython

But wait... I just said I'm normally in an iPython session but that was called from zsh.. If I'm hoping back into zsh I might as well use visidata to have more powerful exploration at my fingertips.
So... can I see this table quickly without breaking my iPython workflow?

__Of course you can with magic!__


```python 
sandbox  🌱 main 🗑️  ×3🛤️  ×3via 🐍 v3.8.11 (sandbox)  took 1m6s
❯ ipython

sandbox ↪ main v3.8.11 ipython
❯ %run -m skimpy cars.csv
╭───────────────────────────────────────────────────────────────────── skimpy summary ─────────────────────────────────────────────────────────────────────╮
│          Data Summary                Data Types                                                                                                          │
│ ┏━━━━━━━━━━━━━━━━━━━┳━━━━━━━━┓ ┏━━━━━━━━━━━━━┳━━━━━━━┓                                                                                                   │
│ ┃ dataframe         ┃ Values ┃ ┃ Column Type ┃ Count ┃                                                                                                   │
│ ┡━━━━━━━━━━━━━━━━━━━╇━━━━━━━━┩ ┡━━━━━━━━━━━━━╇━━━━━━━┩                                                                                                   │
│ │ Number of rows    │ 32     │ │ int64       │ 6     │                                                                                                   │
│ │ Number of columns │ 12     │ │ float64     │ 5     │                                                                                                   │
│ └───────────────────┴────────┘ │ object      │ 1     │                                                                                                   │
│                                └─────────────┴───────┘                                                                                                   │
│                                                                         number                                                                           │
│ ┏━━━━━━━━━━━━┳━━━━━━━━━━━━━━━━━━┳━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━┳━━━━━━━━━━━━┳━━━━━━━━━━━━┳━━━━━━━━━━┳━━━━━━━━━━┳━━━━━━━━━━┳━━━━━━━━━━━━┳━━━━━━━━━━━━━━┓  │
│ ┃            ┃ missing          ┃ complete rate                ┃ mean       ┃ sd         ┃ p0       ┃ p25      ┃ p75      ┃ p100       ┃ hist         ┃  │
│ ┡━━━━━━━━━━━━╇━━━━━━━━━━━━━━━━━━╇━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━╇━━━━━━━━━━━━╇━━━━━━━━━━━━╇━━━━━━━━━━╇━━━━━━━━━━╇━━━━━━━━━━╇━━━━━━━━━━━━╇━━━━━━━━━━━━━━┩  │
│ │ mpg        │                0 │                            1 │         20 │          6 │       10 │       15 │       23 │         34 │    ▃█▇▃▁▃    │  │
│ │ cyl        │                0 │                            1 │        6.2 │        1.8 │        4 │        4 │        8 │          8 │    ▆  ▄ █    │  │
│ │ disp       │                0 │                            1 │        230 │        120 │       71 │      120 │      330 │        470 │    █▆▂▅▄▃    │  │
│ │ hp         │                0 │                            1 │        150 │         69 │       52 │       96 │      180 │        340 │    █▇▇▃▃▁    │  │
│ │ drat       │                0 │                            1 │        3.6 │       0.53 │      2.8 │      3.1 │      3.9 │        4.9 │    █▄▅█▃▁    │  │
│ │ wt         │                0 │                            1 │        3.2 │       0.98 │      1.5 │      2.6 │      3.6 │        5.4 │    ▄▅█▆ ▂    │  │
│ │ qsec       │                0 │                            1 │         18 │        1.8 │       14 │       17 │       19 │         23 │    ▄▅█▅▁▁    │  │
│ │ vs         │                0 │                            1 │       0.44 │        0.5 │        0 │        0 │        1 │          1 │    █    ▆    │  │
│ │ am         │                0 │                            1 │       0.41 │        0.5 │        0 │        0 │        1 │          1 │    █    ▅    │  │
│ │ gear       │                0 │                            1 │        3.7 │       0.74 │        3 │        3 │        4 │          5 │    █  ▆ ▃    │  │
│ │ carb       │                0 │                            1 │        2.8 │        1.6 │        1 │        2 │        4 │          8 │     █▁▅      │  │
│ └────────────┴──────────────────┴──────────────────────────────┴────────────┴────────────┴──────────┴──────────┴──────────┴────────────┴──────────────┘  │
╰────────────────────────────────────────────────────────────────────────── End ───────────────────────────────────────────────────────────────────────────╯


```
