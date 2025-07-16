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


- 기간 : 2021.09.01 ~ 2022.05.22 (9개월)
- 참여 인원 : 4인

## 프로젝트 개요
#### 프로젝트 목표
- 
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
	- **프론트엔드**: 
  - **서비스 서버**: 
  - **데이터베이스 구성**:

## 주요 기능 상세 설명

<div style="display: flex; gap: 32px; margin-top: 1.5em; margin-bottom: 2em;">
  <!-- 좌측 이미지 -->
  <div style="flex: 0 0 300px;">
    <img src="/assets/images/tune-your-shop_function_login.png" alt="JWT 사용자 인증" style="width: 100%; height: auto;">
  </div>

  <!-- 우측 텍스트를 감싸는 flex wrapper (세로 중앙 정렬용) -->
  <div style="flex: 1; display: flex; align-items: center;">
    <div style="width: 100%;">
      <h4 style="margin-top: 0;">기능 1. JWT 사용자 인증 및 인가</h4>

      <ul>
        <li><strong>기획 의도 및 구현 방법</strong>
          <ul>
            <li>두 가지 권한 관리 블라블라</li>
            <li></li>
          </ul>
        </li>
        <li><strong>주요 코드 구조 또는 API 설계 내용</strong>
          <ul>
            <li><code>GET /login</code> : </li>
            <li></li>
          </ul>
        </li>
        <li><strong>기능 구현 과정에서 고려한 점</strong>
          <ul>
            <li></li>
            <li></li>
          </ul>
        </li>
        <li><strong>기능 적용 후 기대 효과</strong>
          <ul>
            <li></li>
            <li></li>
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
    <img src="/assets/images/tune-your-shop_function_onboarding.png" alt="Onboarding 시스템" style="width: 100%; height: auto;">
  </div>

  <!-- 우측 텍스트를 감싸는 flex wrapper (세로 중앙 정렬용) -->
  <div style="flex: 1; display: flex; align-items: center;">
    <div style="width: 100%;">
      <h4 style="margin-top: 0;">기능 2. 온보딩 시스템</h4>

      <ul>
        <li><strong>기획 의도 및 구현 방법</strong>
          <ul>
            <li>사용자 임베딩이 존재하지 않는 신규 유저를 위한 최초 1회 진행 온보딩 기능</li>
            <li>가게 분위기를 표현하는 태그를 사용자가 선택하면, 해당 태그와 연관된 곡 중 20곡을 선별</li>
            <li>이 중 2곡씩 총 10세트로 제시하고, 각 세트마다 1곡을 선택</li>
            <li> 사용자가 선택한 10곡의 임베딩 평균값을 이용해 신규 사용자 임베딩 생성</li>
          </ul>
        </li>
        <li><strong>주요 코드 구조 또는 API 설계 내용</strong>
          <ul>
            <li><code>POST /onboarding</code> : 사용자가 선택한 분위기 태그를 저장하고, 해당 태그에 맞는 후보곡 20곡을 반환</li>
          </ul>
        </li>
        <li><strong>기능 구현 과정에서 고려한 점</strong>
          <ul>
            <li>정확한 임베딩 생성을 위해 태그별로 상호작용 데이터가 풍부한 곡들을 우선적으로 선별</li>
            <li>같은 태그 요청이 반복될 가능성이 높아, Redis 캐싱을 통해 응답 속도 최적화</li>
          </ul>
        </li>
        <li><strong>기능 적용 후 기대 효과</strong>
          <ul>
            <li>음원 상호작용 이력이 없는 신규 유저도 즉시 추천 시스템을 이용할 수 있는 사용자 임베딩 생성 가능</li>
            <li>사용자 초기 경험을 자연스럽게 설계함으로써 서비스 진입 허들을 낮춤</li>
          </ul>
        </li>
      </ul>
    </div>
  </div>
</div>

---

<!-- 기능명 및 개요 -->
<h3 style="margin-top: 1.5em;">기능 3. 사용자 플레이리스트 선택</h3>
<ul>
  <li><strong>기획 의도 및 구현 방법</strong>
    <ul>
      <li>사용자 임베딩이 존재하지 않는 신규 유저를 위한 최초 1회 진행 온보딩 기능</li>
      <li>가게 분위기를 표현하는 태그를 사용자가 선택하면, 해당 태그와 연관된 곡 중 20곡을 선별</li>
      <li>이 중 2곡씩 총 10세트로 제시하고, 각 세트마다 1곡을 선택</li>
      <li> 사용자가 선택한 10곡의 임베딩 평균값을 이용해 신규 사용자 임베딩 생성</li>
    </ul>
  </li>
</ul>

