# proposal_01

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

