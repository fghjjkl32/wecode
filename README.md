# git 정리

## 저장소 생성하기

Git 저장소를 생성하는 방법이다.

```bash
 git init
```

이 명령어는 프로젝트 폴더 내에 숨겨진 **.git 디렉토리를 생성**한다.
이제 Git은 현재 저장소에 대한 모든 변경사항을 추적/관리하게 된다. ** 단 `git init`을 했다고 하여 바로 버전관리를 하는 것은 아니다.**

---

## 상태확인

터미널에서 다음 명령어를 입력하여 repository의 현재 상태를 확인할 수 있다.

```bash
git status
```

작업 디렉토리와 스테이징 영역의 상태를 확인하기 위해서 사용되는 명령어

위 명령어는 Git으로 작업 할 때 굉장히 자주 사용되는 명령어입니다. 어떤 파일이 변경되었는지, 어떤 파일이 추가되었는지 등을 전부 보여준다.

이 명령어들도 상태확인할때 하는 명령어다.

```bash
git diff
```

수정된 파일에서 어떠한 부분이 달라졌는지 확인하는 명령어

```bash
git log
```

commit의 이력을 확인하는 명령어

---

## 변경하기

### git add

작업 디렉토리 상의 변경 내용을 스테이징 영역에 추가하기 위해서 사용하는 명령어

```bash
git add <파일/디렉토릭 경로>
```

여러개의 파일들을 추가하고 싶다면 아래와 같이 할 수 있다.

```bash
ex) git add file.js file2.js file3.js
```

```bash
git add .
```

파일을 각각 추가하지 않고, 아래와 같이 모든 파일을 한번에 추가할 수도 있다.

---

### git commit

commit이란? git이 폴더의 변경 내용을 저장하는 명령어

```bash
git commit -m "변경된 사항에 대한 설명"
```

스테이징 영역에 추가된 파일을 메세지와 함께 로컬저장소로 커밋하는 명령어

add가 장바구니에 담는거라면 구매하는것은 commit이라고 생각이든다.

---

## Branch

### Branches

브랜치란 독립적으로 어떤 작업을 진행하기 위한 개념이다. 필요에 의해 만들어지는 각각의 브랜치는 다른 브랜치의 영향을 받지 않기 때문에, 여러 작업을 동시에 진행 할 수 있다.

### Creating a new branch (브랜치 생성하기)

아래 명령어를 통해 새로운 브랜치를 생성할 수 있다.

```bash
git branch <new-branch-name>
```

새로 만들어진 브랜치는 현재 프로젝트의 코드를 그대로 반영하여 생성된다.

### Changing branches (브랜치 전환하기)

아래 명령어를 통해 다른 브랜치로 이동할 수 있다.

```bash
git checkout <branch-name>
```

원하는 브랜치로 이동하면, 해당 브랜치에만 영향을 주게 된다. 그런 다음 다른 브랜치로 이동하여 작업 할 수 있으며, 이전 브랜치의 변경 사항 및 커밋의 영향을 받지 않는다.

프로젝트에 존재하는 모든 브랜치를 확인하고 싶다면 `git branch` 명령어를 입력하면 된다.

### Merging branches (브랜치 병합하기)

A라는 브랜치에서 작업한 내용과 B라는 브랜치에 적용하고 싶을때 병합하여 합칠 수 있다.
예를 들면 특정 브랜치에서 새로운 기능을 구현하고 테스트 완료한 시점이라면, 기준이 되는 main 브랜치에 구현내용을 적용하기 위해 merge을 사용한다.

아래 명령어를 통해 다른 브랜치를 현재 브랜치와 병합할 수 있다.

```bash
git merge <branch-name>
```

### Deleting a branch (브랜치 삭제하기)

아래 명령어를 통해, 브랜치를 삭제할 수 있다.

```bash
>git branch -d <branch-name>
```

지난글에서 git명령어를 적고나서 그 이후인 깃허브에 호스팅을 해보자.

# 내 로컬 Repository를 github에 push하기

## 1. repository 생성하기

