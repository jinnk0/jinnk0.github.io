---
title: "자영업자들을 위한 음악 큐레이션 서비스: Tune Your Shop"
permalink: /projects/tune-your-shop/
layout: single
classes: wide
author_profile: false
related: true
---
<img src="/assets/images/tune-your-shop.png"
     alt="Tune Your Shop"
     style="max-width: 100%; height: auto; display: block; margin: 2rem auto;" />

- 기간 : 2025.01.06 ~ 2025.02.12 (5주)
- 참여 인원 : 5인

## 프로젝트 개요
#### 프로젝트 목표
AI를 활용해 자영업자의 반복적인 음악 선곡 업무를 자동화하고, 고객 경험과 매출 향상에 기여하는 음악 큐레이션 서비스 개발
#### 프로젝트 배경
<div style="display: flex; gap: 24px; align-items: flex-start;">
  <div style="flex: 1; text-align: center;">
    <img src="/assets/images/tune-your-shop_graph.png" alt="연구결과 이미지" style="max-width: 100%; height: 250px; object-fit: contain;">
    <p style="font-size: 0.7em;">매장 분위기에 어울리는 음악은 매출 증가에 기여, 반면 부적절한 음악은 매출을 떨어뜨림</p>
  </div>
  <div style="flex: 1; text-align: center;">
    <img src="/assets/images/tune-your-shop_graph2.png" alt="기존 서비스 이미지" style="max-width: 100%; height: 250px; object-fit: contain;">
    <p style="font-size: 0.7em;">기존 큐레이션 서비스는 대형 매장 중심, 소상공인은 시간·비용 제약으로 적절한 음악 선곡이 어려움</p>
  </div>
</div>

- 기업 해커톤 주제인 AGI for work에 맞춰, 실생활에서 접하기 쉽고 누구나 공감가능한 주제로 ‘음악’과 ‘업무 효율화’를 결합
- 음악이 매출에 미치는 연구 결과와 관련 서비스를 고려

#### 내 역할 및 기여 요약
- 서비스 백엔드 전반 개발 담당
- 외부 API(스포티파이, Last.fm, Upstage OCR) 연동해 데이터 수집 및 처리
- AI 추천 모델에 필요한 입력값을 조회하고 처리하며 결과를 정제해 프론트엔드에 전달

## 기술 스택 및 아키텍처 구성도
<img src="/assets/images/tune-your-shop_architecture.png"
     alt="Tune Your Shop"
     style="max-width: 80%; height: auto; display: block; margin: 2rem auto;" />
- **사용 기술 스택**:  Python, FastAPI, PostgreSQL, MongoDB, GCP, Docker
- **아키텍처 구성 및 데이터 흐름**:  
	- **프론트엔드**: React 기반, 모바일 사이즈 웹으로 구성. 사용자 요청 시 서비스 서버의 기능 API 호출
    - **서비스 서버**: FastAPI로 구현. 외부 API(Spotify, Last.fm, Upstage OCR) 연동, 프론트에 기능 API 제공
    - **데이터베이스 구성**:
		- PostgreSQL: 관계형 데이터 저장 및 모델 학습용 벡터 저장
	    - MongoDB: 사용자 로그 저장 및 개인화 추천 반영
	    - Redis: 자주 사용하는 정보 캐싱하여 응답 속도 개선
	- **AI 모델 서버**:
	    - PyTorch 기반 LightGCN 모델 학습
	    - Airflow로 주기적인 재학습 스케줄링


## 주요 기능 상세 설명

