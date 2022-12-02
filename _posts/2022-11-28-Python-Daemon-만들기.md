---
title: '[Python] Python Daemon 만들기'
author: SongEun
date: 2022-11-28 12:01:00 +0000
categories: [Dev]
tags: [Python, Daemon]
math: true
mermaid: true
---

최근에 파이썬으로 데몬 만들일이 있었는데 만들면서 삽질한 내용 기록

## **Prerequisites**
+ python-daemon
+ lockfile

## **Code**

### 1. Python Daemon (util.py)

파이썬 daemon 라이브러리에 runner라는 함수가 있는데, 제대로 작동하지 않는다.

찾아보니 더 이상의 코드 업데이트를 지원하지 않는다고 한다. 기존의 코드를 python 3에 맞도록 수정한 [참고 코드](https://gist.github.com/ssong812/a5bf5701ec4cb03db98eda6ccfb79482)를 이용하였다.

### 2. 실행 코드 (run.py)

```python
import os
import util as runner
import logging

def something_to_do(): 
    print("Working ..")
    time.sleep(1)

class App():
    def __init__(self, base_path):
        self.stdin_path = '/dev/null'
        self.stdout_path = '/dev/null'
        self.stderr_path = '/dev/null'
        self.pidfile_path =  os.path.join(base_path, 'daemon.pid')
        self.log_file = os.path.join(base_path, 'daemon.log')
        self.pidfile_timeout = 5

    def run(self):
        logging.basicConfig(level=logging.DEBUG,
                format='%(asctime)s %(levelname)s %(message)s',
                filename=self.log_file,
                filemode='a')

        while True:
            something_to_do()
           
if __name__ == '__main__':

    base_path = '/path/to/contain/pid/and/log'

    daemon_runner = runner.DaemonRunner(App(base_path))
    daemon_runner.do_action()
```

### 3. 실행 방법

```bash
python run.py start
python run.py stop
python run.py restart
```

<br>

___

## **Reference**

+ [https://peps.python.org/pep-3143/](https://peps.python.org/pep-3143/)
+ [https://dinist.tistory.com/26](https://dinist.tistory.com/26)
+ [https://gist.github.com/mgmarino/2df6ecff0de3536c5c16](https://gist.github.com/mgmarino/2df6ecff0de3536c5c16)
+ [https://gist.github.com/kenmoini/fb840813e4538a9aeb94d47c4d914234](https://gist.github.com/kenmoini/fb840813e4538a9aeb94d47c4d914234)
