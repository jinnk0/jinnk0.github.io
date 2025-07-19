---
title: "캠핑 물품 픽업 서비스: Campssg"
permalink: /projects/campssg/
layout: single
classes: wide
author_profile: false
related: true
---
<img src="/assets/images/campssg1.png"
     alt="Campssg_구매자 시점"
     style="max-width: 100%; height: auto; display: block; margin: 2rem auto;" />
<img src="/assets/images/campssg2.png"
     alt="Campssg_마트 운영자 시점"
     style="max-width: 100%; height: auto; display: block; margin: 2rem auto;" />

<!-- 버튼 링크 -->
<!-- Font Awesome 아이콘이 필요하므로 minimal-mistakes에서 이미 로딩됨 -->
<div style="display: flex; gap: 10px; margin-bottom: 2em;">

  <!-- GitHub 버튼 -->
  <a href="https://github.com/campssg/Campssg-Server" target="_blank"
     style="display: inline-flex; align-items: center; gap: 6px; padding: 6px 12px;
            background-color: #f8f9fa; color: #212529; text-decoration: none;
            font-size: 14px; border-radius: 6px; border: 1px solid #dee2e6;">
    <i class="fab fa-github"></i> GitHub
  </a>

  <!-- 시연 영상 버튼 -->
  <a href="https://drive.google.com/file/d/1UKOp8SFskL3WS2uZvAjc25uo3LJpauII/view?usp=sharing" target="_blank"
     style="display: inline-flex; align-items: center; gap: 6px; padding: 6px 12px;
            background-color: #f8f9fa; color: #212529; text-decoration: none;
            font-size: 14px; border-radius: 6px; border: 1px solid #dee2e6;">
    <i class="fas fa-video"></i> 시연 영상
  </a>

</div>


- 기간 : 2021.09.01 ~ 2022.05.27 (9개월)
- 참여 인원 : 4인

## 프로젝트 개요
#### 프로젝트 목표
-  캠핑 시 반복되는 짐 준비의 번거로움을 줄이기 위해, 캠핑장 인근 마트에서 필요한 물품을 미리 주문하고 현장에서 간편하게 픽업할 수 있는 쇼핑 경험을 제공하는 것
-  사용자에게는 짐 부담을 줄이고, 지역 마트에는 추가 매출 기회를 제공하는 상생 모델을 지향
#### 프로젝트 배경
- 캠핑을 갈 때 챙겨야 하는 짐이 많아 불편함
- 캠핑 짐의 대부분은 캠핑장에서 소모하면 사라지는 물품
- 캠핑 짐을 캠핑장 주변 인근 매장에서 주문하고 픽업하도록 하면 편의성 증가

#### 내 역할 및 기여 요약
- 프로젝트 관리 및 팀 리딩
- 데이터베이스 설계 및 최적화
- 백엔드 개발
  - SpringBoot 기반 REST API 설계 및 구현 (주문, 마트 관리, 사용자 인증)
  - JWT 기반 사용자 인증 및 권한 관리 적용
  - 외부 API 연동 (Tour API(GoCamping), 네이버 지도 API 활용 캠핑장·마트 위치 기반 검색)

## 기술 스택 및 아키텍처 구성도
<img src="/assets/images/campssg_architecture.png"
     alt="Campssg 아키텍처"
     style="max-width: 80%; height: auto; display: block; margin: 2rem auto;" />
- **사용 기술 스택**: Java, SpringBoot, AWS EC2, AWS S3, MySQL, JWT, JPA, Firebase
- **아키텍처 구성 및 데이터 흐름**:  
	- **프론트엔드**: Kotlin 기반 Android 애플리케이션으로 구현. 사용자 위치 기반 마트 조회, 장바구니 관리, 결제, 픽업 등 주요 기능을 앱에서 수행. 서버와는 Retrofit2를 통해 REST API 통신
  - **서비스 서버**: Java + Spring Boot 기반 RESTful API 설계 및 구현. EC2에 배포되어 클라이언트 요청을 처리하며, 캠핑장 정보(GoCamping API), 위치 기반 검색(네이버 지도 API) 등 외부 API와 연동
  - **데이터베이스 구성**: MySQL 사용. 사용자 계정, 마트 정보, 상품, 주문 내역 등을 정규화하여 설계하고 JPA 기반으로 연동
  - **파일 저장소**: AWS S3를 활용하여 마트 상품 이미지, QR 코드 이미지 등 정적 자산 관리

## 주요 기능 상세 설명