<!-- 방법 1: Spotify 연동 -->
<div style="display: flex; gap: 32px; margin: 2em 0;">
  <!-- 좌측: 이미지 -->
  <div style="flex: 0 0 300px;">
    <img src="/assets/images/tune-your-shop_function_playlist.png" alt="Spotify 플레이리스트 연동 예시" style="width: 100%; height: auto;">
  </div>

  <!-- 우측: 텍스트 -->
  <div style="flex: 1; display: flex; align-items: center;">
    <div style="width: 100%;">
      <strong>▶ 방법 1. Spotify 연동</strong>
      <ul>
        <li><strong>주요 코드 구조 또는 API 설계 내용</strong>
          <ul>
            <li><code>GET /users/{user_id}/playlists</code> : 사용자가 Spotify에 보유 중인 플레이리스트 목록 반환</li>
          </ul>
        </li>
        <li><strong>기능 구현 과정에서 고려한 점</strong>
          <ul>
            <li>로그인 후 자연스럽게 플레이리스트 조회로 이어지는 UX 구성</li>
            <li>플레이리스트 트랙 정보를 기반으로 유사도 정렬 가능한 구조 설계</li>
          </ul>
        </li>
      </ul>
    </div>
  </div>
</div>

<!-- 방법 2: 이미지 OCR 업로드 -->
<div style="display: flex; gap: 32px; margin: 2em 0;">
  <!-- 좌측: 이미지 -->
  <div style="flex: 0 0 300px;">
    <img src="/assets/images/tune-your-shop_function_ocr.png" alt="OCR 이미지 업로드 예시" style="width: 100%; height: auto;">
  </div>

  <!-- 우측: 텍스트 -->
  <div style="flex: 1; display: flex; align-items: center;">
    <div style="width: 100%;">
      <strong>▶ 방법 2. 이미지 OCR 업로드</strong>
      <ul>
        <li><strong>주요 코드 구조 또는 API 설계 내용</strong>
          <ul>
            <li><code>POST /playlist/image</code> : 사용자가 업로드한 이미지에서 OCR을 통해 음원 목록 추출 후 반환</li>
          </ul>
        </li>
        <li><strong>기능 구현 과정에서 고려한 점</strong>
          <ul>
            <li>Upstage OCR API 활용 및 사용자 검증 프로세스 도입</li>
            <li> 음원명과 아티스트명만 정확히 추출하기 위해 전·후처리 적용</li>
            <ul>
              <li>전처리: 예시 이미지 제공을 통해 불필요한 정보 제거 유도</li>
              <li>후처리: 불용어 필터링, 정규식 기반 텍스트 정제 적용</li>
            </ul>
          </ul>
        </li>
      </ul>
    </div>
  </div>
</div>

<!-- 기대 효과 -->
<strong>기능 적용 후 기대 효과</strong>
<ul>
  <li>두 가지 등록 방식을 통해 사용자 편의성과 접근성 향상</li>
  <li>정확한 취향 반영으로 사용자 만족도 및 추천 신뢰도 상승</li>
  <li>기존 음악 플랫폼보다 개인화된 큐레이션 제공 가능</li>
</ul>

---

<div style="display: flex; gap: 32px; margin-top: 1.5em; margin-bottom: 2em;">
  <!-- 좌측 이미지 -->
  <div style="flex: 0 0 300px;">
    <img src="/assets/images/tune-your-shop_function_recommendation.png" alt="추천 결과 반환 예시" style="width: 100%; height: auto;">
  </div>

  <!-- 우측 텍스트를 감싸는 flex wrapper (세로 중앙 정렬용) -->
  <div style="flex: 1; display: flex; align-items: center;">
    <div style="width: 100%;">
      <h4 style="margin-top: 0;">기능 4. 개인화 음악 추천</h4>

      <ul>
        <li><strong>기획 의도 및 구현 방법</strong>
          <ul>
            <li>사용자 임베딩과 선택한 플레이리스트 트랙 정보를 함께 고려해 개인화된 음악 추천 제공</li>
            <li>사용자 임베딩은 사용자의 상호작용 이력을 반영하여 지속적으로 갱신됨</li>
            <ul>
              <li>신규 사용자는 온보딩 기반 선택 정보로 초기 임베딩 생성</li>
              <li>기존 사용자는 과거 추천 결과 중 선택한 곡 로그를 반영하여 임베딩 재생성</li>
            </ul>
            <li>선택한 플레이리스트의 트랙 메타 정보를 기반으로 추천 모델 API에 입력값 전달 → 추론 결과를 가공해 추천 결과 반환</li>
          </ul>
        </li>
        <li><strong>주요 코드 구조 또는 API 설계 내용</strong>
          <ul>
            <li><code>GET /playlists/{playlist_id}/tracks</code> : Spotify 연동 플레이리스트 선택 시 트랙 목록과 사용자 임베딩을 기반으로 추천 결과 반환</li>
            <li><code>POST /playlist/image/tracks</code> : OCR로 추출한 트랙 목록과 사용자 임베딩을 기반으로 추천 결과 반환</li>
          </ul>
        </li>
        <li><strong>기능 구현 과정에서 고려한 점</strong>
          <ul>
            <li>트랙 메타 정보가 DB에 없는 경우 Last.fm API 연동을 통해 보완</li>
            <li>추천 결과는 단순 모델 출력이 아닌, 사용자 입력에 대한 반응성이 느껴지도록 ‘유사도 기반 정렬’ 방식 적용</li>
          </ul>
        </li>
        <li><strong>기능 적용 후 기대 효과</strong>
          <ul>
            <li>단순 인기 기반이 아닌, 사용자 취향을 반영한 맞춤형 추천 제공</li>
            <li>사용자 임베딩과 플레이리스트를 모두 반영하여 추천의 정확도 향상</li>
          </ul>
        </li>
      </ul>
    </div>
  </div>
