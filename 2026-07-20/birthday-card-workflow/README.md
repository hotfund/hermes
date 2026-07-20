# 더깨비 생일축하카드 자동 생성 + 카카오톡 전송 워크플로우

**작업일시:** 2026-07-20 (일)
**대상:** 내일(7/21) 생일 820/888 포함자 2명

## 완료: 김도형888더금융서비스 대표 ✅

### 실행 순서 (cua-driver CLI)

1. **더깨비 크롬 창 bring_to_front**
2. **"어떤주제?" → "🎂 생일 축하"** 클릭
3. **"분위기" → "고객이름 3행시 + 건배사"** 클릭
4. **"받는 사람 (고객) 이름"** 입력란에 "김도형" 입력 (클립보드 Ctrl+V)
5. **"🎉 이름넣고 건배사 3행시 짓기"** 버튼 클릭
6. **8초 대기** → 3행시 결과 확인: "김이 모락모락 케이크에 / 도란도란 모여 축하해 / 형님 생일 최고, 위하여!"
7. **"메시지 칸에 넣기"** 버튼 클릭
8. **아래로 스크롤 → "🖼 이미지 만들기"** 버튼 클릭
9. **12초 대기** → 카드 이미지 생성 완료
10. **"카카오톡"** 버튼 클릭 → 링크 클립보드 복사
11. **카카오톡 전환** → 친구 검색 "김도형888" → 채팅창 열기
12. **채팅 입력란에 Ctrl+V** → 링크 붙여넣기
13. **최종 보내기 버튼은 교수님이 직접 누름**

## 미완료: 김윤정820영진에셋부천 ⬜

### 핵심 명령어 패턴

```bash
export PATH="$PATH:/c/Users/USER/AppData/Local/Programs/Cua/cua-driver/bin"

# 클립보드에 텍스트 복사
powershell.exe -NoProfile -Command "Set-Clipboard -Value '이름'"

# 입력란 더블클릭 → Ctrl+A → Ctrl+V
echo '{"pid":PID,"window_id":WID,"x":X,"y":Y}' | cua-driver.exe call double_click
echo '{"pid":PID,"keys":["ctrl","a"],"delivery_mode":"foreground"}' | cua-driver.exe call hotkey
echo '{"pid":PID,"keys":["ctrl","v"],"delivery_mode":"foreground"}' | cua-driver.exe call hotkey

# 카카오톡 친구 검색 (Ctrl+Shift+F 통합검색)
echo '{"pid":16660,"keys":["ctrl","shift","f"],"delivery_mode":"foreground"}' | cua-driver.exe call hotkey
```

## Pitfalls

1. **"메시지 칸에 넣기" 클릭 실패** → 메시지 비어있으면 "이미지 만들기" 에러남. 현재 더깨비 버그로 교수님이 수정 예정.
2. **카카오톡 포그라운드 전환 실패** → Alt+Tab → bring_to_front 순서로 해결
3. **Ctrl+V가 안 먹힐 때** → 입력란 double_click → Ctrl+A → Ctrl+V 순서
4. **더깨비 "카카오톡" 버튼** → 링크가 클립보드에 복사됨. 카톡 검색으로 덮어쓸 수 있으니 순서 주의.