<div style="display: flex; align-items: flex-start; gap: 32px; margin-top: 1.5em; margin-bottom: 2em;">
  <!-- 이미지 -->
  <div style="flex: 0 0 300px;">
    <img src="/assets/images/tune-your-shop_function_login.png" alt="Spotify OAuth 로그인 기능" style="width: 100%; height: auto;">
  </div>

  <!-- 텍스트 -->
  <div style="flex: 1;">
    <h4 style="margin-top: 0;">기능 1. 사용자 로그인 (Spotify OAuth 연동)</h4>

    <ul>
      <li><strong>기획 의도 및 구현 방법</strong>
        <ul>
          <li>Spotify OAuth 인증 방식을 사용하여 사용자 로그인 구현</li>
          <li>자체 회원 시스템 없이 Spotify 계정을 통해 로그인하여 진입 장벽을 낮춤</li>
        </ul>
      </li>
      <li><strong>주요 코드 구조 또는 API 설계 내용</strong>
        <ul>
          <li><code>GET /login</code> : Spotify 인증 페이지로 리디렉션</li>
          <li><code>GET /callback</code> : 로그인 후 redirect된 요청에서 사용자 토큰 및 정보 저장</li>
        </ul>
      </li>
      <li><strong>기능 구현 과정에서 고려한 점</strong>
        <ul>
          <li>이후 기능인 플레이리스트 조회 및 음악 추가를 위해 Spotify API 연동이 필수</li>
          <li>OAuth 인증 플로우의 자연스러운 UX를 위해 redirect 흐름을 부드럽게 구성</li>
        </ul>
      </li>
      <li><strong>기능 적용 후 기대 효과</strong>
        <ul>
          <li>Spotify API를 통한 다양한 기능 확장 가능</li>
          <li>별도 회원가입 없이 곡 추천, 플레이리스트 연동 등 고급 기능을 바로 사용 가능</li>
        </ul>
      </li>
    </ul>
  </div>
</div>


✅ 기능 1. `사용자 로그인 (Spotify OAuth 연동)`
- **기획 의도 및 구현 방법**
    - Spotify OAuth 인증 방식을 사용하여 사용자 로그인 구현
    - 자체 회원 시스템을 만들지 않고, Spotify 계정을 통해 로그인하게 하여 사용자 진입 장벽을 낮춤
- **주요 코드 구조 또는 API 설계 내용**
    - `GET /login` : Spotify 인증 페이지로 리디렉션
    - `GET /callback` : 로그인 후 redirect된 요청에서 사용자 토큰/정보 저장
- **기능 구현 과정에서 고려한 점**
    - 이후 기능인 `플레이리스트 정보 조회`와 `플레이리스트 음악 추가`를 위해 Spotify API 연동이 필요
    - OAuth 인증 플로우 특성상 사용자 경험에 어색함이 없도록 redirect 흐름을 자연스럽게 구성
- **기능 적용 후 기대 효과**
    - Spotify API를 통한 다양한 기능 확장이 가능
    - 사용자는 별도 회원가입 없이 곡 추천, 플레이리스트 연동 등 고급 기능을 바로 이용 가능

---

✅ 기능 2. `온보딩 시스템`
- **기획 의도 및 구현 방법**
    - 사용자 임베딩이 존재하지 않는 신규 유저를 위한 최초 1회 진행 온보딩 기능
    - 가게 분위기를 표현하는 태그를 사용자가 선택하면, 해당 태그와 연관된 곡 중 20곡을 선별
    - 이 중 2곡씩 총 10세트로 제시하고, 각 세트마다 1곡을 선택
    - 사용자가 선택한 10곡의 임베딩 평균값을 이용해 신규 사용자 임베딩 생성
- **주요 코드 구조 또는 API 설계 내용**
    - `POST /onboarding` : 사용자가 선택한 분위기 태그를 저장하고, 해당 태그에 맞는 후보곡 20곡을 반환
- **기능 구현 과정에서 고려한 점**
    - 정확한 임베딩 생성을 위해 태그별로 상호작용 데이터가 풍부한 곡들을 우선적으로 선별
    - 같은 태그 요청이 반복될 가능성이 높아, Redis 캐싱을 통해 응답 속도 최적화
- **기능 적용 후 기대 효과**
    - 음원 상호작용 이력이 없는 신규 유저도 즉시 추천 시스템을 이용할 수 있는 사용자 임베딩 생성 가능
    - 사용자 초기 경험을 자연스럽게 설계함으로써 서비스 진입 허들을 낮춤

---

✅ 기능 3. `사용자 플레이리스트 선택`
- **기획 의도 및 구현 방법**
    - 사용자 취향을 정교하게 반영하기 위해, 사용자 보유 플레이리스트의 음원 정보와 추천 곡 간 유사도를 기반으로 추천 결과를 정렬
    - 사용자의 상황에 따라 두 가지 방식 중 하나를 선택하여 플레이리스트 정보를 등록할 수 있도록 구성

▶ 방법 1. Spotify 연동
- **주요 코드 구조 또는 API 설계 내용**
    - `GET /users/{user_id}/playlists` : 사용자가 Spotify에 보유 중인 플레이리스트 목록 반환
- **기능 구현 과정에서 고려한 점**
    - 로그인 → 플레이리스트 조회로 이어지는 자연스러운 사용자 경험을 고려해 Spotify 연동 흐름 설계
    - Spotify 플레이리스트의 트랙 정보를 토대로 유사도 기반 정렬 가능하도록 데이터 연계 구성

