## Step 4: Agents Panel로 여러 작업 관리하기 🎛️

이제 Copilot의 작업 환경이 준비되었으니, 더 복잡한 이슈를 작업하여 방과후 활동 웹사이트를 더 멋지게 만들어봅시다! ✨🚀

지금까지 우리는 이슈를 하나씩 할당하여 Copilot과 팀을 이뤄 작업했습니다. 📝🤝

하지만 추가 단계를 건너뛰고 바로 작업 모드로 들어갈 수 있다면? Copilot이 여러 작업을 동시에 처리하면서 진행 상황을 알려준다면? 🤹‍♂️

어떻게 하는지 살펴봅시다! 👀

### 📖 이론: Agents Panel로 어디서나 위임하기

에이전트 패널은 GitHub에서 에이전틱 워크플로우를 위한 미션 컨트롤 센터입니다.

현재 작업에서 벗어나지 않고 Copilot에 새 작업을 전달하고 기존 작업을 추적할 수 있는 경량 오버레이입니다.

<!-- image source: https://github.blog/news-insights/product-news/agents-panel-launch-copilot-coding-agent-tasks-anywhere-on-github/ -->

   <img width="400" alt="Agents Panel view" src="https://github.blog/wp-content/uploads/2025/08/Agents-panel-with-callout-2.png" />

에이전트 패널에서 할 수 있는 것:

- 🛠️ 페이지를 전환하지 않고 백그라운드 작업 할당
- 👀 실시간 상태로 진행 중인 작업 모니터링
- 🔗 리뷰할 준비가 되면 Pull Request로 바로 이동

Agents panel을 사용하면 여러 이슈를 빠르게 할당하고, 진행 상황을 추적하고, 결과를 리뷰할 수 있습니다. 모두 한 곳에서.

### ⌨️ 활동: Agents Panel을 통해 작업 할당 :robot:

> [!IMPORTANT]
> 진행하기 전에 이전 단계의 `prepare-environment` 브랜치를 머지했는지 확인하세요.

Agents Panel에 익숙해집시다!

1. 새 탭에서 상단 탐색 바의 **Copilot Agents** 패널을 여세요.

   <img width="600" alt="Agents panel view" src="https://github.com/user-attachments/assets/c95a5558-a78d-41fe-bf26-25fb1d8aad52" />

1. 패널에서 `{{ full_repo_name }}` 저장소가 선택되어 있고 브랜치가 `main`으로 설정되어 있는지 확인하세요.
1. Copilot에 다음 작업을 할당하세요:

   > ![Static Badge](https://img.shields.io/badge/-Task%201-text?style=social&logo=github%20copilot)
   >
   > ```prompt
   > Integrate social sharing buttons so
   > users can easily share activities with their friends
   > ```

   > ✨ **보너스:** 웹사이트에서 개선하고 싶은 것을 생각해서 Copilot에 할당하세요. 여기서 창의력을 발휘할 수 있습니다!

1. 잠시 후, 패널에 현재 상태와 함께 작업이 나타나는 것을 확인할 수 있습니다. 할당된 모든 작업의 고수준 개요를 보려면 여기로 돌아올 수 있습니다.

   <img width="400" alt="Agents Panel task in progress view" src="https://github.com/user-attachments/assets/e80c2e39-6b2b-4d0b-9f1e-f02f41495241" />

1. 작업을 클릭하면 새 탭에서 세션 로그로 바로 이동하여 Copilot이 실시간으로 작업하는 방식을 추적할 수 있습니다.

1. Copilot이 이전 단계에서 설정한 커스터마이징 단계를 실행하는 것으로 시작하는 것을 볼 수 있습니다!

   <img width="600" alt="Copilot session logs with copilot setup steps" src="https://github.com/user-attachments/assets/4d93e2f1-9086-486d-b674-98478e16dbdf" />

1. 지금은 Copilot이 작업하도록 두고, 나중에 결과를 리뷰하러 돌아올 수 있습니다 ✨

> [!TIP]
> https://github.com/copilot/agents 에서 Agents Panel을 전체 화면 모드로 접근할 수도 있습니다.

### ⌨️ 활동: 2개의 이슈를 동시에 구현해보기

저장소에 아직 열린 이슈가 있습니다. Copilot이 여러 이슈를 동시에 처리하는 방법을 살펴봅시다!

1. 상단 탐색에서 **Issues** 탭을 선택하세요.

1. 다음 2개의 이슈를 찾아 각각 새 탭에서 여세요.

   - `Difficulty Tracks`

   - `Dark Mode`

1. 두 탭을 열어둔 상태에서 둘 다 Copilot에 동시에 할당하세요.

1. **Copilot Agents** 패널을 다시 열면 할당한 이슈가 여기에도 나타나는 것을 확인하세요!

   <img width="300"  alt="Copilot Agents Panel with three tasks running in parallel" src="https://github.com/user-attachments/assets/551a26c5-ed07-478a-9937-f1f66babd0b5" />

1. 두 작업 모두 별도의 브라우저 탭에서 진행 상황을 모니터링하세요. 오른쪽 상단의 **View Pull Request** 버튼을 클릭하여 각 작업의 Pull Request로 이동할 수 있습니다.
   > 💡 **팁:** 이전 활동에서 할당한 작업의 상태도 확인할 수 있습니다. Copilot이 지금쯤 완료했을 수도 있습니다!

1. Copilot이 작업 중 하나를 완료하면, PR 설명과 변경 사항을 리뷰하고 Pull Request를 머지하세요!

1. 최소 1개의 Pull Request가 머지되면, Mona가 작업을 확인하고 최종 리뷰를 준비합니다.

> [!IMPORTANT]
> 여러 이슈를 병렬로 작업하는 것은 하나의 예술입니다. 🎨
> 머지 충돌을 피하려면 독립적으로 유지하세요! 😱
