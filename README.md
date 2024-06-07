# Portal301 Project Repository Namaing convention

Portal Project는 다음과 같은 Naming Convention을 따릅니다.
<img src="nameing-convention.png">

기본적으로 소문자를 지향하며 프로덕트 이름의 경우에는 대문자도 자유롭게 허용    
## 예시    
### Synchro-TR.gui.electron    
### Synchro-TR.robot.py    
### Synchro-TR.tracker.unity    

<br>

# Project Code/Git Behavior Convention

## Objective
브랜치 관리와 컨벤션 통일을 통한 협업 방식은 팀 협업을 위한 중요한 규칙이지만, 모든 프로젝트에서 이를 100% 동일하게 적용할 필요는 없습니다. 각 프로젝트는 고유한 요구사항과 상황을 가지고 있으며, 이러한 규칙은 프로젝트의 특성과 팀의 필요에 따라 유연하게 조정될 수 있습니다.

따라서, 아래에 명시된 Code/Git Behavior Convention은 프로젝트의 참여자들 간의 합의를 통해 변경될 수 있습니다. 프로젝트 팀은 협의를 통해 최적의 방식을 찾아나갈 수 있으며, 이를 통해 프로젝트의 효율성과 효과성을 극대화할 수 있습니다. 예를 들어, 일부 프로젝트에서는 특정 브랜치 정책이 더 효과적일 수 있으며, 다른 프로젝트에서는 보다 간단한 코드리뷰 절차가 적합할 수 있습니다.

결론적으로, 이 문서는 협업을 위한 가장 기본적인 형태의 작업 약속을 지정해둔 문서입니다. 이 문서는 프로젝트 팀이 효율적이고 원활하게 협력할 수 있는 기본 틀을 제공하며, 이를 통해 프로젝트의 성공적인 수행을 지원하고자 합니다.

## Code Convention
코드 컨벤션은 기본적으로 해당 언어에서 권장하는 표준 컨벤션을 준수합니다. 이를 통해 코드의 일관성과 가독성을 유지하며, 팀원 간의 협업을 원활하게 만듭니다. 각 언어는 자체적으로 권장하는 스타일 가이드와 베스트 프랙티스를 가지고 있으며, 이러한 가이드를 따르는 것은 코드 품질을 향상시키고 유지보수성을 높이는 데 중요한 역할을 합니다.

### 각 언어별 코드컨벤션 

#### [Javascript/TypeScript](https://www.w3schools.com/js/js_conventions.asp)

#### [Python](https://peps.python.org/pep-0008)

#### [C# / Unity](https://learn.microsoft.com/ko-kr/dotnet/csharp/fundamentals/coding-style/coding-conventions)

### 그 밖에 협업을 위한 코드컨벤션
- ```Typescript``` / ```Swift``` / ```Python``` / ```C#```과 같이 타입을 명시하지 않아도 되는 언어 사용시에도 타입을 꼭 명시합니다.
  #### ❌
  ``` C#
    async void Awake()
    {
        var relativePath = SyncRoURIs.UR5e_BASE;
        var absolutePath = PathUtils.GetAbsoluteUri(relativePath);

        var gltfImport = new GltfImport();
        await gltfImport.Load(absolutePath);
        var settings = new InstantiationSettings
        {
            Layer = 3
        };

        var instantiator = new GameObjectInstantiator(gltfImport, gameObject.transform, null, settings);
        await gltfImport.InstantiateMainSceneAsync(instantiator);
    }
  ```
  #### ⭕
  ``` C#
    async void Awake()
    {
        string relativePath = SyncRoURIs.UR5e_BASE;
        string absolutePath = PathUtils.GetAbsoluteUri(relativePath);

        GltfImport gltfImport = new GltfImport();
        await gltfImport.Load(absolutePath);
        InstantiationSettings settings = new InstantiationSettings
        {
            Layer = 3
        };

        GameObjectInstantiator instantiator = new GameObjectInstantiator(gltfImport, gameObject.transform, null, settings);
        await gltfImport.InstantiateMainSceneAsync(instantiator);
    }
  ```
- 사용하지 않는 코드는 원격 리포지토리에 푸쉬할때 제외합니다.
  #### ❌
  ```
    //int Fibonacci(int n)
    //{
    //    if (n <= 1)
    //       return n;
    //    return Fibonacci(n - 1) + Fibonacci(n - 2);
    //}
  ```
- 사용하지 않는 헤더파일은 푸쉬할때 제외합니다.

## Git
### Commit message
 - 커밋 메시지는 한글로 작성합니다.
 - 커밋의 단위는 ***+50/-50***이 가장 이상적입니다.
 - 커밋시에는 ```git commit``` 대신 ```git cz``` 명령어를 사용합니다.
### Git commitizen 설치방법