</div>

---

### 기능 5. 추천 음악 플레이리스트에 추가
- **기획 의도 및 구현 방법**
    - 추천된 음악 중 사용자가 선택한 곡들을 본인의 플레이리스트에 손쉽게 추가할 수 있도록 지원
    - Spotify 연동 유저는 기존에 선택한 플레이리스트에 곡을 추가
    - OCR로 음원 목록을 등록한 유저는 새 플레이리스트를 생성하여 선택한 곡들로 구성
- **주요 코드 구조 또는 API 설계 내용**
    - `POST /playlists/{playlist_id}/tracks` : Spotify 연동 플레이리스트에 선택한 트랙 추가
    - `POST /playlist/create` : 선택한 트랙을 담은 새로운 플레이리스트 생성 및 트랙 추가
- **기능 구현 과정에서 고려한 점**
    - 기존 서비스 흐름과 자연스럽게 연결되도록 설계
- **기능 적용 후 기대 효과**
    - 사용자 편의성을 증대하고 유연한 서비스 경험 제공



## 개발 과정에서의 어려움 및 문제 해결 과정
<div style="display: flex; gap: 32px; margin-top: 1.5em; margin-bottom: 2em;">
  <!-- 좌측 이미지 -->
  <div style="flex: 0 0 300px; display: flex; align-items: center;">
    <img src="/assets/images/tune-your-shop_problem2.png" alt="응답 시간 단축 표" style="width: 100%; height: auto;">
  </div>

  <!-- 우측 텍스트를 감싸는 flex wrapper (세로 중앙 정렬용) -->
  <div style="flex: 1; display: flex; align-items: center;">
    <div style="width: 100%;">
      <h4 style="margin-top: 0;">모델 결과 반환 API 응답 속도 최적화</h4>

      <ul>
        <li><strong>문제점</strong>
          <ul>
            <li>추천 모델 API 응답 지연으로 사용자 경험 저하 우려</li>
          </ul>
        </li>
        <li><strong>해결 방법</strong>
          <ul>
            <li> DB 쿼리를 기존 <code>EXISTS + ORDER BY</code>에서 <code>JOIN + IN</code> 연산자로 변경해 트랙명, 아티스트명 조회 최적화 (47% 속도 단축)</li>
            <li>Python 코드 내에서 정렬 처리로 DB 부하 감소</li>
            <li>외부 API 호출을 `asyncio.gather()`로 비동기 처리해 61% 추가 단축</li>
          </ul>
        </li>
        <li><strong>최종 성과</strong>
          <ul>
            <li>초기 대비 79% 응답 속도 단축으로 서비스 체감 성능 크게 개선</li>
          </ul>
        </li>
      </ul>
    </div>
  </div>
</div>

<div style="display: flex; gap: 32px; margin: 2em 0;">
  <!-- 좌측: 이미지 2개 세로 배치 -->
  <div style="flex: 0 0 300px; display: flex; flex-direction: column; gap: 16px;">
    <img src="/assets/images/tune-your-shop_problem1.png" alt="생략되는 긴 문자열 예시" style="width: 100%; height: auto;">
    <img src="/assets/images/tune-your-shop_problem3.png" alt="불용어 예시" style="width: 100%; height: auto;">
  </div>

  <!-- 우측 텍스트를 감싸는 flex wrapper (세로 중앙 정렬용) -->
  <div style="flex: 1; display: flex; align-items: center;">
    <div style="width: 100%;">
      <h4 style="margin-top: 0;">OCR 인식 최적화 및 음원 매칭 문제 해결</h4>

      <ul>
        <li><strong>문제점</strong>
          <ul>
            <li>플레이리스트 캡처 이미지에서 트랙명/아티스트명이 길어 ‘…’으로 생략되어 데이터베이스와 정확한 매칭 어려움</li>
            <li>OCR 결과에 동영상, 불용어 등 인식 오류 포함</li>
          </ul>
        </li>
        <li><strong>해결 방법</strong>
          <ul>
            <li>‘…’ 생략 부분을 퍼센트(%) 와일드카드로 변환해 SQL `LIKE` 검색 적용</li>
            <li>difflib 라이브러리로 텍스트 유사도 계산, 60% 이상일 경우 동일 음원으로 판단</li>
            <li>정규표현식으로 불용어 필터링 및 사전 제외 단어 리스트 관리</li>
            <li>사용자 직접 검증 프로세스를 추가해 최종 음원 확정</li>
          </ul>
        </li>
        <li><strong>결과</strong>
          <ul>
            <li>OCR 인식 오류를 효과적으로 보완해 사용자 경험과 데이터 정확도 향상</li>
          </ul>
        </li>
      </ul>
    </div>
  </div>
</div>
