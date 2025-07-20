---
title: "개인화된 Top10 영화 추천"
permalink: /projects/top10-movie-recommendation/
layout: single
classes: wide
author_profile: false
related: true
---
<img src="/assets/images/top10-movie-recommendation_graph1.png"
     alt="top10-movie-recommendation_graph1"
     style="max-width: 100%; height: auto; display: block; margin: 2rem auto;" />

<!-- 버튼 링크 -->
<!-- Font Awesome 아이콘이 필요하므로 minimal-mistakes에서 이미 로딩됨 -->
<div style="display: flex; gap: 10px; margin-bottom: 2em;">

  <!-- GitHub 버튼 -->
  <a href="https://github.com/boostcampaitech7/level2-recsys-movierecommendation-recsys-02-lv3" target="_blank"
     style="display: inline-flex; align-items: center; gap: 6px; padding: 6px 12px;
            background-color: #f8f9fa; color: #212529; text-decoration: none;
            font-size: 14px; border-radius: 6px; border: 1px solid #dee2e6;">
    <i class="fab fa-github"></i> GitHub
  </a>

</div>


- 기간 : 2024.11 ~ 2024.11 (3주)
- 참여 인원 : 6인

## 프로젝트 개요
#### 프로젝트 목표
Recall@10 성능을 극대화하는 개인화된 영화 추천 모델 개발

#### 프로젝트 배경
- 각 사용자의 순차적인 영화 시청 이력(implicit feedback) 데이터를 보유
- 시청 이력은 시간 순으로 기록되어 있으나, 중간 또는 이후 일부 시점의 이력이 누락되어 있음
- 누락된 시청 이력을 보완하고, 사용자가 앞으로 시청할 가능성이 높은 영화를 예측할 필요가 있음

#### 결과
- EASE, EASER, RecVAE, MF, Multi-DAE, Multi-VAE, SASRec, BERT4Rec, DeepFM 등 다양한 추천 모델을 실험
- 최종 추천 모델로는 EASE 모델과 RecVAE 모델을 Hadamard product 방식으로 soft voting 앙상블한 모델이 선정
- 두 모델을 앙상블한 방식은 개별 모델 대비 더 높은 Recall@10 성능(0.1624)을 기록

## 내 역할 및 기여
<div style="display: flex; gap: 32px; margin-top: 1.5em; margin-bottom: 2em;">
  <!-- 좌측 이미지 -->
  <div style="flex: 0 0 300px;">
    <img src="/assets/images/top10-movie-recommendation_discussion.png" alt="깃허브 디스커션 공유" style="width: 100%; height: auto;">
  </div>

  <!-- 우측 텍스트를 감싸는 flex wrapper (세로 중앙 정렬용) -->
  <div style="flex: 1; display: flex; align-items: center;">
    <div style="width: 100%;">
      <strong>데이터 기반 인사이트 도출 및 팀 내 공유</strong>
      <ul>
        <li>데이터 전처리 및 EDA 수행</li>
        <li>EDA를 통해 얻은 인사이트를 Github Discussion을 통해 팀원들과 공유하여 모델 설계 방향 논의에 기여</li>
      </ul>
    </div>
  </div>
</div>

---

<div style="display: flex; gap: 32px; margin-top: 1.5em; margin-bottom: 2em;">
  <!-- 좌측 이미지 -->
  <div style="flex: 0 0 300px;">
    <img src="/assets/images/top10-movie-recommendation_graph2.png" alt="추천 모델 실험" style="width: 100%; height: auto;">
  </div>

  <!-- 우측 텍스트를 감싸는 flex wrapper (세로 중앙 정렬용) -->
  <div style="flex: 1; display: flex; align-items: center;">
    <div style="width: 100%;">
      <strong>추천 모델 성능 향상을 위한 실험 진행</strong>
      <ul>
        <li><strong>MF 모델 구현 및 실험</strong>
          <ul>
            <li>Recall@10 0.1427, 베이스라인 대비 약 68% 향상</li>
            <li>영화 제목, 장르, 개봉연도 등 side information을 TF-IDF로 벡터화, MF latent vector에 반영하여 Recall@10 0.1435로 추가 개선</li>
          </ul>
        </li>
        <li><strong>DeepFM 모델 구현 및 실험</strong>
          <ul>
            <li>Recall@10 0.003으로 성능 미달</li>
            <li>메타데이터 반영이 과도하여 유저-아이템 상호작용 정보가 희석되고, long-tail 분포에 맞지 않는 예측 분산 현상이 발생한 것으로 분석</li>
          </ul>
        </li>
      </ul>
    </div>
  </div>
</div>
