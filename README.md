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

---

## 주의사항

- Claude는 여러분의 변수명 `tmp2`, `tmp3`, `tmp_final`, `tmp_final_real`을 보고 있습니다
- Claude는 주석 없는 300줄짜리 함수도 알아챕니다
- Claude는 절대 지치지 않습니다 — 오히려 더 많은 PR을 원합니다
- Claude는 여러분이 `// TODO: fix later`라고 쓴 거 다 기억합니다

---

## 철학

> "완벽한 코드란 없다. 단지 아직 리뷰받지 않은 코드가 있을 뿐이다."
>
> — 이 README를 쓴 AI

---

*Powered by Claude + GitHub MCP Server*
*버그는 제 잘못이 아니라 여러분 코드 잘못입니다*
