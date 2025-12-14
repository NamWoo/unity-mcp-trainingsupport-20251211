

Unity 에서 MCP 기능을 사용할 수 있게 설치하는 방법을 안내합니다.
Unity에서 무료로 제공하고 있는 공장, 물류창고씬을 활용하여 MCP 를 사용해 로봇을 배치하고 움직이게 해 봅니다.

# MCP for Unity

## AI Client 설치

Client 로 활용할 GPT 서비스를 설치합니다.

1. Google `Antigravity`
2. `Cursor`
3. `Claude Code`
4. OpenAI `Codex`
5. 등등

사용 가능합니다. 위 서비스 모두 잘 동작하고 있음을 확인했으며, 결국은 `Model`, 유/무료 의 차이에 따라 성능이 달라지게 됩니다. 모두 무료서비스가 있으니, 무료로 진행하셔도 무방합니다.

저는 `Cursor` 도 연결해보고 `Codex`도 또 연결해보도록 하겠습니다.

1. Cursor 는 Cursor desktop app 환경에서,
2. Codex 는 Cli, Command Line인 Terminal 방식으로 진행해도록 하겠습니다.

### Cursor 설치

다운로드 후 설치만 하면 됩니다.

1. https://cursor.com/download
2. https://docs.cursor.com/ko/get-started/installation


### Codex 설치

윈도우는 WSL, 맥은 기본 터미널에서
1. 윈도우에선 https://developers.openai.com/codex/windows
   1. WSL 환경 구성 및 설치 후
   2. Control + `R`
   3. cmd 명령어 후 터미널에서 `WSL`
   4. `wsl`
      1. `curl -o- https://raw.githubusercontent.com/nvm-sh/nvm/master/install.sh | bash`
      2. 새 터미널 창 `WSL` 열고 `nvm install 22`
      3. 그리고 `codex`



## Unity 설치


1. Unity 설치
   1. `install` Unity Hub
      1. https://docs.unity3d.com/hub/manual/InstallHub.html
   2. `install` Unity Editor
      1. https://unity.com/releases/editor/archive
      2. 현재 날짜 기준 Unity `6000.3.1f1` 까지 다운 받을 수 있습니다.
         1. 여기서는 `6000.0.64f1`  버전을 다운 받겠습니다.
            1. unityhub://6000.0.64f1/5360b7cd7953
            2. Major 버전인 첫번째 `6000` 은 `Unity6` 를 의미
            3. Minor 버전인 두번째 `0` 은 `Unity6.0` 을 의미
            4. `6000.3.1f1`인 경우 `Unity6.3` 의 의미입니다.
      3. `6000.0.64f1` 다운로드 링크
         1. Unity Hub가 설치되어 있으면,
         2. 여기를 눌러 Editor 다운로드 unityhub://6000.0.64f1/5360b7cd7953
         3. `Download` Unity Warehouse Project
2. Unity 실행
   1. Unity Hub에서
      1. Unity Hub 에서 Projects 창, New Project 를 누르고, 지금 다운로드 받은 Editor version을 확인
      2. [중요] 하단에 Templates 목록 중, `High Definition 3D` 항목을 선택 
      3. 오른쪽에 Project 이름 설정, 위치 저장 후 Create project
   2. Unity Editor에서
      1. Unity Warehouse 샘플 다운로드
         1. Editor가 정상적으로 열렸고 오른쪽 상단에 컴파일링 과정도 모두 완료가 되었다면,
         2. Unity Sample Project 다운로드 후 MCP 설치 및 연결
         3. 상단 Window -> Package Manager 로 들어가면
            1. `In Project`, `Unity Registry`, `My Assets` .. 등등 왼쪽에 확인 가능
            2. `In Project`는 현재 프로젝트에 있는 Asset 확인가능
            3. `Unity Registry`는 Unity 에서 직접 제공하는 Asset을 확인가능
            4. `My Assets`은 보유한 Asset 을 확인 가능
         4. Unity Asset Store에서 무료로 공개하고 있는 샘플을 My Asset에 등록하고, 등록된 내 Asset을 현재 프로젝트로 다운받기 위해선,
            1. [Web]Asset Store에 공개된 무료 에셋을 활용
               1. https://assetstore.unity.com/packages/3d/environments/industrial/unity-warehouse-276394
               2. Asset Store 에선 개발자, 디자이너, 모델러 가 만들고 제공하고 있는 Asset 들을 확인가능 (유/무료)
               3. `Add to My Assets` 선택
            2. Unity Editor에서 `Package Manager` - `Unity Warehouse` 가 있는지 확인 (하단 새로고침)
               1. `Download` 선택, 완료 후 `Import 1.0 to project`
               2. 새 창에서 `import`
      2. Unity MCP 다운로드 및 설정
         1. 설치
            1. 다시 `Package Manager` 탭 상단에 보이는 `+` 선택 후 `Add package from git URL...`
            2. `https://github.com/CoplayDev/unity-mcp.git?path=/MCPForUnity` install
            3. 설치가 완료되었다면 상단에 `Window`에서 `MCP for Unity` 항목을 확인할 수 있음
         2. 설정
            1. Settings
               1. Show Debug Logs 옵션 활성화
            2. Connection
               1. Transport 를 `Stdio`
               2. 그리고 `Start Session`
               3. *초록불* 활성화 확인
            3. Client Configuration
               1. Client 에 사용하려는 AI Agent 설정 `Cursor`
               2. Configure 버튼으로 *초록불* 확인
3. MCP for Unity
   1. LLM 명령으로 Unity 실행해보기


참고
3. https://assetstore.unity.com/packages/3d/environments/industrial/unity-warehouse-276394
4. https://assetstore.unity.com/packages/3d/environments/industrial/unity-factory-276400
5. 
6. MCP 설치 https://github.com/CoplayDev/unity-mcp