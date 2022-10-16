# Git Convention  2차 확정본

**팀원 모두는 Fork를 통해 작업합니다.**

---
### Issue

<aside>
💡 [이슈 작업 태그] 작업이 필요한 내용

</aside>

**Issue 작성 시 Label 설정**

- `작업 담당자`, `작업 태그` 설정

⭐️**Issue** **Template 사용**⭐️

- **이유**
    1. **개발하는 과정** 자체를 팀의 개발 관련 문서에 녹여내기 위하여
    2. ㅔㅔ메**작업 담당자** 스스로가 자신의 작업에 대한 이해도를 높이기 위해
    3. **코드 리뷰자**가 작업 자체에 대한 Background 이해도를 높이기 위해
- **Default Template**
    
    ```markdown
    ### 작업에 대한 간단한 설명
    - 작업 자체에 대한 간단한 요약 설명
    
    ### TODO
    - [ ] ~~ 작업
    - [ ] ~~ 작업
    - [ ] ~~ 작업
    
    ### 작업 일정(Optional)
    2022.00.00 - 2022.00.00 (작업일자)
    
    |작업일자|작업 내용|
    |:---:|:---:|
    |2022.00.00|SequenceNumber|
    
    ### Optional
    - 작업 전 숙지 사항
    
    ### 이슈 제안자(Optional)
    - @인물 멘션
    - 이슈 담당자 ≠ 작업 담당자의 케이스에 명시해주세요.
    ```
    
    - **이슈 작성자 = 작업 담당자**
        - 이슈 담당자 ≠ 작업 담당자의 케이스에는 이슈 작성자와 작업 담당자 명시
    - **작업 자체에 대한 기본적으로 ‘왜’ 해야하는지에 대해 생각하기 위한 과정**
- **Bug Template (NOT HOTFIX)**
    
    ```markdown
    ### 어떤 버그(에러)가 발생했나요?
    - 버그 자체에 대한 설명
    
    ### 버그 확인을 위한 Sequence 설명
    1. ~~를 한다.
    2. ~~를 한다.
    3. ~~를 한다.
    4. 어디서 ~~한 버그 발견
    (필요 시 스크린샷 첨부)
    
    ### 버그 발생 원인 추측
    - 버그가 발생한 원인에 대해 간략한 추측
    
    ### 버그 발생 기종 및 OS(Optional)
    - Device:
    - OS Version:
    (기종 혹은 OS 관련 버그가 아닌 경우 생략)
    
    ### 버그 최초 발견자
    - @인물 멘션
    
    ### 버그 FIX 담당자
    - @인물 멘션
    ```
    
    - 버그 발견자와 버그 해결 담당자가 같은 경우에도 명시
    - 버그 해결과 관련된 Issue는 따로 작성할 필요 X
    - 버그 해결에 관한 Branch의 작업 태그는 fix로
- **HOTFIX Template (NOT BUG)**
    
    ```markdown
    ### 어떤 버그(에러)가 발생했나요?
    - 버그 자체에 대한 설명
    
    ### 버그 해결 예상 소요 시간
    |현재 시각|예상 소요 시간|완료 시간|
    |:---:|:---:|:---:|
    |0000.00.00 PM(AM) 00:00|N시간N분|0000.00.00 PM(AM) 00:00|
    ```
    
    - **빠르게 해결해야하는 hotfix 작업 태그의 Issue의 경우에는, Issue를 작성하되 내부 구성요소를 최소한으로 들고갈 수 있도록 한다.**
    - **HOTFIX의 경우 요약본 PR로 1명의 Approve 후 Merge**

| FIX | 개발자의 실수, 혹은 디자인 변경, etc 여러가지 요인으로 인해 ‘수정’되어야하는 것들에 대한 작업 |
| --- | --- |
| BUG | 개발자가 예측하지 못한 오류. 단, ‘수정’되어야한다는 점에서는 FIX와 BUG 태그 둘 다 동일함 |

| Issue & Commit 작업태그 | Description |
| --- | --- |
| feat | 코드 추가 (UI 관련 Component 추가 포함), 기능 추가 |
| fix | 코드 수정(기존에 존재하던 기능 수정), 오타 수정 |
| hotfix | 급하게 해결되어야하는 버그 수정 |
| style | 코드 의미에 영향을 주지 않는 변경사항(코드 포맷팅, 오타 수정, 변수명 변경) |
| design | 디자인(UI) 관련 수정 |
| asset | 에셋 파일 추가 |
| doc | 프로젝트 자체에 대한 Document |
| comment | 코멘트 추가 |
| chore | 빌드 & 패키지 매니저 관련 추가 |
| refactor | 코드 리팩토링 (코드의 가독성 향상을 위한 코드 수정) |

---
### Branch (with Fork?)

- 가장 중심축이 되는 Branch는 `main`이지만, main Branch로 Merge하는 경우는 Testflight, Release etc의 작업물의 Version Upgrade를 하는 경우에만 해당한다.
- 개발의 중심축이 되는 Branch는 `develop`이다.
- 개발의 편리함을 위해 Default Branch는 `main`이 아닌 “`develop`"으로 설정한다
- `main`과 `develop`은 결코 삭제될 수 없다.
- 모든 Branch는 `develop` 이하에서 파생되어 만들어진다
- develop 이하에서 만들어진 Branch의 이름은 `{이슈작업태그}/{작업번호}`의 규칙을 따른다.
    - ex) feat/#24
- 작업을 마친 Branch는 Merge 후 **PR 올린 사람**이 삭제한다.

---
### Commit

