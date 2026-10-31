# thisshine 돌고래 VTuber 아바타 (Warudo용 VRM)

하늘색 긴 머리, 파란 눈, 돌고래 후드를 입은 VTuber 아바타입니다. 의상 5벌이 VRM 하나에 들어 있고, Warudo에서 단축키로 갈아입힙니다.

파일: `Dolphin_thisshine.vrm` (VRM 1.0, 약 51MB)

## 의상

| 번호 | 의상 | Warudo 표정 이름 |
|---|---|---|
| 1 | 돌고래 후드 + 반바지 + 양말·운동화 (기본) | 없음. 모든 의상 표정을 끄면 이 상태 |
| 2 | 하늘색 크롭 저지 + 프릴 치마 + 레그워머 + 플랫폼 운동화 + 액세서리 | `outfit2` |
| 3 | 할로윈 유령 고양이 | `outfit3` |
| 4 | 검정 롱코트 + 셔츠 + 넥타이 + 반바지 | `outfit4` |
| 5 | 별무늬 잠옷 | `outfit5` |

추가 토글:

| 표정 이름 | 하는 일 |
|---|---|
| `paws` | 의상 3의 고양이 손 장갑을 켜고 끕니다. 끄면 맨손이 나옵니다. |
| `hood_off` | 돌고래 후드를 벗깁니다. |

## Warudo에 넣기

1. `Dolphin_thisshine.vrm`을 Warudo의 Characters 폴더에 넣습니다.
   - Warudo에서 캐릭터 에셋을 선택하고 **Open Characters Folder**를 누르면 이 폴더가 열립니다.
   - Steam 기본 설치 경로는 `C:\Program Files (x86)\Steam\steamapps\common\Warudo\Warudo_Data\StreamingAssets\Characters`입니다.
2. 캐릭터 에셋의 Source에서 `Dolphin_thisshine`을 고릅니다.
3. 표정을 가져오겠냐고 물으면 **Yes**를 누릅니다. 묻지 않으면 캐릭터 에셋 → Expressions → **Import VRM Expressions**를 누르고, 이어서 **Generate Key Binding Blueprint**를 누릅니다.

## 꼭 할 설정: 의상 표정을 같은 Layer에 두기

Warudo는 VRM 표정을 가져올 때 `outfit2`~`outfit5`에 서로 다른 Layer(2, 3, 4, 5…)를 줍니다. 이대로 두면 두 의상이 동시에 켜져서 옷이 겹칩니다.

캐릭터 에셋 → Expressions에서 아래처럼 바꿉니다.

| 표정 | Layer |
|---|---|
| `outfit2`, `outfit3`, `outfit4`, `outfit5` | 모두 **10** (같은 숫자면 됩니다) |
| `paws` | 11 |
| `hood_off` | 12 |

같은 Layer의 표정은 하나만 켜집니다. 다른 의상을 켜면 이전 의상은 자동으로 꺼집니다.

## 단축키

자동 생성된 **Expression Key Bindings** 블루프린트에 단축키가 들어 있습니다. 기본값은 Alt+숫자입니다. 바꾸려면 블루프린트에서 **On Keystroke Pressed** 노드의 Keystroke를 수정합니다.

- 의상 1(기본)로 돌아가기: **Alt+Backspace**(모든 표정 끄기)를 누르거나 켜진 의상 표정을 다시 누릅니다.
- 의상 3 맨손: `outfit3`을 켠 상태에서 `paws`를 끕니다. `paws`는 의상 3을 입었을 때만 의미가 있습니다.

## 트래킹

- 표준 VRM 휴머노이드 뼈대라서 Warudo의 웹캠(MediaPipe) 상반신·손 트래킹, 얼굴 트래킹이 그대로 됩니다.
- 모든 의상의 소매는 손목에서 끝나서 손가락 트래킹을 가리지 않습니다. 고양이 손 장갑은 `paws`로 끌 수 있습니다.
- 얼굴은 ARKit 52 블렌드셰이프를 지원합니다. iPhone 계열 트래킹도 쓸 수 있습니다.

## 물리

- 머리카락, 치마, 코트 자락, 유령 자락, 꼬리, 레그워머가 VRM 스프링으로 흔들립니다.
- 다리와 엉덩이에 충돌체가 있어서 치마와 자락이 다리를 뚫지 않습니다.
- 천끼리는 서로 부딪히지 않습니다(VRM 스프링의 한계). 팔을 등 뒤로 돌리면 팔이 천을 지나갈 수 있습니다.

## 알려진 점

- 입지 않은 의상은 투명 처리(MToon alpha cutout)로 숨깁니다. 표정을 켜면 해당 의상의 블렌드셰이프와 재질 알파가 함께 켜집니다.
- 할로윈 미라 마녀 의상은 작업 중이며 나중에 이 파일에 추가됩니다.

## 버전

- 2026-10-31: 의상 1~5 통합 첫 버전