GitHub repository 를 생성하려면, [github.com](http://github.com) 으로 이동 후 우측 상단 + 버튼을 누른 뒤 **'New repository'** 라는 옵션을 선택한다.

![](https://images.velog.io/images/rain98/post/9599cbb8-d420-42c4-8377-15fb1b8ce08e/%E1%84%89%E1%85%B3%E1%84%8F%E1%85%B3%E1%84%85%E1%85%B5%E1%86%AB%E1%84%89%E1%85%A3%E1%86%BA%202021-05-22%20%E1%84%8B%E1%85%A9%E1%84%92%E1%85%AE%2010.15.52.png)

repository 이름을 정하고 생성한다.
![](https://images.velog.io/images/rain98/post/eb5357c6-4893-48c6-b091-2d06c6a9a07a/IMG_B310E44B7510-1.jpeg)

파란색 박스로 쳐져 있는것은

- public/private 공개/비공개
  주로 아직 미공개중인 서비스를 구현하거나 민감한 코드일때 비공개한다.
- Add a README file
  프로젝트 설명 적을 수 있는 파일 추가 여부
- Add .gitignore
  gitignore 에다 정보를 넣으면 그 정보는 제외하여 push가 된다. 주로 보안상 민감한 정보(아이디,패스워드)나 너무 큰 파일(node.modules)이 있는 경우 해당한다.
- Choose a license
  권한 설정

## 2. repository 에 코드 push 하기

**'Create repository'** 버튼을 누르게 되면 새로 만든 GitHub repository 의 스타팅 페이지로 이동하게 된다.
![](https://images.velog.io/images/rain98/post/e84a2caf-f570-4b5d-a02c-4dac25a02a8c/IMG_C76654BF3771-1.jpeg)
이 링크를 복사한 다음 복사한 링크를 여기다 붙여 놓는다.
`git remote add origin "링크붙여놓기".git`

remote 명령어로 깃허브 링크 붙인 repository로 연결 시켜준다.

**git push** 명령어는 로컬 Git repository 의 코드를 GitHub repository 로 업로드 해준다.

```bash
git remote add origin https://github.com/<your-username>/<your-repo-name>.git
git push -u origin marster
```

**최근 메인 브런치의 이름이 master -> main으로 바꼇다고 한다. 만약 변경이 안된다면 main으로 바꿔서 진행해보자.**

처음 **git push** 명령어를 실행하면 GitHub 유저네임과 비밀번호를 입력하라는 prompt 가 뜨게 된다. 깃허브 로그인을 하면된다.

repository 가 성공적으로 push 되었다면, 전에 만든 GitHub repo 페이지로 가서 새로고침하면 로컬에서 push 한 코드가 해당 remote repository 로 업로드 된 것을 확인할 수 있다.

## 3. repository 에 변경사항 남기기

** 로컬 Git repo를 GitHub remote repo 와 연결 후 push 까지 했다고 로컬에서 작업한 내용들이 자동으로 remote 에 반영되는 것은 아니다. 그래서 변경사항이 있으면 다시 push 를 해줘야 GitHub repo 가 업데이트 된다. **

예를 들어,

```jsx
console.log("hello-javascript");
```

위와 같이 콘솔로그문을 이미 가지고 있는 js 파일에 추가해주거나, 변경을 해준다음 저장 후 커밋을 위해 **add 후 커밋메세지를 남겨줍니다.**

```bash
git add .
git commit -m "Change greeting"
```

커밋을 한 뒤, 아래 명령어를 입력해서 업데이트 된 로컬 repo를 GitHub repo로 push 해줘야 변경이 완료된다.

```bash
git push origin master
```

# 풀 리퀘스트 보내기

## 1. repository 클론하기 (clone)

로컬에서 Git repository 를 생성한 뒤 리모트 GitHub repository 를 연결해주는 예시랑 다르게 이번은 GitHub repo 를 먼저 생성한 뒤 **clone** 을 받아 내 로컬환경에 다운로드 후 프로젝트를 시작하는 방법도 있다.

**먼저 배포된 프로젝트를 다운받아서 사용하거나 오픈소스를 받고 만들때 가장 많이 사용하는 방법이다.**

repository 를 **clone** 하기 위해서 복사할 repository로 이동후 'code' 라는 초록색 버튼을 누른 뒤 아래 복사 아이콘을 클릭해준다.

![](https://images.velog.io/images/rain98/post/16a9c875-a5a9-471d-a237-4840ea33b633/IMG_F979375AA459-1.jpeg)

그 다음 해당 remote repository 를 내 컴퓨터로 받아오기 위해, 해당 repo 를 다운로드 받고 싶은 경로로 이동한 뒤 **git clone** 명령어에 방금 복사해준 URL 을 붙여주고 실행해준다.

```bash
git clone <github-repo-link>
```

이렇게 다른 개발자들의 public repository 를 클론받아 작업할 수 있다.

## 2. Branching and merging

![](https://images.velog.io/images/rain98/post/0c2cab0c-35f4-4e23-a732-5e1e8b6389b4/%E1%84%83%E1%85%A1%E1%84%8B%E1%85%AE%E1%86%AB%E1%84%85%E1%85%A9%E1%84%83%E1%85%B3.png)

일반적으로 GitHub repository 의 **master** 브랜치는 항상 잘 작동하고 안정적인 버전의 코드를 포함하고 있어야 한다. 하지만, 새로 추가할 기능을 추가하거나 테스트를 아직 해보지 않은 코드를 push 할때 어떻게 해야할까?

이럴 때 **Branch** 가 필요하다. 브랜치를 사용해서 현재 프로젝트의 코드를 그대로 복제하여 작업 환경을 만들 수 있습니다. 그렇게 된다면, master 브랜치를 건드릴 필요없이 작업환경에서 기능을 추가하거나 테스트를 진행할 수 있게 되는것이다. 나중에 전부 완료가 된다면, 그 때 **master** 브랜치와 새로 생성한 브랜치와 (merge) 병합 해줄 수 있다.

## 2-1. GitHub 에 브랜치 push 하기

예를 들어 **hello-javascript** 프로젝트에 새로운 파일을 추가하고 싶다면, 우선 아래 명령어를 통해 새로운 **브랜치를 생성하고 이동해야** 한다.

이전글에서 사용한 branch를 사용하여 생성한다음

```bash
git branch feature/greetings
```

이동을 생성한 브랜치로 해준다
checkout명령어는 해당 브랜치로 이동해주는 명령어다

```bash
git branch
```

이 명령어를 사용해준다면 해당 브랜치가 몇개있는지, 어디에 위치해있는지 볼 수 있다.

```bash
git checkout feature/greetings
```

브랜치 이름은 보통 feature/"원하는이름" 으로 설정한다.

그런 다음, **example.js** 라는 파일을 만들고 코드를 수정해준다.

```jsx
console.log("Hello React!");
```

그런 뒤, 우리가 이제 익히 알고있는 커밋 절차를 거쳐 변경사항을 커밋해준다.

```bash
git add .
git commit -m "Add: greetings"
```

이제 push를 통해 **feature/greetings** 브랜치를 remote 로 올려준다.

```bash
git push origin feature/greetings
```

## 3. Pull Request (PR) 생성하기

커스텀 브랜치를 push 하고 master 브랜치에 적용될 준비가 되었다면, **Pull Request (PR)** 라는 것을 통해 프로젝트 오너 혹은 팀 리더(권한을 가지고 있는 개발자) 에게 내가 작업한 브랜치의 작업내용을 master 브랜치에 반영해달라는 요청을 보낼 수 있다.
이 요청을 보내는것이 Pull Request다.

master 브랜치로 합쳐지기 전에 확인해야하기 때문에 권한을 가지고 있는 개발자들이 변경사항을 확인할 수 있다.

github 페이지로 들어가 Pull Request 를 생성할 수 있는 페이지로 이동할 수 있다.
거기서 해당 PR의 제목과 어떤 내용을 담고 있는지 설명하는 Description을 작성할 수 있다. 작성하는 문서는 마크다운 문서 형식이다.

완료 했다면 이때부터는 함께 협업하는 개발자들이 방금 만든 PR을 리뷰, 분석하고 댓글까지 달아줄 수 있다.

모든 리뷰 내용이 반영된 후 **master** 브랜치와 충돌이 발생하지 않았다면, 해당 PR은 master 브랜치로 merge 될 준비가 완료되었다.

## 4. GitHub 으로부터 변경사항 pull 하기

Pull Request 를 통해 master 브랜치를 업데이트했다면, 이제 로컬 repository 는 GitHub 에 있는 master와 서로 다른 내용을 가지고 있게 됩니다. 이 때 **git pull** 명령어를 통해 remote 의 최신화된 코드를 내 로컬 repo 에 반영할 수 있다.

우리는 GitHub remote repo 링크에 **origin** 이라는 이름을 붙여줬었기 때문에 아래 명령어를 통해 GitHub repo 의 master 브랜치 내용을 받아올 수 있다.

```bash
git pull origin master
```

---

# 요약

## 1. 새로운 repository 생성

Github 페이지에서 새로운 repository 생성 후에 로컬에서 작업한 내용을 올리기 위한 명령어 순서

> 명령어 입력 순서

1. git init

2. git add .
3. git commit -m “commit message”
4. git remote add origin repostory주소
5. git push -u origin master

- 1번으로 현재 작업중인 폴더에서 git을 사용할 수 있도록 해주고
- 2번으로 폴더 내의 모든 파일(.이 모든 파일을 의미)을 git의 staging area에 추가
- 3번으로 커밋과 동시에 -m으로 커밋 메세지 작성

  > 📌 **git add와 commit전후 git status를 해서 무엇이 변경되었는지 항상 확인해주는 습관 잊지말자**

- 4번으로 원격 저장소, 즉 github repository 주소를 origin 이라는 이름으로 등록
- 5번으로 origin이라는 원격 저장소에 master 브랜치에 푸시, 이때 -u를 쓴다면 다음번 부터 git push만 입력해도 origin의 master로 푸시가 된다.

---

## 2. 1번 이후에 새로운 변경 사항이 있을 때

1번 과정 이후에 변경 사항이 있어 push를 하고 싶을 때 순서

> 명령어 입력 순서

1. git add .
2. git commit -m “commit message”
3. git push

과정은 1번과 같으나 init과 원격 저장소 등록을 할 필요가 없다

---

## 3. branch, merge 사용법

협업을 할 때 많이 쓰는 기능 branch, merge 이름 그대로 가지를 치고, 합치는 방법이다

> 명령어 입력 순서

1. git branch 브랜치이름설정

2. git checkout 브랜치이름

3. git add .

4. git commit -m “commit message”
5. git push origin 브랜치이름

- 1번으로 새로운 브랜치를 생성(기존 브랜치는 master)

- 2번으로 생성한 브랜치로 이동

- 3번으로 모든 파일 추가

- 4번으로 커밋, 메세지 작성

- 5번으로 origin 저장소의 새로운 브랜치에 푸시

브랜치에 푸시까지 완료 한 뒤

git checkout master
git merge 브랜치이름
위의 과정으로 master에 새로운 브랜치를 merge할 수 있다

---

## 4. 충돌 시 해결 방법

pull이나 push를 했을 때 원격저장소의 내용과 로컬폴더내의 내용중 같은 라인에 다른 내용이 있다면 충돌 발생

터미널 로그에 충돌이 난 파일이 표시되니 직접 수정 후 다시 pull이나 push를 실행

가장 좋은 방법은 협업자들끼리 역할을 완전히 분담해 애초에 같은 코드를 건드리지 않는 것이지만, 어쩔 수 없이 그렇게 된다면 항상 작업 전에 pull을 습관화하면 충돌을 최소한으로 줄일 수 있을 것이다

---

## 5. 풀 리퀘스트 보내기

내가 push한 내용을 repository의 마스터 권한을 가진 사람에게 pull 해달라고 요청하는것

우선 참여하고 싶은 repository에 들어가 오른쪽 상단의 fork로 나의 repository에 복사해온다음

> 명령어 입력 순서

1. git clone 원본repository주소

2. git remote add 나의repo이름설정 나의repo주소

3. git remote -v

4. git pull origin
5. git checkout -b 브랜치이름(이슈)설정 origin/master
6. git push 나의repo이름 브랜치이름

- 1번으로 원본 repo의 코드들을 나의 로컬환경에 클론해온다.

- 2번으로 포크해온 나의 repo주소를 새로운 이름으로 추가해준다.

- 3번으로 현재 등록되어있는 원격저장소가 어떤게 있나 확인해본다. 아마 origin이라는 이름의 원본 repo주소와 새로 설정한 이름의 나의repo주소가 있을 것이다

- 4번으로 혹시 모를 코드변화가 있을 수 있으니 한번 pull해서 확인해준다

- 5번으로 원본repo에 이슈명이나 키워드로 브랜치를 생성하고 이동한다

모든 작업 후에 6번으로 나의 repo에 푸시한다.
