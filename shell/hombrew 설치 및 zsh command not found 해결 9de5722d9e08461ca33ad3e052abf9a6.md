# hombrew 설치 및 zsh: command not found 해결

터미널에서 버전확인을 위해 npm -v 입력했을 때 이런식으로 나오길래 당황해서 구글링으로 해결했는데 나중에 똑같은 에러가 발생했을 때를 위해 기록해 두려고한다.

```json
zsh: command not found: npm
zsh: command not found: node
```

또는 homebrew 설치를 위한 brew를 입력하면 똑같이 zsh 에러가 나타나는것을 확인할 수 있는데

/opt/homebrew 디렉토리 삭제 후 아래 방법으로 다시 설치하니 해결 됬었다.

### 1. /opt 디렉토리 이동

```bash
cd /opt
```

### 2. Homebrew 디렉토리를 만든다 (root 권한 필요)

```bash
sudo mkdir homebrew
```

### 3. /opt/homebrew 디렉토리의 소유권을 부여(root 권한이 필요 없도록)

```bash
sudo chown -R $(whoami) /opt/homebrew
```

### 4. homebrew를 다운로드하고 압축을 푼다.

```bash
curl -L https://github.com/Homebrew/brew/tarball/master | tar xz --strip 1 -C homebrew
```

### 5. homebrew/bin 디렉토리를 PATH에 추가한다. (zsh를 사용하지 않을 경우 직접 해야함)

```bash
echo "export PATH=/opt/homebrew/bin:$PATH" >> ~/.zshrc
```

### 6. 마지막으로 아래 명령어 실행

```bash
/bin/bash -c "$(curl -fsSL https://gist.githubusercontent.com/nrubin29/bea5aa83e8dfa91370fe83b62dad6dfa/raw/48f48f7fef21abb308e129a80b3214c2538fc611/homebrew_m1.sh)"
```