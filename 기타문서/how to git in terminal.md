# Terminal 에서 Git 사용하기
***By Kcrong***

<br>
<br>
<br>
## Content Table
**1. Git Clone
2. Edit, Commit, push
3. Git Branch
4. Will Added**



## Git Clone
![1](imgs/20160906-151554.png)

>`$ git clone [git url]` : git url 에 있는 리포지토리의 내용을 로컬로 복사합니다.

Window 기준으로 git.exe가 있는 경로에서 실행하면 됩니다.
Linux / MAC 기준으로는 설치하면 됩니다.


![2](imgs/20160906-152011.png)

>`$ touch testfile` : "testfile" 이름의 파일을 생성합니다. (용량 0)

>`$ echo "test_content" >> testfile` : "test_content" 를 testfile에 추가합니다.

clone 된 경로로 이동하여 파일을 추가하거나 소스를 수정합니다.

## Git Commit


![3](imgs/20160906-152104.png)

> `$ git status` : 현재 git 상황을 확인합니다. 

testfile 이 수정되었으나, 현재 *추적하지 않는 파일* 입니다. 우리는 이 파일의 버전관리를 할 예정이므로, 안내문 대로 `git add`를 해줍시다.

![4](imgs/20160906-152606.png)

> `$ git add testfile` : testfile을 git으로 추적합니다.

`git status`로 보면, testfile 색이 빨간색이던 `testfile`이 이젠 초록색으로 출력됩니다. 이는 해당 파일이 추적 되고 있는 상태라는 의미입니다.
<br>
이제 추적할 파일을 추가해주었으니, commit 을 할 차례입니다.

![5](imgs/20160906-152948.png)

> `git commit -m "Add testfile"` : git 커밋과 동시에 "Add testfile" 이라는 메세지를 남깁니다.

오류가 발생했습니다. 이 에러는 Git 설치 후 처음 이용하는 사람에게만 발생하는 오류니, 에러가 나지 않는 분들은 통과하시면 됩니다.
<br><br><br>

### 오류가 발생할 경우
![6](imgs/20160906-153453.png)

> `$ git config user.name "kcronglab"` : git 설정에 사용자명을 "kcronglab"으로 추가합니다.

> `$ git config user.email "kcrong@kim82536.pe.kr"` : git 설정에 사용자 이메일을 "kcrong@~" 으로 추가합니다.

>> (이때 사용자 명과 사용자 이메일은 원하는 것으로 해도 무방합니다.)

이제 커밋까지 완료한 상황입니다. 다시 `git status`로 상태를 보면

![7](imgs/20160906-153719.png)

커밋이 앞서있다고 합니다. 이제 로컬에 있는 소스 수정 커밋을 서버에 제출해야 합니다. `git push`를 이용하면 됩니다.

## Git Push

![8](imgs/20160906-154228.png)

`master branch` 로 제출 되었다고 합니다.

## Git Branch

`branch` 는 `commit` 의 흐름을 뜻합니다.
방금은 `master` 라는 `branch`에 testfile 수정사항이 `commit`&`push` 되었습니다.

이제는 개인 `branch`를 작성하여 `push` 해보도록 하겠습니다.


`branch`를 생성합니다.

![9](imgs/20160906-160128.png)

`branch` 가 `master` 에서 `kcrong` 으로 전환되었습니다.

이제 다시 수정사항을 만들고 `commit`&`push` 해보겠습니다.

![10](imgs/20160906-160427.png)

아까 사용했던 `$ git push` 을 타이핑하자 오류가 납니다. 로컬에서는 `kcrong` 이라는 `branch`가 생성되었으나, 서버에서는 `kcrong` 이라는 브랜치가 없는 탓입니다. 
서버에서도 `kcrong` 이라는 `branch` 를 생성해 주기 위해, 조금 긴 명령어를 사용합니다.

> `$ git push --set-upstream origin kcrong` : 현재 `branch`를 서버에도 추가합니다. 
(`remote branch`로 추가합니다.)

![11](imgs/20160906-160825.png)

`kcrong` 브랜치로 push 가 된 것을 확인할 수 있습니다.

이제 `kcrong` 에 쌓인 수정사항(`commit`) 을 `master` 에 합쳐 (`merge`) 해봅시다.

## Git Merge

![12](imgs/20160906-161422.png)

`merge`가 완성되었습니다.


## Git Conflict
`conflict`란 두 개 이상의 브랜치가 **동일한 부분을 수정**하거나, **수정이 겹친 상태**를 말합니다.

`dup1` 브랜치와 `dup2` 브랜치를 만들고, 겹치는 상황을 만들어 보도록 하겠습니다.

![13](imgs/20160907-084259.png)

testfile 에 "dup1" 내용을 추가하였습니다. (`dup1` 브랜치)

![14](imgs/20160907-084516.png)

`dup1` 브랜치에서 수정했던 부분에 `dup2` 브랜치에서도 같은 부분을 수정해줍니다.

이제 `dup1`과 `dup2`을 `master`로 `merge`하겠습니다.

![15](imgs/20160907-084842.png)

`merge` 가 실패했다고 합니다. 이제 충돌을 바로잡아 보도록 하겠습니다.

![16](imgs/20160907-084933.png)
![17](imgs/20160907-084955.png)
![18](imgs/20160907-085007.png)
![19](imgs/20160907-085102.png)

이렇게 conflict 상태의 두 커밋을 합쳐보았습니다. 