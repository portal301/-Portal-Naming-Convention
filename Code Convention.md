# Code Convention

코드 컨벤션은 기본적으로 해당 언어에서 권장하는 표준 컨벤션을 준수합니다. 이를 통해 코드의 일관성과 가독성을 유지하며, 팀원 간의 협업을 원활하게 만듭니다. 각 언어는 자체적으로 권장하는 스타일 가이드와 베스트 프랙티스를 가지고 있으며, 이러한 가이드를 따르는 것은 코드 품질을 향상시키고 유지보수성을 높이는 데 중요한 역할을 합니다.

## 각 언어별 코드컨벤션 

#### [Javascript/TypeScript](https://www.w3schools.com/js/js_conventions.asp)

#### [Python](https://peps.python.org/pep-0008)

#### [C# / Unity](https://learn.microsoft.com/ko-kr/dotnet/csharp/fundamentals/coding-style/coding-conventions)

## 그 밖에 협업을 위한 코드컨벤션
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
