# 멀티 부팅 설치하기

#### 1. 우분투 16.04 다운로드
```
- 하단의 링크를 클릭 후 모든 바를 0으로 세팅 후 OS 이미지 파일 다운로드  
```
[다운로드](https://www.ubuntu.com/download/desktop/contribute?version=16.04.1&architecture=amd64 "다운로드")

#### 2. 부팅 USB 만들기
```
- 하단의 링크를 클릭해 프로그램 다운
- USB 삽입
- 프로그램을 실행 후 위에서 다운받은 OS 이미지 파일을 선택
- 다음 다음을 눌러 USB에 설치  
```
[다운로드](https://www.pendrivelinux.com/universal-usb-installer-easy-as-1-2-3 "다운로드")

#### 3. 하드 볼륨 축소
```
- 찾기 -> 하드 디스크 파티션 만들기 및 포맷
- 용량 축소시킬 하드  선택 후, 마우스 오른쪽 눌러 볼륨 축소 클릭
- 최소 40기가 이상으로 선택
```
#### 4. 부팅옵션 변경
```
- 찾기 -> 전원 옵션
- 전원 단추 작동 설정 - 현재 사용할 수 없는 설정 변경
- 빠른 시작 켜기 체크 해제
- USB 삽입
- 재부팅 후, BIOS 세팅으로 진입(F2, F8, F10, DEL 키 중 하나)
- boot -> secure boot -> disabled
- boot -> Boot Device Priority -> USB를 1순위로 설정
- Save Changes and Reset 눌러 재부팅
```
#### 5. 우분투 설치
```
- Install Ubuntu 클릭
- 언어 선택 -> 설치 중 업데이트 다운로드 선택
- 설치 형식 -> 기타 선택
- 메모리가 적을 경우 스왑영억 지정으로 가상메모리 할당
- 남은 공간을 더블 클릭
- 용량 : 4096 MB, 논리파티션, 시작, 스왑 영역
- 남은 공간을 더블 클릭
- 주파티션, 시작, EXT4 저널링 파일 시스템, / 선택
- 계속 다음 눌러 설치 완료
- 재부팅 버튼 누르고 재빨리 USB를 뺀 후 재부팅
```
# 설치 끝
이면 좋겠지만 위의 방법으로 정상적으로 설치하신 분은 몇 안 될거라고 예상합니다. 이는 ***노트북 제조사마다의 차이 + 노트북 모델 + 외장그래픽*** 등의 이유로 에러가 발생하기 때문입니다. 
# 에러 해결하기

#### 1. Install Ubuntu 클릭시 재부팅이 되는 경우 
```
- 키보드로 Install Ubuntu에 커서를 올린 후 e 키를 누름
- quiest splash --- 이라는 문장을 quiest splash nomodeset 으로 변경
- F10 눌러 재부팅
```
#### 2. nvidia 외장 그래픽 사용할 경우

하단의 링크를 눌러서 그래픽 드라이버 다운로드  

[다운로드](http://www.nvidia.co.kr/Download/index.aspx?lang=kr "다운로드")

터미널을 실행시킨 후 입력
```
sudo gedit /etc/modprobe.d/blacklist.conf
```
아래의 문구를 마지막에 추가 후 저장
```
blacklist amd76x_edac #this might not be required for x86 32 bit users.
blacklist vga16fb
blacklist nouveau
blacklist rivafb
blacklist nvidiafb
blacklist rivatv
```
터미널에 명령어 입력 
```
sudo apt-get remove --purge nvidia*
```
새로운 터미널을 열어 명령어 입력 (ctrl + art + f1)
```
sudo service lightdm stop
```
다운로드 받은 파일을 실행 가능한 상태로 변경
```
chmod +x NVIDIA-Linux-x86_64-361.42.run
```
다운받은 폴더로 들어가 실행
```
sudo ./NVIDIA-Linux-x86_64-367.35.run
```
설치 끝나면 디스플레이 매니저를 시작
```
sudo service lightdm start
```
그래픽으로 전환(ctrl + alt + f7) 후 설치 됐는지 확인
```
nvidia-smi
nvidia-settings
```
# ATOM 설치
[다운로드](https://atom.io "다운로드")
# pycharm(community version) 설치
[다운로드](https://www.jetbrains.com/pycharm "다운로드")
# pycharm 실행
```
- 설치한 폴더로 들어감
- bin 폴더로 들어감
- ./pycharm.sh
```
# 조금 더 쉽게 pycharm 실행
```
vi ~/.bashrc
```
마지막줄에 아래 문장 추가 후 저장
```python
alias pycharm="~/다운로드/pycharm-community-2016.2.3/bin/pycharm.sh"
```
```
source ~/.bashrc
```
# apt-get 업그레이드 및 git 설치
```
sudo apt-get update
sudo apt-get upgrade
sudo apt-get install git
```
# pyenv 설치
#### 1. Install pyenv
```
curl -L https://raw.githubusercontent.com/yyuu/pyenv-installer/master/bin/pyenv-installer | bash
```
#### 2. shell에 추가
```
vi ~/.bashrc
```
맨마지막에 아래 내용 붙여 넣고 저장
```
export PATH="~/.pyenv/bin:$PATH"
eval "$(pyenv init -)"
eval "$(pyenv virtualenv-init -)"
```
#### 3. 터미널 재시작
터미널을 완전히 종료 혹은 아래 명령어 입력
```
source ~/.bashrc
source ~/.bash_profile
```
