# SSU Datathon 2025: Semiconductor Technology Trend Analysis

### Uncovering the Future of Semiconductors: A Data-Driven Trend Analysis of 60,000+ Research Papers.
This repository contains the data analysis pipelines, weekly progress records, and final deliverables developed by Team **신전탐험대** for the SSU Datathon 2025. We leverage domain-specific engineering knowledge to decipher large-scale academic publication trends.

---

## 1. Project Overview (프로젝트 개요)

### 1.1 데이터 선정 배경: 왜 '반도체'인가?
* **기술 패러다임의 급변:** 현대 첨단 산업의 핵심인 반도체 기술은 무어의 법칙(Moore's Law) 한계 직면과 AI 반도체 등장으로 인해 연구 패러다임이 가장 빠르게 변화하는 분야입니다.
* **데이터 정제의 필요성:** 6만 건의 대규모 공학 논문 데이터 속에서 단순 검색으로는 노이즈가 너무 많아 기술 트렌드를 정확히 읽기 어렵습니다. 이에 전공 지식을 결합한 고도화된 정제 기법을 적용하여 실제 반도체 R&D의 핵심 줄기를 파악하고자 했습니다.

### 1.2 팀 구성 및 역할 분담 (Team Structure)
신소재공학 전공자와 전기공학 전공자의 융합 연구를 통해 반도체 생태계의 양대 축인 공정과 회로 분야를 전문적으로 분석했습니다.

* **공정팀 (Process Team):** 신소재공학 전공자가 주도하여 포토공정(Photolithography) 및 첨단 패키징(Advanced Packaging) 분야를 담당했습니다. 도메인 지식을 바탕으로 기존 공정 분류 체계의 오탐지 문제를 해결하고 필터링 로직을 설계했습니다.
* **회로팀 (Circuit Team):** 전기공학 전공자가 주도하여 AI 특화 회로(PIM/CIM), Mixed-Signal RF, 인터페이스 분야를 분석했습니다. 데이터 타겟팅 검증 및 설계 파라미터 트렌드를 정량 분석했습니다.

---

## 2. Weekly Activity Logs (주차별 활동 보고서)

| 주차 | 주요 활동 내용 | 활동 보고서 |
| :--- | :--- | :--- |
| **1주차** | 데이터 탐색, 연구 주제 구체화 및 방향성 설정 | [보기](데이터톤 1주차 활동보고서.pdf) |
| **2주차** | 데이터 전처리 및 1차 필터링 파이프라인 구축 | [보기](2주차_활동보고서(신전탐험대).pdf) |
| **3주차** | 다층 키워드 필터링(Multi-layer) 알고리즘 적용 | [보기](3주차_활동보고서(신전탐험대).pdf) |
| **4주차** | 데이터 시각화 및 도메인 정량 분석 | [보기](4주차_활동보고서(신전탐험대).pdf) |
| **5주차** | 기술 패러다임 해석 및 최종 성과물 작성 | [보기](5주차_활동보고서(신전탐험대).pdf) |

---

## 3. Core Code Explanation (핵심 코드 설명)

대규모 논문 데이터에서 반도체 분야의 의미 있는 데이터만 정밀하게 추출하기 위해 파이썬 기반의 다층 키워드 필터링 파이프라인을 구현했습니다.

```python
def filter_semiconductor_data(dataframe):
    # 1. 반도체 공정/회로 필수 포함 키워드 정의
    inclusion_keywords = ['photolithography', 'packaging', 'PIM', 'CIM', 'heterogeneous integration']
    
    # 2. 오탐지를 방지하기 위한 제외 키워드 정의 (노이즈 제거)
    exclusion_keywords = ['bio-sensor', 'chemical-test', 'environmental']
    
    # 3. 다층 필터링 적용
    filtered_df = dataframe[dataframe['abstract'].str.contains('|'.join(inclusion_keywords), case=False, na=False)]
    final_df = filtered_df[~filtered_df['abstract'].str.contains('|'.join(exclusion_keywords), case=False, na=False)]
    
    return final_df
```

## 4. Final Deliverables (최종 결과물)
최종 발표 성과물 (PPT/PDF): 5주간의 분석 데이터, 시각화 그래프, 공학적 트렌드 해석이 담긴 최종 발표 자료입니다.
[보기](최종 성과물(신전탐험대).pdf)

