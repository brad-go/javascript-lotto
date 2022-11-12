# :slot_machine: 우아한 테크 코스 3주차 미션 - 로또

## 목차

1. [미션 목표](#golf-미션-목표)
2. [게임 진행 방식](#game_die-게임-진행-방식)
3. [기능 목록](#rocket-기능-목록)

## :golf: 미션 목표

- **함수(또는 메서드)의 길이가 15라인을 넘어가지 않도록 구현**한다.
- **함수(또는 메서드)가 한 가지 일만 잘 하도록 구현**한다.
- `else`를 지양한다.
  - 힌트: `if` 조건절에서 값을 `return`하는 방식으로 구현하면 `else`를 사용하지 않아도 된다.
  - 때로는 `if/else`, `switch`문을 사용하는 것이 더 깔끔해 보일 수 있다. 어느 경우에 쓰는 것이 적절할지 스스로 고민해 본다.
- **도메인 로직에 단위 테스트를 구현**해야 한다. 단, UI(`Console.readLine`, `Console.print`) 로직에 대한 단위 테스트는 제외한다.
- **핵심 로직을 구현하는 코드와 UI를 담당하는 로직을 구분**한다.

## :game_die: 게임 진행 방식

아래와 같은 규칙으로 진행되는 로또 게임 기능을 구현합니다.

```
- 로또 번호의 숫자 범위는 1~45까지이다.
- 1개의 로또를 발행할 때 중복되지 않는 6개의 숫자를 뽑는다.
- 당첨 번호 추첨 시 중복되지 않는 숫자 6개와 보너스 번호 1개를 뽑는다.
- 당첨은 1등부터 5등까지 있다. 당첨 기준과 금액은 아래와 같다.
    - 1등: 6개 번호 일치 / 2,000,000,000원
    - 2등: 5개 번호 + 보너스 번호 일치 / 30,000,000원
    - 3등: 5개 번호 일치 / 1,500,000원
    - 4등: 4개 번호 일치 / 50,000원
    - 5등: 3개 번호 일치 / 5,000원
```

- 로또 구입 금액을 입력받습니다. (로또 1장의 가격은 1,000원)

```
14000
```

- 구입 금액에 해당하는 만큼 로또를 발행하며, 발행한 로또 수량 및 번호를 출력합니다. 로또 번호는 오름차순으로 정렬하여 보여줍니다.

```
8개를 구매했습니다.
[8, 21, 23, 41, 42, 43]
[3, 5, 11, 16, 32, 38]
[7, 11, 16, 35, 36, 44]
[1, 8, 11, 31, 41, 42]
[13, 14, 16, 38, 42, 45]
[7, 11, 30, 40, 42, 43]
[2, 13, 22, 32, 38, 45]
[1, 3, 5, 14, 22, 45]
```

- 당첨 번호를 입력받습니다.

```
1,2,3,4,5,6
```

- 보너스 번호를 입력받습니다.

```
7
```

- 사용자가 구매한 로또 번호와 당첨 번호를 비교합니다.
- 당첨 내역을 출력합니다.

```
3개 일치 (5,000원) - 1개
4개 일치 (50,000원) - 0개
5개 일치 (1,500,000원) - 0개
5개 일치, 보너스 볼 일치 (30,000,000원) - 0개
6개 일치 (2,000,000,000원) - 0개
```

- 수익률을 출력합니다. 수익률은 소수점 둘째 자리에서 반올림합니다. (ex. 100.0%, 51.5%, 1,000,000.0%)

```
총 수익률은 62.5%입니다.
```

- 로또 게임을 종료합니다.

#### 예외 상황

사용자가 잘못된 값을 입력할 경우 throw문을 사용해 예외를 발생시키고, "[ERROR]"로 시작하는 에러 메시지를 출력 후 종료합니다.

```
[ERROR] 로또 번호는 1부터 45 사이의 숫자여야 합니다.
```

#### 실행 결과 예시

```
구입금액을 입력해 주세요.
8000

8개를 구매했습니다.
[8, 21, 23, 41, 42, 43]
[3, 5, 11, 16, 32, 38]
[7, 11, 16, 35, 36, 44]
[1, 8, 11, 31, 41, 42]
[13, 14, 16, 38, 42, 45]
[7, 11, 30, 40, 42, 43]
[2, 13, 22, 32, 38, 45]
[1, 3, 5, 14, 22, 45]

당첨 번호를 입력해 주세요.
1,2,3,4,5,6

보너스 번호를 입력해 주세요.
7

당첨 통계
---
3개 일치 (5,000원) - 1개
4개 일치 (50,000원) - 0개
5개 일치 (1,500,000원) - 0개
5개 일치, 보너스 볼 일치 (30,000,000원) - 0개
6개 일치 (2,000,000,000원) - 0개
총 수익률은 62.5%입니다.
```

## :rocket: 기능 목록

### 입력 기능

[MissionUtils라이브러리](https://github.com/woowacourse-projects/javascript-mission-utils#mission-utils)에서 제공하는 `MissionUtils.Console.readLine`을 사용합니다.

- [ ] 로또 구입 금액 입력 받기

  - [ ] 1,000원 단위인지 확인하는 기능
  - [ ] 1,000원으로 나누어 떨어지지 않는 경우 예외 처리하기

- [ ] 당첨 번호 입력 받기

  - [ ] 쉽표를 기준으로 6자리의 당첨번호 입력 받기
  - [ ] 쉼표와 숫자가 아닌 다른 문자열의 경우 예외 처리하기
  - [ ] 숫자가 6자리가 넘어간 경우 예외 처리하기
  - [ ] 숫자가 쉼표로 구분되지 않았을 경우 예외 처리하기
  - [ ] 숫자가 1~45 사이의 수가 아니라면 예외 처리하기

- [ ] 보너스 번호 입력 받기
  - [ ] 1~45사이의 숫자가 아닌 경우 예외 처리하기
  - [ ] 하나의 숫자가 아닌 경우 예외 처리하기

### 출력 기능

[MissionUtils라이브러리](https://github.com/woowacourse-projects/javascript-mission-utils#mission-utils)에서 제공하는 `MissionUtils.Console.print`를 사용합니다.

```
8개를 구매했습니다.
[8, 21, 23, 41, 42, 43]
[3, 5, 11, 16, 32, 38]
[7, 11, 16, 35, 36, 44]
[1, 8, 11, 31, 41, 42]
[13, 14, 16, 38, 42, 45]
[7, 11, 30, 40, 42, 43]
[2, 13, 22, 32, 38, 45]
[1, 3, 5, 14, 22, 45]
```

- [ ] 발행한 로또에 대한 정보 출력하기
  - [ ] 입력 금액에 따른 발행한 로또의 수량 출력하기
  - [ ] 로또 번호를 오름차순으로 출력하기

```
3개 일치 (5,000원) - 1개
4개 일치 (50,000원) - 0개
5개 일치 (1,500,000원) - 0개
5개 일치, 보너스 볼 일치 (30,000,000원) - 0개
6개 일치 (2,000,000,000원) - 0개
```

- [ ] 당첨 내역 출력하기
  - [ ] 로또 번호와 당첨 번호 비교하는 기능
  - [ ] 모든 로또를 당첨 번호와 비교하기
  - [ ] 위와 같이 일치 개수에 따른 당첨 내역 출력하기

```
총 수익률은 62.5%입니다.
```

- [ ] 수익률 출력하기
  - [ ] 당첨된 총 금액 구하기
  - [ ] 입력받은 로또 구입 금액과 당첨금을 통해 수익률 계산하기
  - [ ] 수익률은 소수점 둘째 자리에서 반올림 하기

### 로또 발행

- [MissionUtils라이브러리](https://github.com/woowacourse-projects/javascript-mission-utils#mission-utils)에서 제공하는 `MissionUtils.Random.pickUniqueNumbersInRange` 를 사용합니다.
- 구현된 로또 클래스를 활용해 구현합니다.

```js
// 사용 예시
const numbers = MissionUtils.Random.pickUniqueNumbersInRange(1, 45, 6);
```

```js
// 로또 클래스
class Lotto {
  #numbers;

  constructor(numbers) {
    this.validate(numbers);
    this.#numbers = numbers;
  }

  validate(numbers) {
    if (numbers.length !== 6) {
      throw new Error();
    }
  }

  // TODO: 추가 기능 구현
}
```

- [x] 1~45 사이의 임의의 서로 다른 6자리 수를 생성하는 기능 - `LottoGenerator#createLottoNumbers`
- [ ] 생성한 6자리 수 오름차순으로 정렬하기 - `LottoGenrator#sortAscending`
- [ ] 생성한 6자리 수를 Lotto클래스에 넣어 로또 발행하기 - `LottoGenerator#createLotto`;
- [ ] 발행할 로또 개수(입력받은 금액 / 로또 가격(1,000))만큼 로또 생성하기