<aside>
💡 [#이슈번호] 작업 태그 - 작업 내용

</aside>

| Issue & Commit 작업태그 | Description |
| --- | --- |
| feat | 코드 추가 (UI 관련 Component 추가 포함), 기능 추가 |
| fix | 코드 수정(기존에 존재하던 기능 수정), 오타 수정 |
| hotfix | 급하게 해결되어야하는 버그 수정 |
| style | 코드 의미에 영향을 주지 않는 변경사항(코드 포맷팅, 오타 수정, 변수명 변경) |
| design | 디자인(UI) 관련 수정 |
| asset | 에셋 파일 추가 |
| doc | 프로젝트 자체에 대한 Document |
| comment | 코멘트 추가 |
| chore | 빌드 & 패키지 매니저 관련 추가 |
| refactor | 코드 리팩토링 (코드의 가독성 향상을 위한 코드 수정) |
- 커밋은 최대한 쪼개서 작업한다.
- 각각의 커밋은 하나의 내용만을 담고있게 만든다.

---
### PR

- **PR Template**
    
    <aside>
    💡 [관련 이슈 작업 태그] #이슈번호 작업 내용 축약
    
    </aside>
    
    **PR 작성 시 Label 설정**
    
    - `작업 담당자`, `작업 태그` 설정
    
    ```markdown
    ### 작업 내용 설명
    1. ~~를 작업
    2. ~~를 작업
    3. ~~를 작업
    
    ### 관련 이슈
    - #이슈번호
    
    ### 작업의 결과물
    - 코드 or 스크린샷 or 동영상
    - 작업의 결과물이 따로 존재하지 않는 경우에는 기록 X
    
    ### 작업의 비고사항 및 한계점
    - 비고사항 및 한계점이 없다면 기록 X
    
    ### To Reviewers
    - 리뷰어에게 중점적으로 살펴봐줬으면 하는 내용
    
    Close #이슈번호
    ```
    
- 관련된 이슈가 PR Merge와 함께 닫혀야하는 경우 PR의 말미에 `Close #이슈번호` 를 작성한다.

---
### Review

**Review Request Sequence (PR 작성자 입장에서)**

1. Issue → Fork → Branch 생성? → 작업 완료
2. PR을 생성한다
3. PR을 작성했음을 카카오톡으로 알린다 (Slack 사용 시에는 Slack으로)
    
    PR #124 올렸습니다. (리뷰어 멘션)
    

**Review Sequence (코드 리뷰어의 입장에서)**

1. PR을 훑어본다.
2. PR을 훑어본 후, 추가적인 내용 확인이 필요한 경우 Issue를 확인한다.
3. 코드에 관한 리뷰 반영 우선 순위를 Review의 서두에 제시하며 코드 리뷰를 한다.
    
    **Review 상세**
    
    [코드 리뷰 in 뱅크샐러드 개발 문화 | 뱅크샐러드](https://blog.banksalad.com/tech/banksalad-code-review-culture/)
    
    p5;
    idx 대신 index를 쓰면 어떨까요?
    
    | Comment | 단순 코멘트. 칭찬 etc |
    | --- | --- |
    | Approve | p3 - p5의 리뷰만 존재하는 경우 |
    | Request Change | p1 - p2 리뷰가 하나라도 존재하는 경우 |
4. PR에 대한 리뷰를 작성했음을 카카오톡으로 알린다 (Slack 사용 시에는 Slack으로)
    
    PR #124 REVIEW 완료했습니다. (PR 담당자 멘션)
    
---
### Merge

1. Review 확인 후 피드백을 반영한다.
2. 반영된 부분을 Reply에서 commit id로 반영되었음을 알린다.
    
    > p5;
    idx 대신 index를 쓰면 어떨까요?
    
    - reply: 38bcd14 반영했습니다!
    > 
3. **2명 이상** Approve 시 **PR을 올린 사람이 Merge**
    - **단, p1 - p2 우선 순위를 지니는 변경 요청 사항이 없는지를 체크하고 없는 경우**
    - **단, PR이 develop에 Merge가 되어도 Conflict가 발생하지 않는 경우**
4. Merge 후 Branch를 삭제한다.
5. Merge되었음을 카카오톡으로 알린다 (Slack 사용 시에는 Slack으로)
    
    PR #124 Merge 완료했습니다
    
---
### Conflict

1. PR 시 발생한 Conflict는 1차적으로 PR 작성자가 먼저 해결을 가늠해본다.
2. Conflict 해결 도중 발생하는 문제가 걱정된다면 임시로 Conflict 해결을 테스트해보기 위한 Branch를 작성 후 Conflict를 해결해보자. 이 경우, 해당 Branch의 이름은 아래와 같다
    
    
    | 기존 Branch 이름 | 수정된 Branch 이름 |
    | --- | --- |
    | {이슈작업태그}/{작업번호}  | {이슈작업태그}/temp{작업번호} |
    | feat/#43 | feat/temp#43 |
3. PR 담당자가 Conflict 해결에 시간이 걸린다면 팀원들에게 알린 후, 해결에 걸리는 시간을 알려준다.
4. PR 담당자가 Conflict 해결이 어렵다고 생각되는 경우, 팀원들에게 알린다.
5. Conflict 해결 도중 예상치 못한 상황이 발생한 경우, 그 즉시 팀원들에게 알린다.

---

### Kanban

- **사용 X**
    - 깔끔한 Issue 관리를 한다면 Kanban을 사용하지 않기로 합의되었습니다.

### **Milestone**

- **사용 O**
    - Sprint의 목표점 설정 및 해야하는 일들을 List up을 하는 용도로 사용.
