# proposal_01

Type A. [개념도] 사용자 정의형 파이프라인 (High-Level Concept)
목적: "레고 블록처럼 조립한다"는 핵심 컨셉을 직관적으로 보여주기 위함 (제안서 앞부분용) 핵심 키워드: Input → Block Assembly → Output

```mermaid
sequenceDiagram
    participant Sensor as 현장 센서 (Data)
    participant Engine as 추론 엔진 (Inference)
    participant Operator as 관리자/작업자 (Human)
    participant Tuner as 오토 튜너 (Optimizer)

    Sensor->>Engine: 1. 실시간 데이터 전송 (이미지+소음)
    Engine->>Engine: 2. 멀티모달 융합 분석
    Engine->>Operator: 3. 결과 판정 (불량 의심 / 정확도 85%)
    
    alt 판정 정확 (Correct)
        Operator-->>Engine: 확인 (Confirm)
    else 판정 오류 (Incorrect)
        Operator->>Tuner: 4. 피드백 전송 (오탐지 신고)
        Tuner->>Tuner: 5. 파라미터 재조정 (Threshold 변경)
        Tuner->>Engine: 6. 최적화된 설정값 배포 (Update)
    end
    
    Engine->>Engine: 7. 성능 향상 (정확도 95% 도달)
```

Type B. [상세 구조도] 시스템 아키텍처 (System Architecture)
목적: 기술적 깊이와 구성 요소(MSA, Docker 등)를 보여주기 위함 (기술 부문용) 구조: 4-Tier Layer (인프라 - 코어 - 서비스 - 유저)
```mermaid
graph LR
    subgraph "1. Multi-Modal Input"
        A1[Vision<br>Camera/CCTV]
        A2[Audio<br>Mic/Sensor]
        A3[Text/Log<br>PLC/Server]
    end

    subgraph "2. Hyper Inference Pipeline (User-Defined)"
        direction TB
        B1[("Data Ingestion<br>(전처리/동기화)")] --> B2{{"Model Selection<br>(YOLO/BERT/Whisper)"}}
        B2 --> B3["Ensemble Logic<br>(모델 결합/가중치)"]
        B3 --> B4["Post-Processing<br>(임계값 필터링)"]
        
        style B2 fill:#f9f,stroke:#333,stroke-width:4px
    end

    subgraph "3. Optimized Output"
        C1[Dashboard<br>모니터링]
        C2[Control Signal<br>설비 제어]
        C3[Alert<br>담당자 알림]
    end

    A1 --> B1
    A2 --> B1
    A3 --> B1
    B4 --> C1
    B4 --> C2
    B4 --> C3
```

Type C. [프로세스] 자율 최적화 데이터 흐름도 (Process Flow)
목적: "어떻게 스스로 똑똑해지는가?"(Auto-Tuning)를 설명하기 위함 핵심: Feedback Loop (순환 구조)

```mermaid
sequenceDiagram
    participant Sensor as 현장 센서 (Data)
    participant Engine as 추론 엔진 (Inference)
    participant Operator as 관리자/작업자 (Human)
    participant Tuner as 오토 튜너 (Optimizer)

    Sensor->>Engine: 1. 실시간 데이터 전송 (이미지+소음)
    Engine->>Engine: 2. 멀티모달 융합 분석
    Engine->>Operator: 3. 결과 판정 (불량 의심 / 정확도 85%)
    
    alt 판정 정확 (Correct)
        Operator-->>Engine: 확인 (Confirm)
    else 판정 오류 (Incorrect)
        Operator->>Tuner: 4. 피드백 전송 (오탐지 신고)
        Tuner->>Tuner: 5. 파라미터 재조정 (Threshold 변경)
        Tuner->>Engine: 6. 최적화된 설정값 배포 (Update)
    end
    
    Engine->>Engine: 7. 성능 향상 (정확도 95% 도달)
```