<div style="display: flex; gap: 32px; margin-top: 1.5em; margin-bottom: 2em;">
  <!-- 좌측 이미지 -->
  <div style="flex: 0 0 300px;">
    <img src="/assets/images/campssg_function_search.png" alt="캠핑장 위치 기반 마트 조회" style="width: 100%; height: auto;">
  </div>

  <!-- 우측 텍스트를 감싸는 flex wrapper (세로 중앙 정렬용) -->
  <div style="flex: 1; display: flex; align-items: center;">
    <div style="width: 100%;">
      <h4 style="margin-top: 0;">기능 1. 캠핑장 위치 기준 인근 마트 조회</h4>

      <ul>
        <li><strong>기획 의도 및 구현 방법</strong>
          <ul>
            <li>캠핑장 주변에서 필요한 물품을 빠르게 구입할 수 있도록, 사용자가 선택한 캠핑장 위치를 기준으로 인근 마트를 조회하는 기능을 구현</li>
            <li>GoCamping API를 활용하여 캠핑장 위치 좌표를 받아옴</li>
          </ul>
        </li>
        <li><strong>주요 코드 구조 또는 API 설계 내용</strong>
          <ul>
            <li><code>GET /search/mart/{latitude}/{longitude}</code> : 주어진 위도, 경도 좌표를 기준으로 반경 3km 이내의 마트를 오름차순으로 반환 (가까운 순서)</li>
          </ul>
        </li>
        <li><strong>기능 구현 과정에서 고려한 점</strong>
          <ul>
            <li>지정 좌표와 마트 간 거리 계산 시, 위도/경도를 활용한 하버사인 공식(Haversine Formula) 적용</li>
          </ul>
        </li>
        <li><strong>기능 적용 후 기대 효과</strong>
          <ul>
            <li>사용자 입장에서 캠핑장에 도착하기 전, 실제 접근 가능한 마트를 손쉽게 찾을 수 있어 사용성과 신뢰성 향상</li>
          </ul>
        </li>
      </ul>
    </div>
  </div>
</div>

---

<div style="display: flex; gap: 32px; margin-top: 1.5em; margin-bottom: 2em;">
  <!-- 좌측 이미지 -->
  <div style="flex: 0 0 600px;">
    <img src="/assets/images/campssg_function_cart.png" alt="캠핑장 위치 기반 마트 조회" style="width: 100%; height: auto;">
  </div>

  <!-- 우측 텍스트를 감싸는 flex wrapper (세로 중앙 정렬용) -->
  <div style="flex: 1; display: flex; align-items: center;">
    <div style="width: 100%;">
      <h4 style="margin-top: 0;">기능 2. 마트 상품 조회 및 장바구니</h4>

      <ul>
        <li><strong>기획 의도 및 구현 방법</strong>
          <ul>
            <li>캠핑에 필요한 물품은 여러 개를 한 번에 구매하는 경우가 많기 때문에, 장바구니 기능을 통해 상품을 모아서 주문할 수 있도록 설계</li>
          </ul>
        </li>
        <li><strong>주요 코드 구조 또는 API 설계 내용</strong>
          <ul>
            <li><code>GET /search/mart/{martId}</code> : 선택한 마트의 상품 목록 반환</li>
            <li><code>GET /serach/mart/canAdd/{martId}</code> : 선택한 마트의 상품이 기존 장바구니 상품의 마트와 일치하는지 확인</li>
            <li><code>POST /search/mart/{martId}/{productId}</code> : 일치할 경우 해당 상품을 장바구니에 추가</li>
            <li><code>POST /search/mart/new/{productId}</code> : 일치하지 않을 경우 기존 장바구니를 삭제하고 새로운 장바구니를 생성하여 상품 추가</li>
          </ul>
        </li>
        <li><strong>기능 구현 과정에서 고려한 점</strong>
          <ul>
            <li>사용자 혼란 방지를 위해 장바구니에는 항상 하나의 마트의 상품만 담기도록 제약 조건 설정</li>
            <li>같은 마트 여부 확인 API를 통해 장바구니 일관성을 보장하고, UX 혼란 최소화</li>
          </ul>
        </li>
        <li><strong>기능 적용 후 기대 효과</strong>
          <ul>
            <li>다양한 상품을 편리하게 한 번에 구매 가능</li>
            <li>중복 결제나 상품 혼선을 방지함으로써 구매 전환율 향상</li>
          </ul>
        </li>
      </ul>
    </div>
  </div>
</div>

---

