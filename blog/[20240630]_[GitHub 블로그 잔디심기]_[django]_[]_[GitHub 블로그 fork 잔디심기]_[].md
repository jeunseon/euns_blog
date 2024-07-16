# GitHub Blog 잔디 심기

Fork 로 가져온 repository는 commit 해도 잔디가 심어지지 않는다.

## <span style="color:#1a5490;">블로그로 깃헙 잔디 심기 1</span>

Fork로 가져오지 않고 < Code 로 다운로드하여 가져올 경우

<span style="color:red;">★ 저작권 문제로 public으로 저장소를 만들면 안되고 private 하게 만든다.</span>

1. Fork 로 가져오면 단디가 심어지지 않아서 < Code 버튼을 눌러 다운로드 한다. 
2. repository (저장소) 새로 만든 후 다운로드한 파일의 내용만 업로드 한다.
3. github pages에서 배포한다.

----

## <span style="color:#1a5490;">블로그로 깃헙 잔디 심기 2 (글, 링크, commit 포함)</span>

<span style="color:red; font-size:12px;">
※ 윈도우 검색창에 git bash 를 검색하여 git bash에서 입력을 한다. <br />
→ git bash 노트북 복사 키  : CTRL + FN + INSERT키 <br />
→ git bash 노트북 붙여넣기 키  : SHIFT + FN + INSERT키
</span>
<br />
<br />
<span style="color:#006dd7; font-weight:bold;">

1. GitHub 에 새로운 repository (저장소) 생성

2. < Code 에서 HTTPS 주소 복사하여 Git Bash에서 bare clone
```bash
git clone --bare 복사할 레포지토리 주소
```

3. 로컬에서 해당 파일로 이동
```bash
cd 복사한 레포.git

-> 복사한 레포.git 은 bare clone 을 한 뒤 .git 파일 이름이 뜬다.
```

4. mirror-push 로 새로운 레파지토리에 push 한다.
```bash
git push --mirror 새로 생성한 레포 주소
```

5. 처음에 임시로 생성했던 로컬 레파지토리 삭제
```bash
cd ..
rm -rf 복사한 레포.git
```
</span>

<span style="color:red; font-size:12px;">
→ cd ..    로 이전 경로로 이동 <br />
→  rm -rf 를 이용하기 위해 Git Bash 에서 해당 내용을 입력한다.
</span>