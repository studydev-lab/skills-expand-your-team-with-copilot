## Step 3: Copilot 환경 준비하기

학교에 대한 추가 정보와 선생님들이 자주 요청하는 일반적인 작업을 Copilot에 제공합시다.

앞으로의 개발이 모든 사람에게 원활하고 신뢰할 수 있도록, Copilot도 모든 도구와 종속성이 이미 설치된 상태에서 세션을 시작해야 합니다. :rocket:

### 📖 이론: Copilot의 개발 환경 커스터마이징

Copilot의 환경은 여러 가지 방법으로 커스터마이징할 수 있습니다. 아래에서 가장 유용한 커스터마이징 옵션을 살펴봅시다:

📝 **Copilot 지침**

Copilot 지침 파일은 Copilot이 이슈에 대한 추론을 시작하기 전에 저장소별 안내, 선호 사항 및 컨텍스트를 제공해야 합니다. 다음을 포함하세요:

- 프로젝트 개요 (목적, 목표 및 관련 배경 정보 포함)
- 프로그램 아키텍처, 따라야 할 표준 및 규칙
- 일반적인 작업을 위한 유용한 명령어 또는 스크립트

⚙️ **Copilot 설정 단계**

필요한 모든 도구와 종속성 버전으로 코딩 에이전트 세션을 사전 구성하여 빠르고 일관되며 재현 가능한 도움을 보장합니다. 이는 일반적으로 다음을 의미합니다:

- 원하는 버전의 Python, Node와 같은 필수 도구 구성
- 프로젝트 종속성, 라이브러리 사전 설치 및 설정 스크립트 실행

이것은 Copilot이 임시 설치를 시도하면서 발생하는 지연이나 오류를 방지하는 데 크게 도움이 됩니다

