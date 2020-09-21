---
layout: post
title:  "jupyter notebook test"
subtitle: "jupyter notebook test"
categories: development
tags: web
comments: true
--- 
- Date : 2020.9.13
- Author : Jiwon Jang

- folium을 활용하여 OSM기반 지도 표출
- 어떤 건물을 표출해야하는지 고민

__[표출 정보]__  
__(space)__  
- tile로 작업
- 도로망,상점 정보,연구지역 (단계 구분도)
- 이태원역 : 37.5342356,126.9934594

- layer 1 : OSM
- layer 2 : Building point
- layer 3 : Road shapefile(geojson)
- layer 4 : Instagram Buzz / heatmap - choropleth
- layer 5 : grid
- layer 6 : Simulation result / Timestamp geojson / heatmap - choropleth


__(Time)__
- timestamp
- 전체 지역의 추세 표출

__[reference]__
- Interactive Choropleth Map of Washington DC using Folium and Python : https://medium.com/@lindsayrallen1/interactive-choropleth-map-of-washington-dc-using-folium-and-python-2794708514d5
- grid : https://www.jpytr.com/post/analysinggeographicdatawithfolium/
- folium plugin : https://dailyheumsi.tistory.com/85


```python
import pickle
```


```python
# # # load
with open('AddressCoordinates.pickle', 'rb') as f:
    Addresses = pickle.load(f)
```


```python

```