<div style="display: flex; gap: 32px; margin-top: 1.5em; margin-bottom: 2em;">
  <!-- 좌측 이미지 -->
  <div style="flex: 0 0 300px;">
    <img src="/assets/images/campssg_function_price.png" alt="가격 비교 예시" style="width: 100%; height: auto;">
  </div>

  <!-- 우측 텍스트를 감싸는 flex wrapper (세로 중앙 정렬용) -->
  <div style="flex: 1; display: flex; align-items: center;">
    <div style="width: 100%;">
      <h4 style="margin-top: 0;">기능 3. 다른 마트와 거리 및 장바구니 상품 가격 비교</h4>

      <ul>
        <li><strong>기획 의도 및 구현 방법</strong>
          <ul>
            <li>사용자가 선택한 상품이 다른 마트에서는 더 저렴하거나 가까울 수 있으므로, 장바구니에 담긴 상품을 기준으로 다른 마트와의 가격 및 재고를 비교할 수 있는 기능을 제공</li>
          </ul>
        </li>
        <li><strong>주요 코드 구조 또는 API 설계 내용</strong>
          <ul>
            <li><code>GET /cart/{latitude}/{longitude}</code> : 캠핑장 위치를 기반으로 반경 3km 내에 있는 마트들과 장바구니에 담겨있는 상품들의 재고 및 가격 비교</li>
          </ul>
        </li>
        <li><strong>기능 구현 과정에서 고려한 점</strong>
          <ul>
            <li>마트별로 상품 재고가 다를 수 있음을 고려해, 없는 상품 명시</li>
            <li>사용자에게 정확한 비교 정보를 제공하기 위해 가격 외에 재고 여부, 거리 정보도 함께 제공</li>
          </ul>
        </li>
        <li><strong>기능 적용 후 기대 효과</strong>
          <ul>
            <li>소비자 입장에서 더 저렴한 가격의 마트를 선택할 수 있어 경제적 효용성 증가</li>
            <li>마트 간 경쟁 유도 가능</li>
          </ul>
        </li>
      </ul>
    </div>
  </div>
</div>

---

<div style="display: flex; gap: 32px; margin-top: 1.5em; margin-bottom: 2em;">
  <!-- 좌측 이미지 -->
  <div style="flex: 0 0 300px; display: flex; flex-direction: column; gap: 16px;">
    <img src="/assets/images/campssg_function_product1.png" alt="상품 리스트 등록" style="width: 100%; height: auto;">
    <img src="/assets/images/campssg_function_product2.png" alt="상품 개별 등록" style="width: 100%; height: auto;">
  </div>

  <!-- 우측 텍스트를 감싸는 flex wrapper (세로 중앙 정렬용) -->
  <div style="flex: 1; display: flex; align-items: center;">
    <div style="width: 100%;">
      <h4 style="margin-top: 0;">기능 4. 마트에 상품 등록</h4>

      <ul>
        <li><strong>기획 의도 및 구현 방법</strong>
          <ul>
            <li>마트 운영자가 상품을 간편하게 등록할 수 있도록 캠핑용품 추천 리스트를 제공하고, 원하는 경우 개별 상품을 자유롭게 추가할 수 있도록 설계</li>
          </ul>
        </li>
        <li><strong>주요 코드 구조 또는 API 설계 내용</strong>
          <ul>
            <li><code>POST /mart/{martId}</code> : 해당 마트에 개별 상품 등록</li>
            <li><code>POST /mart/{martId}/list</code> : 해당 마트에 상품 리스트 등록</li>
          </ul>
        </li>
        <li><strong>기능 구현 과정에서 고려한 점</strong>
          <ul>
            <li>대량 등록을 지원하기 위해 복수 상품 등록 API 설계 (배치 등록 고려)</li>
          </ul>
        </li>
        <li><strong>기능 적용 후 기대 효과</strong>
          <ul>
            <li>마트 관리자 입장에서 상품 등록 시간이 단축됨</li>
            <li>플랫폼 초기 정착에 필요한 물품 등록 장벽을 낮춤</li>
          </ul>
        </li>
      </ul>
    </div>
  </div>
</div>

---

