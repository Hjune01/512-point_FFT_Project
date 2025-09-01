# FFT Fixed-Point Project  
**Team 8 | 대한상공회의소 AI 시스템반도체 설계 2기**  
김진수 · 권혁진 · 양현준 · 송유경  

---

## 📌 프로젝트 개요  
**목표**: 512-point FFT 구조 RTL 구현 및 FPGA 합성  

**핵심 기술**  
- **Butterfly 구조**: FFT 기본 연산 블록 (합/차 및 Twiddle Factor 곱)  
- **CBFP (Convergent Block Floating Point)** 적용  
- **동적 스케일링**으로 고정 소수점 정밀도 손실 최소화  
- **SQNR +16 dB 향상** → FPGA/DSP 환경에서 효율적  

---

## 🔧 구현 구조  
- 단계별 **Shift Register → Butterfly → Twiddle 모듈 파이프라인화**  
- **RTL Simulation → Gate Simulation → FPGA Synthesis → Timing 검증**  
- MATLAB 결과와 RTL 결과 정합성 확인  

---

## ⚡ Trouble Shooting  
- **Unconnected 신호** → 와이어 초기화 추가  
- **Glitch 문제** → 조합/순차 논리 분리  
- **Latch 생성** → 모든 조건에 `else` 추가  
- **Timing mismatch** → Butterfly와 Twiddle 간 **1 CLK Delay** 삽입  

---

## 🖥️ FPGA Synthesis 결과  
- DSP 사용률 **22%** (곱셈/덧셈 연산 집중)  
- **Setup/Hold 타이밍 만족**  
- 데이터 소실 문제 해결 완료  

---

## ✅ 결론  
- **512-point FFT RTL 구현 및 FPGA 합성 성공**  
- CBFP 적용으로 **Bit Growth 제어 & SQNR 개선**  
- **MATLAB ↔ Verilog 결과 일치** 확인  
- FPGA 합성/검증 단계에서 **Timing 문제 해결**  

---

## 💡 고찰  
- 파이프라인 설계의 핵심은 **데이터 흐름 제어보다 valid 신호 동기화**  
- 시뮬레이션 기반 디버깅으로 **정확한 오류 추적 가능**  
- 팀 프로젝트에서는 **속도보다 공동 이해 & 협업**이 성과로 이어짐  
