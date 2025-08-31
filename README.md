# 🎶 Bad Apple!! — 540fps 8K Upscale Project

[download](https://github.com/dxdxffgg99/badapple.540fps/releases/tag/v1.0)

이 저장소는 **Bad Apple!!** 영상을  
👉 **540fps**, **8K 해상도**, **HEVC(H.265)** 로 업스케일링한 결과물을 담고 있습니다.

---

## 📽️ 프로젝트 개요
- 원본: badapple 
- 프레임 수: 약 **118,151** (540fps 기준, 약 3분 39초)  
- 출력 해상도: **1920 × 1080 (FHD)**  
- 최종 인코딩: **HEVC (H.265)**  
- 오디오: 원본에서 추출하여 합성

---

## 🛠️ 실행 방법

### 1. 의존성
- [FFmpeg](https://ffmpeg.org/)  
- NVIDIA GPU (예: RTX 4060) 또는 CPU  

# 프레임 추출
ffmpeg -i badapple.mp4 -vf "fps=540,format=rgb24" in_frames/%08d.png

# 합성 (영상+오디오)
ffmpeg -r 540 -i out_frames/%08d.png -i badapple.mp4 -map 0:v:0 -map 1:a:0 -c:v hevc_nvenc -cq 19 -preset p5 -pix_fmt p010le -c:a copy output_hevc_audio.mp4

📂 결과물
output_hevc_audio.mp4 → 최종 FHD 540fps HEVC 영상

GitHub LFS 또는 Release 첨부로 배포

⚠️ 주의
프레임 수가 많아 (11만+) 진행률이 천천히 올라갑니다.

540fps는 테스트/연구 목적입니다. 일반 재생기에서는 정상 재생이 어려울 수 있습니다.

📜 License
원본 Bad Apple!! 영상은 원작자에게 저작권이 있습니다.
본 프로젝트는 기술적 연구 및 팬 프로젝트 목적으로만 공유합니다.