<div style="display: flex; gap: 32px; margin-top: 1.5em; margin-bottom: 2em;">
  <!-- 좌측 이미지 -->
  <div style="flex: 0 0 300px;">
    <img src="/assets/images/campssg_function_order.png" alt="상품 등록 예시" style="width: 100%; height: auto;">
  </div>

  <!-- 우측 텍스트를 감싸는 flex wrapper (세로 중앙 정렬용) -->
  <div style="flex: 1; display: flex; align-items: center;">
    <div style="width: 100%;">
      <h4 style="margin-top: 0;">기능 5. 상품 결제 및 QR 코드를 통한 픽업</h4>

      <ul>
        <li><strong>기획 의도 및 구현 방법</strong>
          <ul>
            <li>빠른 픽업을 위해 결제 완료 시 QR 코드를 발급하여 이를 스캔하면 픽업 완료 처리를 간편하게 할 수 있도록 설계</li>
            <li>결제 기능은 Bootpay SDK를 통해 프론트에서 구현</li>
            <li>서버는 결제 정보를 받아 주문서 생성 및 QR 코드 발급, 주문서 상태 관리</li>
          </ul>
        </li>
        <li><strong>주요 코드 구조 또는 API 설계 내용</strong>
          <ul>
            <li><code>POST /order/add</code> : 결제 완료 후 QR코드를 포함한 주문서 생성</li>
            <li><code>PUT /order/{orderId}/{status}</code> : 주문서의 주문 상태 변경</li>
          </ul>
        </li>
        <li><strong>기능 구현 과정에서 고려한 점</strong>
          <ul>
            <li>QR 코드에 해당 주문서의 주문 상태 변경 API의 url을 담아 주문서의 주문 상태를 픽업 완료로 변경</li>
          </ul>
        </li>
        <li><strong>기능 적용 후 기대 효과</strong>
          <ul>
            <li>운영자 입장에서 복잡한 확인 절차 없이 실물 픽업 처리 가능</li>
            <li>사용자에게도 간편하고 매끄러운 주문-결제-수령 경험 제공</li>
          </ul>
        </li>
      </ul>
    </div>
  </div>
</div>

## 개발 과정에서의 어려움 및 문제 해결 과정
<div style="display: flex; gap: 32px; margin-top: 1.5em; margin-bottom: 2em;">
  <!-- 좌측 이미지 -->
  <div style="flex: 0 0 300px; display: flex; align-items: center;">
    <img src="/assets/images/campssg_problem1.png" alt="장바구니 마트 정보 충돌 시 알림창" style="width: 100%; height: auto;">
  </div>

  <!-- 우측 텍스트를 감싸는 flex wrapper (세로 중앙 정렬용) -->
  <div style="flex: 1; display: flex; align-items: center;">
    <div style="width: 100%;">
      <h4 style="margin-top: 0;">장바구니 상품 추가 시 마트 충돌 문제 해결</h4>

      <ul>
        <li><strong>문제점</strong>
          <ul>
            <li>사용자가 특정 마트에서 상품을 담은 후, 다른 마트에서 상품을 추가하려 하면 기존 상품과 소속 마트가 달라 충돌 발생</li>
            <li>장바구니에 여러 마트의 상품이 혼재될 위험성 존재</li>
          </ul>
        </li>
        <li><strong>해결 방법</strong>
          <ul>
            <li>장바구니에 상품 추가 시 기존 상품과 마트 ID 비교</li>
            <li>추가하려는 상품의 마트가 기존 상품과 다를 경우 경고 팝업을 띄워 사용자 확인 요청</li>
            <li>사용자가 승인하면 기존 장바구니를 삭제하고 새로운 장바구니를 생성하여 상품 추가</li>
          </ul>
        </li>
      </ul>
    </div>
  </div>
</div>

<div style="display: flex; gap: 32px; margin-top: 1.5em; margin-bottom: 2em;">
  <!-- 좌측 이미지 -->
  <div style="flex: 0 0 300px; display: flex; align-items: center;">
    <img src="/assets/images/campssg_problem2.png" alt="장바구니 상품 가격 비교 기능 최적화" style="width: 100%; height: auto;">
  </div>

  <!-- 우측 텍스트를 감싸는 flex wrapper (세로 중앙 정렬용) -->
  <div style="flex: 1; display: flex; align-items: center;">
    <div style="width: 100%;">
      <h4 style="margin-top: 0;">장바구니 상품 가격 비교 기능 최적화</h4>

      <ul>
        <li><strong>문제점</strong>
          <ul>
            <li>장바구니 상품 가격 비교 기능 이용 시 마트마다 상품 품목과 재고가 달라 일부 상품이 누락되는 문제 발생</li>
            <li>모든 상품을 기준으로 비교하면 재고가 없는 마트가 가격이 적게 뜨기 때문에 비교 자체가 어려움</li>
          </ul>
        </li>
        <li><strong>해결 방법</strong>
          <ul>
            <li>각 마트마다 장바구니 내 상품 중 재고가 없는 품목의 개수를 표시</li>
            <li>사용자가 마트별 재고 상황을 명확히 인지하고 가격을 확인할 수 있도록 개선</li>
          </ul>
        </li>
      </ul>
    </div>
  </div>
</div>
