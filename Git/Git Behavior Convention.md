# Git Behavior Convention

## Commit message
 - 커밋 메시지는 한글로 작성합니다.
 - 커밋의 단위는 ***+50/-50***이 가장 이상적입니다.
 - 커밋시에는 ```git commit``` 대신 ```git cz``` 명령어를 사용합니다.
## Git commitizen 설치방법

1. npm이 설치되지 않았다면, [Node.js](https://nodejs.org/en) 를 설치합니다.
2. 커맨드라인 창을 열고 다음을 입력합니다.
   ```cmd
   npm install -g commitizen
   npm install -g cz-conventional-changelog
   npm install -g cz-emoji-conventional cz-emoji
   echo '{ "path": "cz-emoji-conventional" }' > ~/.czrc
   ```

## Git commitizen 사용방법
1. 변경 사항을 ```git add``` 명령어로 추가 한 후, ```git cz```를 commit 대신 사용합니다. <br><br>
2. ``` Select the type of change that you're committing:```
   - 방향키 ```위```, ```아래``` 버튼을 사용하여 작업 타입을 입력합니다. <br><br>
3. ```What is the scope of this change```
   - 변경된 파일에 대해 입력합니다. 만약 작업 파일이 여러개인 경우 가장 대표적인 파일 하나를 지정합니다. <br><br>
4. ```Write a short, imperative tense description of the change```
   - 간략하게 어떤 변경이 있었는지를 작성합니다.
   - 이때 가능한 명확하게 작성합니다.
   - ex)
     - ```glb 파일을 불러오기 위한 경로를 기존 일반 string에서 Path.Combine을 사용해 불러오도록 수정```
     - ```이미지를 로드하는 중 NullPointException으로 인해 강제종료되는 버그 수정``` <br><br>  
			  
5. ```Provide a longer description of the change: ```는 생략합니다. <br><br>
  
6. ```Are there any breaking changes?```
   - 이는 소프트웨어에 잠재적인 오류를 일으킬 수 있는 부분이 있는지 물어보는 질문입니다. 웬만하면 ```n```을 입력합니다. (만약 그런 문제가 있다면 커밋과 푸시를 안하는게 이상적입니다.) <br><br>
        
7. ```Does this change affect any open issues?```
    - 만일 프로젝트에서 ```깃허브 이슈```를 등록, 관리하고 있다면 ```y```를 입력 후 ***해당 이슈의 번호***를 입력합니다. 아니라면 ```n```을 입력합니다.<br><br>
  
