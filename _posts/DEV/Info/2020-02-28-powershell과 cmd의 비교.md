---
title:  "[번역] - Windows PowerShell vs. CMD: What’s The Difference?"
search: true
toc : true
toc_label : 네비게이션
toc_sticky : true
tag:
  - tool
  - tip
categories:
  - Info
excerpt: "[번역글] - PowerShell 과 CMD의 차이점"
last_modified_at: 2020-02-28T08:06:00-05:00
---

React native 실습을 위해 패키지를 설치하는 과정에서 [`chocolatey`](https://chocolatey.org/) 라는 툴을 설치하려 했는데, 같은 CLI 환경이어도 CMD 환경에서는 설치가 되지 않아 powershell에서는 설치되는게 궁금해 찾아봤다.   

그러던 와중, 파워쉘과 CMD의 차이점을 간략하게 설명한 글을 찾을 수 있었다.   
알아두면 좋은 내용일 것 같아서 번역글을 블로그에 남겨 본다.


* 글을 매끄럽게 하기 위해 원문의 의도를 최대한 해치지 않는 선에서 의역한 부분이 있는 점은 양해 부탁드립니다. 😊

* 오역 및 지적은 감사히 받겠습니다. 😀


## [원문] [Windows PowerShell vs. CMD: What’s The Difference?](https://www.varonis.com/blog/powershell-vs-cmd/)
> by JEFF PETTERS

## 1. 서론
과거로 돌아가, 플로피 디스크를 사용해 당시 최고의 기기였던 IBM 8086을 부팅해 보았던 사람이라면 커서가 깜빡이는 초록색 화면의 C:\> 프롬프트를 본 적이 있을 것입니다.      

C:\> 가 나타나던 프롬프트 창은 세련된 GUI를 갖게 되었고, 플로피 디스크를 통해 부팅하던 방식도 하드 디스크를 이용한 방식으로 변화했는데 명령 프롬프트(CMD) 만은 아직까지도 살아남았습니다.

CMD 는 최근에서야 Windows 7 에서 등장한 PowerShell 로 교체되었는데, 기존의 CMD 가 증기 기관차라면 PowerShell 은 마치 무인 자동차와도 같은 모습을 보여주고 있습니다.

## 2. Windows Command Prompt
<img src="/assets/images/2020-02-28-powershell-vs-cmd/cmd.PNG">


**CMD** 로도 알려진 윈도우 명령 프롬프트는 마이크로소프트 도스 운영체제의 독보적인 쉘이었습니다. CMD 는 Windows 10 빌드 14791 버전에서 PowerShell 이 마이크로소프트 기본 설정으로 지정되기 전까지 기본 쉘이었으며, 도스 운영체제부터 현재까지 이어져오는 것들 중 하나입니다.

## 3. Windows PowerShell
<img src="/assets/images/2020-02-28-powershell-vs-cmd/powershell.PNG">


**Windows PowerShell** 은 기존의 CMD 기능과 내장 시스템 관리 기능을 가진 새로운 스크립트 / `cmdlet` 명령어가 결합된 MS의 새로운 쉘입니다.  

PowerShell 의 `cmdlets` 는 사용자과 관리자가 재사용 가능한 스크립트를 통해 복잡한 업무를 자동화할 수 있도록 하며, 시스템 관리자는 PowerShell 을 사용해 관리 업무를 자동화함으로써 막대한 시간을 절약할 수 있습니다.

## 4. PowerShell vs. CMD
PowerShell 과 CMD 를 비교하는 것은 마치 사과와 귤을 비교하는 것과 같은 일입니다. 두 인터페이스에서 `dir` 명령어가 작동하는 방식은 같아 보일 수 있어도, 사실 이 둘은 완전히 다릅니다.   

PowerShell 은 윈도우 내부의 관리 옵션을 다루는 독립적인 프로그래밍 객체[^1]인 `cmdlets` 를 사용하는데, PowerShell 이 공개되기 전에는 이러한 옵션을 찾기 위해 시스템 관리자가 GUI를 통해 확인해야만 했으며 대량의 옵션을 변경하기 위해 (GUI 환경에서) 메뉴를 클릭하는 방법은 마땅히 재사용할 방법이 없었습니다.

PowerShell 은 리눅스의 `bash` 처럼 [`파이프`](https://ko.wikipedia.org/wiki/%ED%8C%8C%EC%9D%B4%ED%94%84_(%EC%9C%A0%EB%8B%89%EC%8A%A4)) 를 통해 `cmdlet` 를 묶고, 입/출력 데이터를 공유합니다. `파이프` 는 사용자가 매개변수와 데이터를 `cmdlets` 간 전달할 수 있는 복잡한 스크립트를 만들 수 있게 해주었고, 이를 이용해 사용자는 서버와 같은 데이터의 대규모 변경이나 작업의 자동화를 위한 재사용 가능한 스크립트를 만들 수 있습니다.

PowerShell 의 여러 멋진 기능들 중 하나는 각자 다른 `cmdlet` 에 대해 별명을 붙일 수 있다는 것입니다. 별명(Aliases)을 통해 사용자는 여러 `cmdlets` 나 스크립트에 대해 고유한 이름을 부여할 수 있는데, 이를 통해 사용자는 보다 직관적으로 다른 쉘 사이를 넘나들 수 있습니다.

(예를 들자면, `ls` 는 리눅스 `bash` 에서는 디렉토리 목록을 보여주는 명령어지만 PowerShell에서는 `ls` 와 `dir` 모두 `Get-ChildItem` 이라는 `cmdlet` 의 별명으로 사용할 수 있습니다.)

[^1]: self-contained programming objects
