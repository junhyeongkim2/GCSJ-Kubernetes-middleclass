# GCSJ

### 1주차 - Day 4

**-Getting started with Google Kubernetes Engine-**

### 실습 : Cloud Build로 작업하기

이 실습에서는 Docker 컨테이너 이미지를 Cloud Build를 사용하여 제공된 코드와 Dockerfile로 빌드합니다

그런 다음 컨테이너를 Container Registry에 업로드 합니다.

# **작업 1. 필요한 API가 활성화되어 있는지 확인**

1. Google Cloud 프로젝트의 이름을 기록해 둡니다. 이 값은 Google Cloud Console의 상단 표시줄에 표시됩니다. `qwiklabs-gcp-`16진수 뒤에 오는 형식 입니다.
2. Google Cloud Console의 **탐색 메뉴API 및 서비스**

   (

   [https://cdn.qwiklabs.com/tkgw1TDgj4Q%2BYKQUW4jUFd0O5OEKlUMBRYbhlCrF0WY%3D](https://cdn.qwiklabs.com/tkgw1TDgj4Q%2BYKQUW4jUFd0O5OEKlUMBRYbhlCrF0WY%3D)

   )에서

   를 클릭합니다 .

3. **API 및 서비스 활성화 를** 클릭 합니다 .
4. **API 및 서비스 검색** 상자에 를 입력 합니다 `Cloud Build`.
5. Cloud Build API의 결과 카드에서 Cloud Build API가 활성화되었음을 확인하는 메시지가 표시되지 않으면 `ENABLE`버튼을 클릭합니다.
6. 뒤로 버튼을 사용하여 검색 상자가 있는 이전 화면으로 돌아갑니다. 검색 상자에 를 입력 `Container Registry`합니다.
7. Google Container Registry API의 결과 카드에서 Container Registry API가 사용 설정되었음을 확인하는 메시지가 표시되지 않으면 `ENABLE`버튼을 클릭합니다.

# **작업 2. DockerFile 및 Cloud Build로 컨테이너 빌드**

빌드 구성 파일을 작성하여 컨테이너를 빌드할 때 수행할 작업에 대한 지침을 Cloud Build에 제공할 수 있습니다. 이러한 빌드 파일은 종속성을 가져오고, 단위 테스트를 실행하고, 분석하는 등의 작업을 수행할 수 있습니다. 이 작업에서는 DockerFile을 만들고 이를 Cloud Build에서 빌드 구성 스크립트로 사용합니다. 또한 컨테이너 내부의 응용 프로그램을 나타내는 간단한 셸 스크립트(quickstart.sh)를 만듭니다.

1. Google Cloud Console 제목 표시줄에서 **Cloud Shell 활성화** 를 클릭합니다 .
2. 메시지가 표시되면 **계속** 을 클릭 합니다.

Google Cloud Console 창 하단에 Cloud Shell이 열립니다.

1. `quickstart.sh`nano 텍스트 편집기를 사용하여 빈 파일을 만듭니다 .

`나노 퀵스타트.sh`

복사되었습니다!

content_copy

1. `quickstart.sh`파일 에 다음 줄을 추가 합니다.

`#!/bin/sh echo "안녕하세요! 시간은 $(date)입니다."`

복사되었습니다!

content_copy

1. 파일을 저장하고 **CTRL+X** 키를 눌러 nano를 닫은 다음 **Y** 및 **Enter** 키를 누릅니다 .
2. `Dockerfile`nano 텍스트 편집기를 사용하여 빈 파일을 만듭니다 .

`나노 도커 파일`

복사되었습니다!

content_copy

1. 다음 Dockerfile 명령을 추가합니다.

`고산에서`

복사되었습니다!

content_copy

이것은 Alpine Linux 기본 이미지를 사용하도록 빌드에 지시합니다.

1. Dockerfile 끝에 다음 Dockerfile 명령을 추가합니다.

`복사 빠른 시작.sh /`

복사되었습니다!

content_copy

`quickstart.sh`그러면 이미지의 / 디렉토리에 스크립트가 추가 됩니다.

1. Dockerfile 끝에 다음 Dockerfile 명령을 추가합니다.

`CMD ["/quickstart.sh"]`

복사되었습니다!

content_copy

`/quickstart.sh`이렇게 하면 연결된 컨테이너가 생성되고 실행될 때 스크립트 를 실행하도록 이미지가 구성 됩니다.

이제 Dockerfile은 다음과 같아야 합니다.

`고산에서 복사 빠른 시작.sh / CMD ["/quickstart.sh"]`

복사되었습니다!

content_copy

1. 파일을 저장하고 **CTRL+X** 키를 눌러 nano를 닫은 다음 **Y** 및 **Enter** 키를 누릅니다 .
2. Cloud Shell에서 다음 명령어를 실행하여 `quickstart.sh`스크립트를 실행 가능하게 만듭니다.

`chmod +x 빠른 시작.sh`

복사되었습니다!

content_copy

1. Cloud Shell에서 다음 명령어를 실행하여 Cloud Build에서 Docker 컨테이너 이미지를 빌드합니다.

`gcloud 빌드 제출 --tag gcr.io/${GOOGLE_CLOUD_PROJECT}/quickstart-image .`

복사되었습니다!

content_copy

**참고:** 명령 끝에 있는 점(".")을 놓치지 마십시오. 점은 소스 코드가 빌드 시 현재 작업 디렉토리에 있음을 지정합니다.

빌드가 완료되면 Docker 이미지가 빌드되어 Container Registry에 푸시됩니다.

1. Google Cloud Console의 **탐색 메뉴Container Registry이미지**

   (

   [https://cdn.qwiklabs.com/tkgw1TDgj4Q%2BYKQUW4jUFd0O5OEKlUMBRYbhlCrF0WY%3D](https://cdn.qwiklabs.com/tkgw1TDgj4Q%2BYKQUW4jUFd0O5OEKlUMBRYbhlCrF0WY%3D)

   )에서

   >

   를 클릭 합니다.

`quickstart-image`목록에 Docker 이미지가 나타납니다 .

# **작업 3. 빌드 구성 파일 및 Cloud Build로 컨테이너 빌드**

Cloud Build는 커스텀 빌드 구성 파일도 지원합니다. 이 작업에서는 Cloud Build와 함께 커스텀 YAML 형식의 빌드 파일을 사용하여 기존 Docker 컨테이너를 통합합니다.

1. Cloud Shell에서 다음 명령어를 입력하여 저장소를 실습 Cloud Shell에 복제합니다.

`자식 클론 https://github.com/GoogleCloudPlatform/training-data-analyst`

복사되었습니다!

content_copy

1. 작업 디렉터리에 대한 바로 가기로 소프트 링크를 만듭니다.

`ln -s ~/training-data-analyst/courses/ak8s/v1.1 ~/ak8s`

복사되었습니다!

content_copy

1. 이 실습의 샘플 파일이 포함된 디렉터리로 변경합니다.

`CD ~/ak8s/Cloud_Build/a`

복사되었습니다!

content_copy

라는 샘플 사용자 정의 클라우드 빌드 구성 파일 이 이 디렉토리에 제공 되며 첫 번째 작업에서 생성 한 스크립트 및 `cloudbuild.yaml`사본도 제공됩니다 .`Dockerfilequickstart.sh`

1. Cloud Shell에서 다음 명령어를 실행하여 의 콘텐츠를 봅니다 `cloudbuild.yaml`.

`고양이 cloudbuild.yaml`

복사되었습니다!

content_copy

다음이 표시됩니다.

`단계:

- 이름: 'gcr.io/cloud-builders/docker'
  인수: [ '빌드', '-t', 'gcr.io/$PROJECT_ID/quickstart-image', '.' ]
  이미지:
- 'gcr.io/$PROJECT_ID/빠른 시작 이미지'`

이 파일은 Cloud Build가 Docker를 사용하여 현재 로컬 디렉터리의 Dockerfile 사양을 사용하여 이미지를 빌드하고 `gcr.io/$PROJECT_ID/quickstart-image`( `$PROJECT_ID`연결된 프로젝트의 프로젝트 ID로 Cloud Build에 의해 자동으로 채워지는 대체 변수임) 태그를 지정하고 해당 이미지를 다음으로 푸시하도록 지시합니다. 컨테이너 레지스트리.

1. Cloud Shell에서 다음 명령어를 실행하여 `cloudbuild.yaml`빌드 구성 파일로 사용하여 Cloud Build를 시작합니다.

`gcloud 빌드 submit --config cloudbuild.yaml .`

복사되었습니다!

content_copy

Cloud Shell에 대한 빌드 출력은 이전과 동일해야 합니다. 빌드가 완료되면 동일한 이미지의 새 버전이 Container Registry로 푸시됩니다.

1. Google Cloud Console의 **탐색 메뉴Container Registry이미지**`quickstart-image`

   (

   [https://cdn.qwiklabs.com/tkgw1TDgj4Q%2BYKQUW4jUFd0O5OEKlUMBRYbhlCrF0WY%3D](https://cdn.qwiklabs.com/tkgw1TDgj4Q%2BYKQUW4jUFd0O5OEKlUMBRYbhlCrF0WY%3D)

   )에서

   >

   를 클릭한 다음 을 클릭

   합니다.

의 두 가지 버전이 `quickstart-image`목록에 있습니다.

*내 진행 상황* 확인을 클릭 하여 목표를 확인합니다.

Cloud Build에서 두 개의 컨테이너 이미지를 빌드합니다.

**내 진행 상황 확인**

1. Google Cloud Console의 **탐색 메뉴Cloud Build기록**

   (

   [https://cdn.qwiklabs.com/tkgw1TDgj4Q%2BYKQUW4jUFd0O5OEKlUMBRYbhlCrF0WY%3D](https://cdn.qwiklabs.com/tkgw1TDgj4Q%2BYKQUW4jUFd0O5OEKlUMBRYbhlCrF0WY%3D)

   )에서

   >

   을 클릭 합니다.

두 개의 빌드가 목록에 나타납니다.

1. 목록 상단에서 빌드의 빌드 ID를 클릭합니다.

빌드 로그를 포함한 빌드 세부 정보가 표시됩니다.

# **작업 4. 빌드 구성 파일 및 Cloud Build로 컨테이너 빌드 및 테스트**

커스텀 빌드 구성 파일의 진정한 힘은 단순히 컨테이너를 빌드하는 것 외에도 새로 빌드된 컨테이너에서 테스트를 실행하고 다양한 대상으로 푸시하고 Kubernetes Engine에 배포하는 것과 같은 다른 작업을 병렬 또는 순서로 수행할 수 있다는 것입니다. .

이 실습에서는 빌드한 컨테이너를 테스트하고 호출 환경에 결과를 보고하는 빌드 구성 파일과 같은 간단한 예를 볼 것입니다.

1. Cloud Shell에서 이 실습의 샘플 파일이 포함된 디렉터리로 변경합니다.

`CD ~/ak8s/Cloud_Build/b`

복사되었습니다!

content_copy

이전과 마찬가지로 `quickstart.sh`스크립트와 샘플 사용자 정의 클라우드 빌드 구성 파일 `cloudbuild.yaml`이 이 디렉토리에 제공되었습니다. 빌드한 컨테이너를 테스트하는 Cloud Build의 기능을 보여주기 위해 약간 수정되었습니다.

이전 작업에 사용된 것과 동일한 Dockerfile도 있습니다.

1. Cloud Shell에서 다음 명령어를 실행하여 의 콘텐츠를 봅니다 `cloudbuild.yaml`.

`고양이 cloudbuild.yaml`

복사되었습니다!

content_copy

다음이 표시됩니다.

`단계:

- 이름: 'gcr.io/cloud-builders/docker'
  인수: [ '빌드', '-t', 'gcr.io/$PROJECT_ID/quickstart-image', '.' ]
- 이름: 'gcr.io/$PROJECT_ID/quickstart-image'
  인수: ['실패']
  이미지:
- 'gcr.io/$PROJECT_ID/빠른 시작 이미지`

이전 작업 외에도 이 빌드 구성 파일 `quickstart-image`은 생성된 파일을 실행합니다. 이 작업에서 스크립트는 인수 가 전달 `quickstart.sh` 될 때 테스트 실패를 시뮬레이션하도록 수정되었습니다 .`['fail']`

1. Cloud Shell에서 다음 명령어를 실행하여 `cloudbuild.yaml`빌드 구성 파일로 사용하여 Cloud Build를 시작합니다.

`gcloud 빌드 submit --config cloudbuild.yaml .`

복사되었습니다!

content_copy

다음과 같은 텍스트로 끝나는 명령의 출력이 표시됩니다.

**산출**

`1단계 완료 오류 오류: 빌드 1단계 "gcr.io/ivil-charmer -227922 klabs-gcp -49 ab2930eea05/quickstart-image" 실패: 종료 상태 127 -------------------------------------------------- -------------------------------------------------- ------오류: (gcloud.builds.submit) 빌드 f3e94c28-fba4 -4012 -a419 -48 e90fca7491이 'FAILURE' 상태로 완료됨`

1. 명령 셸에서 빌드가 실패했음을 알고 있는지 확인합니다.

`에코 $?`

복사되었습니다!

content_copy

명령은 0이 아닌 값으로 응답합니다. 이 빌드를 스크립트에 포함했다면 스크립트가 빌드 실패 시 작동할 수 있습니다.

*내 진행 상황* 확인을 클릭 하여 목표를 확인합니다.

---

### 쿠버네티스 소개

쿠버네티스란?

1. 컨테이너 중심의 관리 환경으로 google에서 최초로 개발하여 오픈소스 커뮤니티에 제공
2. 현재는 cloud native computing foundation의 프로젝트
3. kubernetest는 컨테이너화된 애플리케이션의 배포,확장,부하 분산, 로깅, 모니터링, 기타 관리 기능을 자동화한다
4. Iaas 기능도 지원 예) 다양한 사용자 환경설정 , 구성 유연성
5. 선언적 구성 지원 , 일련의 명령어를 실행하는 게 아니라 달성하려는 상태를 설명하여 원하는 상태를 달성
6. 선언한 시스템을 자동으로 유지할 수 있다는 점은 쿠버네티스의 큰 장점이다

### GKE란?

1. GKE는 완전 관리형 서비스로 기본 리소스를 프로비저닝할 필요가 없다
2. GKE는 컨테이너 최적화 운영체제를 사용
3. kubernetes를 위한 google cloud의 관리형 서비스
4. GKE 클러스터 내에서 컨테이너를 호스팅하는 가상머신을 노드라고 한다
5. 오픈소스 kubernetes에는 대시보드가 포함되어 있지만 안전하게 설정하려면 상당한 노력이 필요 하지만 gcp 콘솔은 관리할 필요가 없는 GKE 클러스터 및 워크로드의 대시보드로 kubernetes 대시보드 보다 성능이 훨씬 우수하다
