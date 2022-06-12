---
layout: post
title: 旅行记录 
description: 记录到过的地方以及停留的天数
date: 2022-06-12
tags: [2022, tech, python, pyecharts, life, travel]
---

<iframe src="/files/2022/06/TravelMarks/travelMarks.html" width="920" height="800" frameborder="0" allowfullscreen style="border: solid 2px 000"></iframe>

<div style='display: flex; justify-content: flex-end'>
<div> 项目地址：</div>
<div> <img src="/images/2022/06/TravelMarks/GitHub-Mark-120px-plus.png" width='30' style="border:solid 1px 000;margin:2px;"/> </div>
<div> <a href="https://github.com/Ethel-yueying-sun/TravelMarks"> TravelMarks </a> </div>
</div>
---
<!-- TOC -->

- [前言](#前言)
- [用 PyEcharts 画中国地图 - 持续更新中](#用-pyecharts-画中国地图---持续更新中)
    - [1. 做出基本地图](#1-做出基本地图)

<!-- /TOC -->

---

## 前言

这张地图用来记录SYY到过的城市，数据为当前城市停留的天数

## 用 PyEcharts 画中国地图 - 持续更新中

### 1. 做出基本地图

- 数据格式：（地点，停留天数）
```
data_counts = [
    # 河南省
    ('洛阳', 6752),
    ('开封', 1095),
    ('郑州', 100)
]
```

- 画出基本地图
```
c = (
    Map()
    # add(图标名称，数据源，地图源)
    # 地图源可以根据需求选择精确到省或市，这里精确到市
    .add('TravelMarks', data_counts, 'china-cities')
    .set_global_opts(
        visualmap_opts=opts.VisualMapOpts(
            max_=_max,
            is_piecewise=True # 数据是否分段，这里分段，显示为地图左下角分段标签
            )
    )
    # 是否显示各地名称，这里不显示
    .set_series_opts(label_opts=opts.LabelOpts(is_show=False))
    .render('travelMarks.html')
)
```
