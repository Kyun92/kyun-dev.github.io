---
layout: post
title: 블로그 테스트
tags: [Typescirpt]
---

자바스크립트에서 같은 동작을 하는 함수가 존재하더라도 타입에 따라 다른 결과가 나오는 경우가 있다. 더하기 함수에서 우리는 인자를 number 만 받던지 string만 받던지 정하고 싶다고 하자.

```
    const a = {
    	add: (a: number, b: number): number => a + b,
    	add: (a: string, b: string): string => a + b
    }

    // 함수명 중복 발생
```

위 함수는 같은 동작을 하지만, 인자의 타입에 따라 다른 타입을 뽑아내고 싶은 경우가 있다.

하지만 저렇게 같은 이름으로 선언하면 중복됐다고 선언되지 않고 그렇다고 타입을 느슨하게 설정하면

```
    const a = {
    	add: (a: number | string, b: number | string): number | string => a + b,
    }

    // a.add(1 + 'abc') 문제 발생!
```

의도하지 않은 결과가 나올 수도 있다.

이를 방지하기위해 등장한 것이 제네릭 일명 짝맞추기이다.

```
    interface object<T> {
    	add: (a: T, b: T) => T;
    }

    const a: obj<number> = {
    	add:(a, b) => a + b,
    }

    const b: obj<string> = {
    	add:(a, b) => a + b,
    }
```

## extends - 제네릭 제한두기

```
    interface obj<T extends string> {
    	...
    }
```

이렇게 하면 T를 string으로 제한 할 수 있다. string 자리에는 interface, type 모두 올 수 있다.

![?](https://www.notion.so/lukalim/Generic-17e306fe33714b74a296a99288372352#e108aecc42024bb0ab7ef4b72b95288e)

→ 제네릭을 이용한 `forEach` 함수 구현 `item` 의 타입이 자동으로 추론 된다.