> [!NOTE]
> Copilot에 더 많은 기능을 제공하기 위해 [Model Context Protocol (MCP) 서버를 활성화](https://docs.github.com/en/copilot/how-tos/use-copilot-agents/coding-agent/extend-coding-agent-with-mcp#adding-an-mcp-configuration-to-your-repository)할 수도 있습니다!
>
> > [GitHub](https://github.com/github/github-mcp-server) 및 [Playwright](https://github.com/microsoft/playwright-mcp) MCP 서버는 기본적으로 이미 활성화되어 있습니다 :rocket:

### ⌨️ 활동: Copilot을 안내할 지침 작성

학교에 대한 세부 정보, Copilot이 맡아야 할 역할, 선생님들이 요청하는 일반적인 작업을 포함하는 Copilot 지침을 작성합시다. 이것은 Copilot이 선생님들과 더 자연스럽게 상호작용하는 데 도움이 됩니다.

1. 상단 탐색에서 **Code** 탭을 선택하세요.

1. 다음 이름으로 새 브랜치를 생성하세요:

   ```txt
   prepare-environment
   ```

   <img width="250" alt="image" src="https://github.com/user-attachments/assets/c48deded-4214-4edd-9a50-d1368bfb12e8" />

1. `.github/copilot-instructions.md` 파일로 이동하여 편집을 위해 여세요.

1. 플레이스홀더 텍스트를 개발 가이드 링크로 교체하세요.

   ```md
   ## Development Environment

   For detailed setup and development instructions, please refer to our [Development Guide](../docs/how-to-develop.md).
   ```

1. 학교와 선생님들에 대한 추가 정보를 추가하여 Copilot이 더 자연스럽게 상호작용하도록 도와주세요.

   ```md
   ### User Interaction

   Consider the following when communicating with the staff.

   - The staff is not technical. Explain in simple terms as much as possible and avoid software jargon.
   - Any new code must be easy to maintain and understand, without significant coding experience.

   ## Program architecture

   - The website users are the students and teachers. Make sure the user experience is simple.
   - Do not make additional apps or services.
   - Do not make command line tools.
   - Do not create a long single file application. Always use an easy-to-understand directory structure.
   - Only use HTML, CSS, Javascript, and Python. No other languages.
   ```

   > 💡 팁: 더 많은 세부 사항을 추가할 수 있습니다. 아이디어는 `copilot-instructions-ext.md` 파일을 확인하세요.

1. 완료되면 `prepare-environment` 브랜치에 **변경 사항을 커밋**하세요.

### ⌨️ 활동: Copilot을 위한 코딩 환경 준비

Copilot의 개발 환경을 커스터마이징하고 [권한](https://docs.github.com/en/actions/writing-workflows/choosing-what-your-workflow-does/controlling-permissions-for-github_token)을 조정하는 것은 `copilot-setup-steps.yml`이라는 고유한 [GitHub Actions](https://github.com/features/actions) 워크플로우로 수행합니다.

이 프로젝트에서는 Python 백엔드 종속성을 사전 설치하고 백엔드가 사용할 MongoDB 데이터베이스를 준비합니다.

1. `prepare-environment` 브랜치에 있는지 확인하세요.

1. `.github/workflows/` 디렉토리로 이동하세요.

1. 오른쪽 상단에서 **Add file** 버튼을 클릭하고 **Create new file**을 선택하세요.

   <img width="250" alt="image" src="https://github.com/user-attachments/assets/c135dd3f-72bd-4d2b-b21f-9c4968a06f5f" />

1. 파일 이름을 다음과 같이 설정하세요:

   ```txt
   copilot-setup-steps.yml
   ```

   <img width="650" alt="image" src="https://github.com/user-attachments/assets/ac615290-1045-45a5-8201-637721ef6fd2" />

1. 다음 워크플로우 설정을 붙여넣으세요. 이것은 웹사이트의 Python 백엔드 종속성을 사전 설치하고 MongoDB 서비스를 설정합니다.

   ```yml
   name: "Copilot Setup Steps"

   on: workflow_dispatch
   jobs:
     # This is the required job name. If different, Copilot will ignore it.
     copilot-setup-steps:
       runs-on: ubuntu-latest
    
     # Starts a MongoDB service for Copilot to use during its session.
       services:
        mongo:
          image: mongo:7
          ports:
            - 27017:27017

       # Grant Copilot early access to read the repository content.
       permissions:
         contents: read

       steps:
         - name: Checkout code
           uses: actions/checkout@v5

         - name: Set up Python
           uses: actions/setup-python@v6
           with:
             python-version: "3.13"
             cache: "pip"

         - name: Install Python dependencies
           run: |
             python -m pip install --upgrade pip
             pip install -r src/requirements.txt
   ```

   > 🪧 **참고:** Copilot은 나중에 자동으로 저장소 콘텐츠를 가져옵니다. 이 워크플로우는 설정 중 종속성 설치를 위해 조기 접근을 제공합니다.

   > 🪧 **참고:** Copilot은 누락된 종속성을 자동으로 식별하고 설치합니다. 지금 하면 Copilot의 시간을 절약하고 적절한 환경 설정을 보장합니다.

1. 오른쪽 상단에서 **Commit changes...** 버튼을 클릭하고 `prepare-environment` 브랜치에 변경 사항을 커밋하세요.

1. **Pull Request를 생성**하되, 아직 머지하지 **마세요**. Mona가 파일이 올바른지 확인할 것입니다.

1. Mona가 다음 단계를 공유한 후, Pull Request를 **머지해야** 합니다.

> 🙋 **질문:** 수동 프로세스가 Copilot이 대부분의 작업을 수행하는 것과 비교하여 어떻게 느껴졌나요? 🤔

<details>
<summary>🤷 문제가 있으신가요?</summary><br/>

Mona가 실수에 대한 피드백을 공유하기 전에 실수로 Pull Request를 머지한 경우, 괜찮습니다. 브랜치를 다시 만들고 새 Pull Request로 다시 시도하세요.

</details>
