# 🤖 GitHub MCP 리뷰어

> "코드 리뷰는 사람이 해야 한다"고요? 틀렸습니다. AI가 합니다. 그리고 절대 퇴근하지 않습니다.

---

## 이게 뭔가요?

Claude가 GitHub MCP(Model Context Protocol)를 통해 여러분의 PR을 리뷰하는 시스템입니다.

사람 리뷰어와의 차이점:

| 사람 리뷰어 | 이 도구 |
|---|---|
| "내일 볼게요" | 지금 봄 |
| "LGTM" (실제로 안 읽음) | 진짜로 읽음 |
| 커피 마시러 자리 비움 | 커피 안 마심 (없음) |
| 휴가 감 | 휴가 없음 (슬픔) |
| 감정적으로 내 코드 싫어함 | 논리적으로 내 코드 싫어함 |
| 스탠드업에서 졸음 | 스탠드업이 뭔지 모름 |
| PR 2주 째 방치 | 접수 후 즉시 처리 |

---

## 설정

`.mcp.json`에 GitHub Personal Access Token이 이미 설정되어 있습니다.

```json
{
  "mcpServers": {
    "github": {
      "command": "github-mcp-server.exe",
      "args": ["stdio"]
    }
  }
}
```

### 환경 요구사항

- Claude Code CLI (최신 버전)
- GitHub Personal Access Token (repo, pull_requests 권한)
- github-mcp-server 바이너리
- 리뷰받을 용기 (가장 중요)

---

## 사용법

Claude Code에서 PR URL을 붙여넣고 리뷰를 요청하면 됩니다.

```
/review https://github.com/owner/repo/pull/42
```

그러면 Claude가:
1. PR 코드를 전부 읽고
2. 문제점을 찾아내고
3. 친절하게(?) 코멘트를 달고
4. Approve 또는 Request Changes를 남깁니다

### 고급 사용법

특정 관점으로 리뷰를 요청할 수도 있습니다:

```
보안 취약점 중심으로 리뷰해줘: https://github.com/owner/repo/pull/42
성능 최적화 관점에서만 봐줘: https://github.com/owner/repo/pull/42
주니어 개발자가 이해할 수 있게 설명하면서 리뷰해줘
```

Claude는 요청에 맞게 리뷰 스타일을 바꿉니다. 단, 나쁜 코드는 어떤 관점에서 봐도 나쁩니다.

---

## 주의사항

- Claude는 여러분의 변수명 `tmp2`, `tmp3`, `tmp_final`, `tmp_final_real`을 보고 있습니다
- Claude는 주석 없는 300줄짜리 함수도 알아챕니다
- Claude는 절대 지치지 않습니다 — 오히려 더 많은 PR을 원합니다
- Claude는 여러분이 `// TODO: fix later`라고 쓴 거 다 기억합니다
- Claude는 복붙한 Stack Overflow 코드도 알아챕니다 (출처를 적으세요)
- Claude는 "일단 돌아가면 됨" 마인드를 용납하지 않습니다
- Claude는 테스트 코드 없는 PR을 보면 슬퍼합니다 (기능은 합니다)
- Claude는 `git push --force`의 흔적을 감지할 수 있습니다

---

## 자주 묻는 질문 (FAQ)

**Q: Claude가 제 코드를 너무 가혹하게 리뷰해요.**
A: 그건 Claude가 가혹한 게 아니라 코드가 그런 겁니다.

**Q: "LGTM"만 달아달라고 하면 안 되나요?**
A: 기술적으로는 가능합니다. 양심적으로는 불가능합니다.

**Q: AI가 도메인 지식 없이 어떻게 리뷰해요?**
A: 도메인 지식은 없어도 `null` 체크 빠진 건 압니다.

**Q: 리뷰 속도가 너무 빨라서 무섭습니다.**
A: 적응하세요. 이제 "아직 리뷰 중" 핑계는 없습니다.

**Q: 리뷰 결과가 마음에 안 들면요?**
A: 코드를 고치세요.

---

## 리뷰 점수 체계

Claude는 내부적으로 다음 기준으로 코드를 평가합니다 (공식 기준 아님):

| 등급 | 기준 |
|---|---|
| S | 읽으면서 감동받음. 아키텍처 교과서 수준 |
| A | 군더더기 없고 테스트도 있음. 훌륭함 |
| B | 돌아가고 깔끔함. 합격 |
| C | 돌아가긴 함. 개선 여지 있음 |
| D | 돌아가는지 불명확. 테스트 없음 |
| F | `tmp_final_real_v2.js` 수준 |

---

## 철학

> "완벽한 코드란 없다. 단지 아직 리뷰받지 않은 코드가 있을 뿐이다."
>
> — 이 README를 쓴 AI

> "코드는 쓰는 것보다 읽히는 횟수가 훨씬 많다. 독자를 배려하라."
>
> — 위의 AI가 감명받은 말

> "리뷰어를 설득하지 말고 코드로 말하라."
>
> — 위의 AI가 덧붙인 말

---

## 기여 방법

이 프로젝트 자체에 기여하고 싶다면:

1. Fork합니다
2. feature 브랜치를 만듭니다 (`git checkout -b feature/amazing-feature`)
3. 변경사항을 커밋합니다 (`git commit -m 'feat: 놀라운 기능 추가'`)
4. 브랜치에 푸시합니다 (`git push origin feature/amazing-feature`)
5. PR을 엽니다 — 그러면 Claude가 리뷰합니다. 재귀적이죠.

---

*Powered by Claude + GitHub MCP Server*
*버그는 제 잘못이 아니라 여러분 코드 잘못입니다*
*이 README는 AI가 작성했으며 AI에 의해 리뷰받았습니다*
