# Go 기반 CLI 프로젝트 – 이해하기 쉬운 간단한 예제 모음

Go 언어로 작성된 간단하고 구조가 명확한 CLI(명령줄 인터페이스) 프로젝트 예시를 소개합니다. 초보자도 쉽게 코드를 따라가며 CLI의 구조와 동작 원리를 익힐 수 있습니다.

---

## 1. Go CLI 템플릿

**설명:**  
CLI 프로젝트의 뼈대를 제공하는 템플릿. Cobra, urfave/cli 등 유명한 CLI 프레임워크를 활용하여 명령 구조와 플래그 파싱 등 기본 패턴을 익힐 수 있습니다.

**예시 레포:**  
- [spf13/cobra-cli](https://github.com/spf13/cobra-cli) (Cobra 프레임워크)
- [urfave/cli-example](https://github.com/urfave/cli-example) (urfave/cli 프레임워크)

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