▶ 방법 2. 이미지 OCR 업로드
- **주요 코드 구조 또는 API 설계 내용**
    - `POST /playlist/image` : 사용자가 업로드한 이미지에서 OCR을 통해 음원 목록 추출 후 반환
- **기능 구현 과정에서 고려한 점**
    - Upstage OCR API 활용 
    - OCR 인식률 한계를 보완하기 위해 사용자 검증 프로세스를 필수로 도입
    - 음원명과 아티스트명만 정확히 추출하기 위해 전·후처리 적용
        - 전처리: 이미지 업로드 시 예시 이미지를 제공하여 불필요한 정보 제거 유도
        - 후처리: OCR 결과에서 불용어 필터링 및 정규식 기반 텍스트 정제


- **기능 적용 후 기대 효과**
    - 다양한 방식의 플레이리스트 등록을 지원하여 사용자 접근성과 활용도 향상
    - 사용자 취향이 반영된 플레이리스트 기반의 유사도 정렬로 더 정확한 추천 결과 제공

---

✅ 기능 4. `개인화 음악 추천`
- **기획 의도 및 구현 방법**
    - 사용자 임베딩과 선택한 플레이리스트 트랙 정보를 함께 고려해 개인화된 음악 추천 제공
    - 사용자 임베딩은 사용자의 상호작용 이력을 반영하여 지속적으로 갱신됨
        - 신규 사용자는 온보딩 기반 선택 정보로 초기 임베딩 생성
        - 기존 사용자는 과거 추천 결과 중 선택한 곡 로그를 반영하여 임베딩 재생성
    - 선택한 플레이리스트의 트랙 메타 정보를 기반으로 추천 모델 API에 입력값 전달 → 추론 결과를 가공해 추천 결과 반환
- **주요 코드 구조 또는 API 설계 내용**
    - `GET /playlists/{playlist_id}/tracks` : Spotify 연동 플레이리스트 선택 시 트랙 목록과 사용자 임베딩을 기반으로 추천 결과 반환
    - `POST /playlist/image/tracks` : OCR로 추출한 트랙 목록과 사용자 임베딩을 기반으로 추천 결과 반환
- **기능 구현 과정에서 고려한 점**
    - 트랙 메타 정보가 DB에 없는 경우 Last.fm API 연동을 통해 보완
    - 추천 결과는 단순 모델 출력이 아닌, 사용자 입력에 대한 반응성이 느껴지도록 ‘유사도 기반 정렬’ 방식 적용
- **기능 적용 후 기대 효과**
    - 단순 인기 기반이 아닌, 사용자 취향을 반영한 맞춤형 추천 제공
    - 사용자 임베딩과 플레이리스트를 모두 반영하여 추천의 정확도 향상

---

✅ 기능 5. `추천 음악 플레이리스트에 추가`
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
- **모델 결과 반환 API 응답 속도 최적화**
    - 문제점: 추천 모델 API 응답 지연으로 사용자 경험 저하 우려
    - 해결 방법:
        - DB 쿼리를 기존 `EXISTS + ORDER BY`에서 `JOIN + IN` 연산자로 변경해 트랙명, 아티스트명 조회 최적화 (47% 속도 단축)
        - Python 코드 내에서 정렬 처리로 DB 부하 감소
        - 외부 API 호출을 `asyncio.gather()`로 비동기 처리해 61% 추가 단축
    - 최종 성과: 초기 대비 79% 응답 속도 단축으로 서비스 체감 성능 크게 개선
- **OCR 인식 최적화 및 음원 매칭 문제 해결**
    - 문제점:
        - 플레이리스트 캡처 이미지에서 트랙명/아티스트명이 길어 ‘…’으로 생략되어 데이터베이스와 정확한 매칭 어려움
        - OCR 결과에 동영상, 불용어 등 인식 오류 포함
    - 해결 방법:
        - ‘…’ 생략 부분을 퍼센트(%) 와일드카드로 변환해 SQL `LIKE` 검색 적용
        - difflib 라이브러리로 텍스트 유사도 계산, 60% 이상일 경우 동일 음원으로 판단
        - 정규표현식으로 불용어 필터링 및 사전 제외 단어 리스트 관리
        - 사용자 직접 검증 프로세스를 추가해 최종 음원 확정
    - 결과: OCR 인식 오류를 효과적으로 보완해 사용자 경험과 데이터 정확도 향상