8. 여기까지 진행했다면, 다음과 같은 형식의 커밋 로그를 확인할 수 있습니다.
   ![image](https://github.com/portal301/NOTICE-Portal-Naming-Convention/assets/5483768/974bf870-7ec3-48bc-8be9-f7434307d1a6)

## Branches
브랜치 관리는 협업 중 변경사항을 추적하고 관리하는 데 매우 유용한 도구입니다. 이를 통해 개발자들은 독립적으로 작업을 진행할 수 있으며, 서로의 작업에 영향을 주지 않고 병렬로 개발을 진행할 수 있습니다. 또한, 브랜치를 사용하면 각 작업의 변경사항을 명확하게 구분하고 관리할 수 있어, 프로젝트의 복잡성을 효과적으로 줄일 수 있습니다.

코드리뷰는 코드 퀄리티를 보장하는 데 중요한 역할을 합니다. 브랜치를 통해 개발된 코드는 병합 전에 반드시 코드리뷰를 거치게 함으로써, 코드의 오류를 사전에 발견하고 수정할 수 있습니다. 또한, 코드리뷰 과정은 팀원 간의 지식 공유와 협력을 촉진하여, 전체적인 코드 퀄리티를 향상시킵니다.
이와 같은 브랜치 전략과 코드리뷰 과정은 협업의 효율성을 높이고, 프로젝트의 안정성과 품질을 보장하는 데 있어 필수적인 요소입니다. 이러한 접근 방식은 조직 내 개발 프로세스를 체계화하고, 성공적인 프로젝트 수행을 지원합니다.

#### main
- Feature들이 병합되는 Base브랜치입니다.
- Base 브랜치를 항상 안정적인 상태로 유지하는 것은 매우 중요합니다. 이를 통해 치명적인 오류가 없는 코드 베이스를 보장할 수 있으며, 모든 팀원이 신뢰할 수 있는 기반을 제공받게 됩니다. 안정적인 Base 브랜치는 CI/CD를 통한 배포를 가능하게 하여, 제품의 품질과 신뢰성을 높이는 데 기여합니다.

#### Feature
새로운 Feature를 개발하기 전 *Feature-기능이름* 의 이름으로 브랜치 생성 후 작업합니다.
- 기능 이름에 띄어쓰기가 필요한 경우 -로 단어 구분합니다.
- 예시 Feature-UI-Implementation

Feature 개발 이후 `main` 브랜치로 Merge 합니다.
  - 2인 이상 개발 시 ```Pull Request``` 사용을 권장합니다.
  - ```Squash & Merge``` 방식 사용을 권장합니다.
    - Merge 이후 origin repository에서 해당 브랜치는 삭제합니다.
    - [Merge 방식 차이에 대해 읽어보면 좋은 글](https://blog.outsider.ne.kr/1704) 

## Pull Requests
[Portal301 PR 가이드라인](https://github.com/portal301/NOTICE-Portal-Project-Conventions/blob/main/Git/PR%20Convention.md)

## Issue 작성방법
- Github의 Issue는 버그 리포팅, 테스트 배포시 가이드등 여러가지 방법으로 사용될 수 있습니다.

### 예시 : Test
- 배포 전 테스트 단계에서 행해지는 테스트는 두가지로 나눌 수 있습니다.
  - 특정 Feature 별로 사용하는 **Task Test**: 이는 단 하나의 기능을 테스트합니다.
  - 통합 기능을 테스트하는 **Acceptance Test**: 이는 기능보다 더 큰 단위의 테스트입니다. ex) 특정 뷰 컴포넌트의 기능 등..
- Test 작성시에는 개발자가 아닌 사람이라도, Issue에 적힌 내용만 보고 쉽게 따라할 수 있도록 작성되어야합니다.
- 모든 단계는 전문용어가 아닌 ***Plain Language***로 작성되어야 합니다.
- Acceptance Test 작성시에는 Task Test를 포함한 종합적인 테스트 방법이 작성되어야 합니다.
  
#### Task Test 예시
![image](https://github.com/user-attachments/assets/717525e2-a6dd-4892-8e9a-962a9b497a17)


## Git commit log 간지나게 보는법
1. 커맨드 라인 툴에서 ```nano ~/.gitconfig```를 입력합니다. 다른 텍스트 편집기로 ```~/.gitconfig```를 수정하셔도 됩니다.
2. 다음 내용을 복사 후 붙여넣기 합니다.
	 ```
	[alias]
	lg1 = log --graph --abbrev-commit --decorate --format=format:'%C(bold blue)%h%C(reset) - %C(bold green)(%ar)%C(reset) %C(white)%s%C(reset) %C(dim white)- %an%C(reset)%C(auto)%d%C(reset)' --all
	lg2 = log --graph --abbrev-commit --decorate --format=format:'%C(bold blue)%h%C(reset) - %C(bold cyan)%aD%C(reset) %C(bold green)(%ar)%C(reset)%C(auto)%d%C(reset)%n''          %C(white)%s%C(reset) %C(dim white)- %an%C(reset)'
	lg = lg1
	```
3. 윈도우 기준 ```ctrl + x```를 눌러 저장합니다.
4. 프로젝트 폴더로 이동해 ```git lg```를 입력합니다.
5. 짜잔
   ![image](https://github.com/portal301/NOTICE-Portal-Naming-Convention/assets/5483768/a1056634-fb24-462f-91bb-908e454ff655)