1. npm이 설치되지 않았다면, [Node.js](https://nodejs.org/en) 를 설치합니다.
2. 커맨드라인 창을 열고 다음을 입력합니다.
   ```cmd
   npm install -g commitizen
   npm install -g cz-conventional-changelog
   npm install -g cz-emoji-conventional cz-emoji
   echo '{ "path": "cz-emoji-conventional" }' > ~/.czrc
   ```

### Git commitizen 사용방법
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

<hr>

### Branches
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
<hr>

### Pull Request 가이드라인
#### 개요
Pull Request는 협업 개발 환경에서 코드 변경 사항을 제안하고 리뷰하는 중요한 도구입니다. 개발자가 새로운 기능을 추가하거나 버그를 수정한 후, 자신의 브랜치에서 작업을 완료하면, Pull Request를 통해 변경 사항을 메인 브랜치에 병합할 것을 요청합니다. 이 과정에서 팀원들은 제안된 변경 사항을 검토하고, 코드의 품질을 보장하며, 잠재적인 문제를 발견할 수 있습니다. 코드 리뷰어들은 피드백을 제공하고, 필요한 경우 추가 수정 사항을 요청합니다. 이러한 절차를 통해 코드의 안정성과 일관성을 유지하고, 협업 개발의 효율성을 높일 수 있습니다.
#### 사용 방법
- Pull Request의 작업 단위는 빌드 파일의 변화를 제외하고 ***+500/-500***을 넘지 않는것이 이상적입니다.
- 너무 많은 양의 코드 리뷰 요청은 리뷰어가 이해하기 힘들뿐더러, 리뷰의 질적 하락을 야기할 수 있습니다.

##### 등록
1. Branch의 Feature 작업이 완료되면, 작업 Repo 페이지에 접속하여 상단의 Pull Request를 클릭합니다.
   ![image](https://github.com/portal301/NOTICE-Portal-Naming-Convention/assets/5483768/1078cfb9-7b95-4576-b398-176cd77662c1)
2. 병합될 브랜치를 ```Comparing Branch```로 설정하고, 병합의 목적지가 될 브랜치를 ```Base Branch```에 설정합니다. 이후 ```Create Pull Request``` 버튼을 클릭합니다.
   ![image](https://github.com/portal301/NOTICE-Portal-Naming-Convention/assets/5483768/2201570b-9095-4c97-bfba-b3a181ee274f)
3. 제목에 간략한 Feature의 목적을 작성후(1)
4. ```Reviewer```에 코드 리뷰를 해줄 담당자를 등록합니다.(2)
5. ```Assignee```에는 해당 브랜치에 작업을 한 사람을 지정합니다.(3)
6. 이후 작업 내용에 대해 적습니다.(4)  
   ![image](https://github.com/portal301/NOTICE-Portal-Naming-Convention/assets/5483768/3b50085b-adf0-407e-87e2-3941e9f359b6)
7. Create Pull Request 버튼을 눌러 PR을 등록합니다.

##### 리뷰
1. 리뷰어는 코드리뷰를 요청받으면, 전체 파일을 훑어봅니다.
2. 이때 확인이 완료된 코드는 ```viewed``` 버튼을 클릭해 지워나갑니다.
   ![image](https://github.com/portal301/NOTICE-Portal-Naming-Convention/assets/5483768/4ddb5209-beef-4724-a172-fe0bef18969f)
3. 코드상에 문제나 궁금함이 있으면, 각 라인 앞에 마우스를 올려놓으면 생기는 ```+``` 버튼을 눌러 코맨트를 남길 수 있습니다.
   ![image](https://github.com/portal301/NOTICE-Portal-Naming-Convention/assets/5483768/f0ff4126-f8b1-477f-9676-f3436842f84b)
4. 전체 파일이 완료되었다면 ```Review Changes``` 버튼을 눌러 코멘트를 남기거나, 해당 PR의 Merge를 ```Approve``` 할 수 있습니다.
   ![image](https://github.com/portal301/NOTICE-Portal-Naming-Convention/assets/5483768/71676101-6a1a-4c9a-8b79-e6055f0fa9bd)

##### Merge
1. 리뷰가 완료된 PR은 ```Merge Pull Request``` 버튼을 눌러 ```base branch```로 병합할 수 있습니다.
![image](https://github.com/portal301/NOTICE-Portal-Naming-Convention/assets/5483768/67cb0c86-5953-4cad-8a5b-86a20e5b69fa)
2. 이 과정에서 ```Squash and Merge```를 권장하며, 원격 repo에 존재하는 ```compare``` 브랜치는 버튼을 통해 삭제합니다.

#### 템플릿
1. 원격 Repository 디렉토리 최상단에 ```.github``` 폴더를 생성합니다.
2. ```.github```폴더 안에 ```PULL_REQUEST_TEMPLATE.md```파일을 생성 후 아래의 템플릿을 복사 & 붙여넣기 합니다.

```
## 🧑‍💻 PR 내용

 - 수정/추가한 내용을 적어주세요.
 - 수정/추가한 내용을 적어주세요.
 - 수정/추가한 내용을 적어주세요.
```
<hr>

### Git commit log 간지나게 보는법
1. 커맨드 라인 툴에서 ```nano ~./gitconfig```를 입력합니다. 다른 텍스트 편집기로 ```~./gitconfig```를 수정하셔도 됩니다.
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
