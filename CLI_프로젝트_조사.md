# Go 기반 CLI 프로젝트 – 이해하기 쉬운 간단한 예제 모음

Go 언어로 작성된 간단하고 구조가 명확한 CLI(명령줄 인터페이스) 프로젝트 예시를 소개합니다. 초보자도 쉽게 코드를 따라가며 CLI의 구조와 동작 원리를 익힐 수 있습니다.

---

## 1. Todo List CLI

**설명:**  
간단한 할 일(Task) 목록을 추가/삭제/조회할 수 있는 CLI 도구입니다.

**주요 기능:**  
- 할 일 추가  
- 할 일 목록 조회  
- 할 일 완료 체크 및 삭제

**예시 레포:**  
- [ayushbherwani1998/todo-cli](https://github.com/ayushbherwani1998/todo-cli)  
- [make-it/todo-cli](https://github.com/make-it/todo-cli)

---

## 2. Go CLI 템플릿

**설명:**  
CLI 프로젝트의 뼈대를 제공하는 템플릿. Cobra, urfave/cli 등 유명한 CLI 프레임워크를 활용하여 명령 구조와 플래그 파싱 등 기본 패턴을 익힐 수 있습니다.

**예시 레포:**  
- [spf13/cobra-cli](https://github.com/spf13/cobra-cli) (Cobra 프레임워크)
- [urfave/cli-example](https://github.com/urfave/cli-example) (urfave/cli 프레임워크)

---

## 3. 간단한 계산기 CLI

**설명:**  
사칙연산(+, -, *, /)을 명령줄에서 수행하는 기본 CLI 예제입니다.

**예시 레포:**  
- [TheAlgorithms/Go: calculator.go](https://github.com/TheAlgorithms/Go/blob/master/math/calculator.go)
- [abdfnx/calc-cli](https://github.com/abdfnx/calc-cli)

---

## 4. 파일 카운터(line/word/char count)

**설명:**  
파일의 라인 수, 단어 수, 문자 수를 세는 간단한 wc(Word Count) 클론입니다.

**예시 레포:**  
- [hakluke/how-to-exit-vim - wc.go](https://github.com/hakluke/how-to-exit-vim/blob/master/examples/wc.go)
- [gopherguides/wc-go](https://github.com/gopherguides/wc-go)

---

## 5. HTTP 요청 CLI

**설명:**  
curl처럼 동작하는 아주 간단한 http 요청 CLI 도구. URL을 입력하면 GET 결과를 출력합니다.

**예시 레포:**  
- [prashantgupta24/simplehttp](https://github.com/prashantgupta24/simplehttp)
- [subosito/gotenv/examples/http-client](https://github.com/subosito/gotenv/blob/master/examples/http-client/main.go)

---

## 예시 코드: Go로 만드는 간단 Todo CLI

아래는 가장 기본적인 Todo CLI 예시 코드입니다:

```go
package main

import (
    "bufio"
    "fmt"
    "os"
    "strings"
)

var todos []string

func main() {
    scanner := bufio.NewScanner(os.Stdin)
    for {
        fmt.Print("명령어(add/list/exit): ")
        scanner.Scan()
        input := scanner.Text()
        switch {
        case strings.HasPrefix(input, "add "):
            todo := strings.TrimPrefix(input, "add ")
            todos = append(todos, todo)
            fmt.Println("추가됨:", todo)
        case input == "list":
            fmt.Println("할 일 목록:")
            for i, todo := range todos {
                fmt.Printf("%d. %s\n", i+1, todo)
            }
        case input == "exit":
            fmt.Println("종료합니다.")
            return
        default:
            fmt.Println("알 수 없는 명령어입니다.")
        }
    }
}
```

---

## 참고

- Go 공식문서의 [Command-Line Interface Applications](https://golangdocs.com/cli-applications-in-golang) 섹션도 참고해보세요.
- 원하는 예제의 종류(예: todo, 계산기, 파일 처리 등)가 있으면 더 구체적으로 추천해 드릴 수 있습니다!
