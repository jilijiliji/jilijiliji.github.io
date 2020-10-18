---
title: Can AI agent find the best place to visit in the commercial district? - Deep Reinforcement learning approach
date: 2020-10-17 17:00:00 -0400
classes: wide
layout: single
categories: Itaewon
---
 
# 지도 소개 (Introduction to Itaewon Instagram contents map)
장소를 방문하기에 앞서 우리는 일상적으로 소셜 미디어의 후기를 보고 식당 및 카페를 방문한다. 검색을 통해 가장 높은 만족감을 줄 것으로 기대되는 가게를 방문한다.
하지만 지역의 몇몇 식당이름을 가지고 검색한 결과를 이용하여 해당 지역에 방문하는 것이 정말로 최고의 선택일까. 만약 내가 찾은 가게가 한때 유명했는 가게이거나 충분히 검색하지 못한 경우 지역에 가장 유명한 가게는 방문하지 못할 것이다. 방문하기 위한 최고의 장소를 찾기 위햇 인터넷에서 더 많은 시간을 사용하는 것보다, 상권 전체의 온라인 유명도 분포를 알 수 있다면 이 같은 어려움을 해결할 수 있을 것으로 생각된다.

본 지도는 대한민국 서울특별시의 대표적이 상권인 용산구 이태원역 일대에 형성되어 있는 이태원 상권의 인스타그램 유명도를 표출하고([Map 1](https://jilijiliji.github.io/ITW_baseMap_20201011.html), [Map 2](https://jilijiliji.github.io/ITW_timeInstagramCummulative.html)), 심층 강화학습을 적용하 지역별 유명도를 기반으로 지역을 방문하는 에이전트를 학습시켰다([Map 3](https://jilijiliji.github.io/SimulationResult_20201012.html)). 그 결과 처음에는 무작위로 행동하는 에이전트가 주어진 데이터를 기반으로 가장 유명한 지역을 방문할 수 있는 행동 정책을 학습하는 것을 확인할 수 있다. 지도를 만들기 위해 20대의 컴퓨터를 병렬처리하여 데이터를 수집하였고, 이태원 지역에 위치한 가게 이름을 검색어로 활용하여 인스타그램의 자료를 수집하여 데이터베이스를 구축하였다. 수집된 자료는 전처리 과정을 통해 해당 가게를 명시적으로 지칭할 수 있는 콘텐츠만 분류하였다. 이와 같으 과정을 통해 2013년 1월 1일 부터 2019년 8월 19일 사이(대략 2167일)에 발생한 인스타그램 콘텐츠를 데이터베이스에 저장하였다. 

[[Map 1]](https://jilijiliji.github.io/ITW_baseMap_20201011.html)는 데이터를 수집한 마지막 시기인 2019년 8월 19일에 발생한 인스타그램 콘텐츠를 표출하였다. 특정 시점의 자료만 이용하는 경우 상권의 전반적인 온라인 유명도의 추세를 확인할 수 없기 때문에 이태원 상권의 인스타그램 콘텐츠의 시공간 분포(spatiotemporal)를 [[Map 2]](https://jilijiliji.github.io/ITW_timeInstagramCummulative.html)에 표출하였다. 인스타그램이 한국에 출시된 2013년에는 이태원 상권에 거의 콘텐츠가 생성되지 않지만, 2019년 8월로 갈 수록 이태원 상권 전반에 콘텐츠가 형성되는 것을 확인할 수 있다. 특히 콘텐츠의 분포를 통해서 특정 시점의 활성된 지역을 파악할 수 있다.
마지막으로 수집한 자료를 활용하여 상권의 유명도를 기술하는 것에서 뿐만 아니라, 인스타그램 콘텐츠는 유동인구에 유의미한 영향을 주는 시공간 자료이기 때문에 데이터를 활용하여 의사결정을 도울 수 있는 인공지능을 제작하였다.([Jang, et.al, 2020](https://github.com/jilijiliji/jilijiliji.github.io/blob/master/spatialpanel_instagtram_0928.pdf)).
시간에 따라 공간적으로 이질적으로 분포하는 데이터를 환경으로 구성하였고, 심층강화학습을 사용하여 환경과 상호작용하는 에이전트를 학습시켰다. 학습결과 가장 유명한 지역을 연속적으로 방문하는 최적 정책을 학습한 에이전트를 학습시킬 수 있었다[[Map 3]](https://jilijiliji.github.io/SimulationResult_20201012.html).

# [Map 1](https://jilijiliji.github.io/ITW_baseMap_20201011.html) : Itaewon Instagram contents map(Static Map)

<center><img src="/assets/basemapimage.jpg" width="600" height="500"></center>
<center>Itaewon Instagram contents map 1 example</center>
* Colors range from blue to red 
* Blue color represents the most lowest frequency, on the other hand red color represents the most highest frequency
<br/>

[[Map 1]](https://jilijiliji.github.io/ITW_baseMap_20201011.html)은 인스타그램 자료, 가게 위치, 연구지역, 시뮬레이션 범위 자료를 지도에 표출하였다.
* HeatMap(Instagram Buzz) layer : 인스타그램 자료는 HeatMap(Instagram Buzz) layer 에 표출되어 있다. 상권 내부의 인스타그램 콘텐츠의 상대적인 분포를 보기 위해 HeatMap으로 표출 하였다. 

* BUILDING(341) layer : 이태원 상권의 가게 위치는 BUILDING(341) layer에서 확인할 수 있다. 총 341개의 가게가 연구지역에 표출되어 있다. 가게가 위치한 좌표에 마커가 표시되어 있으며, 마커를 클릭하면 데이터 수집기간 동안 ‘누적된’ 인스타그램 콘텐츠 수를 확인 할 수 있다.

* Simulation Environment(Grid) Layer : Simulation Environment(Grid) Layer는 심층강화학습을 적용한 환경을 나타보여준다. 이태원역을 중심으로  1000㎡의 범위를 시뮬레이션 환경으로 한정하였고 1000㎡의 환경은 10㎡의 그리드 10,000개로 이루어져 있다.

* Research Area layer : Research Area layer는 이태원 상권이 형성되어 있는 행정동(용산동2가, 이태원동, 한남동)을 확인할 수 있다.

# [Map 2](https://jilijiliji.github.io/ITW_timeInstagramCummulative.html) : Itaewon Instagram contents map(Dynamic Map)

<center><img src="/assets/map2Example.gif" width="600" height="500"></center>
<center>Map 2 example</center>
* Colors range from blue to red 
* Blue color represents the most lowest frequency, on the other hand red color represents the most highest frequency
<br/>

[[Map 2]](https://jilijiliji.github.io/ITW_timeInstagramCummulative.html)는 2013년 1월 1일 부터 2019년 8월 19일 사이(대략 2167일)에 발생한 인스타그램 콘텐츠를 시간순으로 표출하였다. 시간 순으로 이태원 상권 지역의 활성화된 지역을 파악하기 위해 콘텐츠의 지역별 누적합을 표출하였다. 콘텐츠의 분포를 통해서 특정 시점의 활성된 지역을 파악할 수 있다.

# [Map 3](https://jilijiliji.github.io/SimulationResult_20201012.html) : Deep Reinforcement learning simulation result(dynamic map)

<center><img src="/assets/images//reinforcementlearning.jpg" width="500" height="500"></center>
<center>Reinforcement learning process</center>
<br/>
강화학습 에이전트가 학습을 진행하는 과정은 위의 이미지와 같다. 에이전트는 environment의 state에 따라서 action을 선택하고, action에 기반하여 환경에서 reward를 받는다. 
- 학습과정 서술

<center><img src="/assets/images/grid.jpg" width="300" height="300"/> <img src="/assets/gridSimulation.gif" width="300" height="300"></center>
<center>Left : Map 1 - Simulation Environment(Grid)</center>
<center>Right : Deep Reinforcement Learning Simulation in Grid World</center>
<center>(Right image corresponds to the same coordinates on the left image)</center>
* circle : Agent who is interacting with the environment
* Red grid : Red grids represent the place where shops are located
<br/>

[[Map 3]](https://jilijiliji.github.io/SimulationResult_20201012.html)은 심층강화학습을 이용하여 에이전트를 학습시키는 과정을 표출하였다. 심층강화학습 시뮬레이션에서 에이전트는 인스타그램 콘텐츠가 많은 지역을 방문한 경우 높은 보상을 받으며, 그렇지 않은 경우 보상을 받지 못하게 된다. 학습을 통해 에이전트가 이태원 상권에서 가장 유명한 지역을 방문하는 최적 정책을 도출한다. [Map 1](https://jilijiliji.github.io/ITW_baseMap_20201011.html)의 ‘Simulation Environment(Grid) Layer’에서 확인할 수 있듯, 실제 공간범위에 대응할 수 있는 그리드 환경을 구성하였고, 각각의 그리드의 공간범위에 해당하는 지역에서 발생하는 인스타그램 콘텐츠를 각 그리드에 집계하였다.

<center><img src="/assets/simulationResult.gif" width="600" height="500"></center>
<center>Map 3 - Deep Reinforcement Learning Simulation in Real World</center>
* Colors range from blue to red 
* Blue color represents the most lowest frequency, on the other hand red color represents the most highest frequency
* The most visited areas become red and relatively the least visited areas become blue
<br/>

2018년 8월 ~ 2019년 8월 사이의 자료를 활용하여 에이전트를 학습한 결과는 [Map 3](https://jilijiliji.github.io/SimulationResult_20201012.html)과 같다. 시뮬레이션 에피소드 진행에 따른 에이전트의 지역 방문 빈도를 확인할 수 있다. 에이전트가 많이 방문한 지역은 Heatmap에서 붉은 색상을 보이고 그렇지 않은 경우 파란 색상을 보인다. 에이전트는 학습 초기에는 모든 지역을 무작위로 방문하지만 학습이 진행됨에 따라 온라인에서 유명한 지역을 방문하는 정책을 학습할 수 있게 되며,  결과적으로 가장 높은 보상을 얻을 수 있는 지역으로 수렴하는 것을 확인할 수 있다.

Itaewon Instagram Contents Map의 결과를 기반으로 상권을 방문하는 예비 방문객은 상권 내부의 유명한 가게가 군집되어 있는 지역을 방문하 수 있는 최적 계획을 기획할 수 있다. 또한 지역 상권에서 사업을 운영하는 소상공인에게도 유용한 정보를 줄 수 있을 것을 기대된다. 특정 시점의 상권이 활성화된 정도를 파악할 수 있으며, 학습된 에이전트를 활용하여 향후 인구유동이 많은 지역을 예측할 수도 있다. 이와 같은 정보를 활용하여 가게 계약 연장 및 신규 점포 입지 선정 등의 의사결정에 도움을 줄 수 있을 것으로 기대된다. 더 나아가 향후 연구에서 임대료 상등 등으로 인한 가게의 소멸과정을 학습모델에 추가하여 젠트리피케이션을 예측하고 대응할 수 있는 GeoAI로 발전시킬 수 있는 가능성을 기대한다.

* This post is based on the working paper below
* (in progress) Jang, J., & Choi, J. (2020). Predicting pedestrian behaviors in Itaewon commercial district using user generated contents : deep reinforcement learning approach.