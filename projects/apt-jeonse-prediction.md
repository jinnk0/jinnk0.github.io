---
title: "개인화된 Top10 영화 추천천"
permalink: /projects/top10-movie-recommendation/
layout: single
classes: wide
author_profile: false
related: true
---
<img src="/assets/images/apt-jeonse-prediction_graph1.png"
     alt="apt-jeonse-prediction_graph1"
     style="max-width: 100%; height: auto; display: block; margin: 2rem auto;" />

<!-- 버튼 링크 -->
<!-- Font Awesome 아이콘이 필요하므로 minimal-mistakes에서 이미 로딩됨 -->
<div style="display: flex; gap: 10px; margin-bottom: 2em;">

  <!-- GitHub 버튼 -->
  <a href="https://github.com/boostcampaitech7/level2-competitiveds-recsys-01" target="_blank"
     style="display: inline-flex; align-items: center; gap: 6px; padding: 6px 12px;
            background-color: #f8f9fa; color: #212529; text-decoration: none;
            font-size: 14px; border-radius: 6px; border: 1px solid #dee2e6;">
    <i class="fab fa-github"></i> GitHub
  </a>

</div>


- 기간 : 2024.09 ~ 2024.10 (3주)
- 참여 인원 : 5인

## 프로젝트 개요
#### 프로젝트 목표
MAE 점수를 최소화하는 수도권 아파트 전세가 예측 모델 개발

#### 프로젝트 배경
- 부동산 시장의 정보 비대칭성을 해소하고자 함
- 아파트 전세가는 실수요자에게 큰 영향을 줌
- 금리, 지하철, 학교, 공원 등 다양한 주변 정보를 반영한 전세가 예측 필요

#### 결과
- LightGBM, CatBoost, XGBoost 등의 트리 기반 모델과 딥러닝 모델을 실험한 결과, XGBoost가 가장 우수한 성능을 보임
- [다양한 피처를 생성](https://github.com/boostcampaitech7/level2-competitiveds-recsys-01/blob/main/code/features/README.md)하고 feature importance를 기반으로 상위 20개의 feature만 반영한 모델로 베이스라인 (MAE 7904.04) 대비 3684.9866로 약 53.4% 성능 향상
- 시드 앙상블을 통해 MAE 3477.8167로 5% 추가 개선
- 공간 가중치 행렬을 반영하여 MAE 3455.8046으로 최종 0.6% 성능 향상
<img src="/assets/images/apt-jeonse-prediction_result.png"
     alt="apt-jeonse-prediction_result"
     style="max-width: 80%; height: auto; display: block; margin: 2rem auto;" />
- 부스트캠프 내에서 진행된 경진대회 9팀 중 최종 2위 달성

## 내 역할 및 기여
 <div style="flex: 1; display: flex; align-items: center;">
    <div style="width: 100%;">
      <strong>Feature Engineering으로 모델 성능 개선</strong>
      <ul>
        <li><strong>클러스터링 기반 피처 추가</strong>
          <ul>
            <li>위도, 경도에 대해 클러스터링하여 생성된 군집 ID</li>
            <li>군집의 중심(centroid)와 샘플 간의 거리</li>
          </ul>
        </li>
        <li><strong>주변 환경 정보 기반 피처 추가</strong>
          <ul>
            <li>2km 반경 내의 공원 면적 총합</li>
            <li>2km 반경 내의 학교 개수</li>
            <li>1km 반경 내의 지하철역 개수</li>
            <li>가장 가까운 지하철역과의 거리</li>
          </ul>
        </li>
        <li><strong>생성한 피처 대부분이 최종 모델의 피처로 반영되어 성능 개선에 크게 기여함</strong></li>
      </ul>
    </div>
  </div>

  ---

  <div style="flex: 1; display: flex; align-items: center;">
    <div style="width: 100%;">
      <strong>공간 가중치 행렬 도입으로 최종 성능 개선</strong>
      <ul>
        <li><strong>가설 수립</strong>
          <ul>
            <li>아파트 전세가는 공간적 자기상관(spatial autocorrelation)을 갖는다는 가정 하에, 가까운 거리에 있는 아파트의 전세가가 유사할 것이라 판단</li>
          </ul>
        </li>
        <li><strong>구현 방식</strong>
          <ul>
            <li>위도, 경도를 기준으로 거리 기반 가중치 행렬을 계산</li>
            <li>메모리 효율을 위해 희소 행렬(Sparse Matrix) 형태로 저장</li>
            <li>각 아파트에 대해 주변 아파트의 면적당 전세가의 공간 가중 평균을 계산하여 새로운 피처로 추가</li>
          </ul>
        </li>
      </ul>
    </div>
  </div>

  #### 공간적 가중치 행렬 구현 과정에서의 Trouble Shooting
  <div style="flex: 1; display: flex; align-items: center;">
    <div style="width: 100%;">
      <strong>대규모 공간 가중치 행렬 계산</strong>
      <ul>
        <li><strong>문제점</strong>
          <ul>
            <li>약 180만 개의 row로 구성된 대규모 데이터셋</li>
            <li>전체를 한 번에 처리할 경우 메모리 초과 발생</li>
          </ul>
        </li>
        <li><strong>해결 전략</strong>
          <ul>
            <li>목적은 가중치 행렬 생성 자체가 아닌, 공간 가중 평균 피처 도출</li>
            <li>계산은 1회로 충분하므로 속도보다 메모리 효율 우선</li>
            <li>청크 단위(예: 1만 개)로 나누어 순차적으로 계산한 뒤, pkl 파일로 저장</li>
          </ul>
        </li>
      </ul>
    </div>
  </div>
