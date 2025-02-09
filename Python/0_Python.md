#### **[Python]**
#1. [Data Type](#250120-250121--python--data-type)<br>
#2. [Function](#250122--function)<br>
#3. [Module / 제어문](#250123--모듈--조건문--반복문)<br>
#4. [Data Structure / Method / Copy](#250124-250131--data-structure-method--copy)<br>
#5. [OOP](#250203-250204--oop)<br><br>


# **250120-250121 | <Python / Data Type>**

## **[1] Python**
### 1. Python
#### 1) 기본 개념

|용어|개념|
|:-:|----|
|**문장(Statement)**|- 실행 가능한 동작을 기술하는 코드.|
|**표현식(Expression)**|- 값으로 평가될 수 있는 코드 조각.<br>- 표현식 ⊂ 문장.|
|**값(Value)**|- 표현식이 평가된 결과.|
|**평가(Evaluate)**|- 표현식을 순차적으로 실행하여 값을 얻는 과정.<br>- 프로그램의 동작을 결정.|
|**변수(Variable)**|- 값을 저장하기 위한 이름.|
|**타입(Type)**|- 변수나 값이 가질 수 있는 데이터의 종류.|
|**변수 할당**|- 표현식을 통해 변수에 값을 저장.|

## **[2] Data Type**
### 1. Data Type
#### 1) Data Type
|분류|종류|
|:-:|:--:|
|**Numeric Type**|int, float, complex(복소수)|
|**Sequence Type**|list, tuple, range, str|
|**Non-sequence Type**|set, dict|
|**ETC**|Boolean, None, Function|

### 2. Numeric Type
#### 1) `int` (정수형)
- 개념
    - 정수를 표현하는 자료형.
- 코드
    ```python
    int_1 = 10
    int_2 = 0
    int_3 = -5
    ```

#### 2) `float` (실수형)
- 개념
    - 실수를 표현하는 자료형.
- 코드
    ```python
    float_1 = 3.14
    float_2 = -4.28

    # e 활용 : 314 * 0.01
    float_3 = 314e-2
    ```
- **⭐ 부동소수점 에러**
    - 컴퓨터가 실수를 표현하는 방식(근삿값값)으로 인해 발생하는 작은 오차.<br>
    → `decimal` 모듈을 사용하여 부동소수점 연산의 정확성을 보장.
    ```python
    from decimal import Decimal
    print(Decimal('3.2') - Decimal('3.1')) # 0.1
    print(Decimal('1.1') - Decimal('1.0')) # 0.1
    ```

### 3. Sequence Type
#### 1) Sequence Type
- 개념
    - 여러 개의 값들을 순서대로 나열하여 저장하는 자료형.
- 특징
    1. 순서(Sequence)
        - 값들이 순서대로 저장(정렬 X).
    2. 인덱싱(Indexing)
        - 각 값이 고유한 인덱스(번호)를 가지고 있어 특정 위치의 값 선택 및 수정 可.
    3. 슬라이싱(Slicing)
        - 인덱스 범위를 조절하여 부분적인 값 추출 可.
    4. 길이(Length)
        - 저장된 값의 개수(길이)를 구하기 위해 `len()` 함수 사용.
    5. 반복(Iteration)
        - 저장된 값을 반복적으로 처리하기 위해 반복문 사용.

#### 2) ⭐ `str` (문자열)
- 개념
    - 순서가 있는 문자들 저장, **변경 不可**.
- 특징
    - 문자열 변경 관련 함수는 새로운 주소를 받는 새로운 값을 생성.
- Escape Sequence
    - `\n`, `\t`, `\\`, `\'`, `\"`
- String Interpolation
    - f-string
- 코드
    ```python
    # str
    str_1 = 'hello'
    str_2 = "world"

    # f-string
    print(f'hello {str_3}!')   # hello world!

    # Indexing
    str_3[0]   # p
    str_3[-1]  # n

    # Slicing
    str_3[:3]     # pyt
    str_3[2:5]    # tho
    str_3[2:5:2]  # to
    str_3[::-1]   # nohtyp
    ```

#### 3) ⭐ `list`
- 개념
    - 여러 개의 값을 순서대로 저장, **변경 可**.
- 코드
    ```python
    # list
    lst_1 = []
    lst_2 = [1, 'a', 2, 'b']
    lst_3 = [1, 2, 'hello', ['my', 'world']]

    # Length
    print(len(lst_3))   # 4

    # Indexing
    print(lst_3[0])     # 1

    # Slicing
    print(lst_3[:3])    # [1, 2, 'hello']
    print(lst_3[::2])   # [1, 'hello']
    print(lst_3[::-1])  # [['my', 'world'], 'hello', 2, 1]

    # 가변
    lst_3[0] = 100
    print(lst_3)        # [100, 2, 'hello', ['my', 'world']]
    ```

#### 4) `tuple`
- 개념
    - 여러 개의 값을 순서대로 저장, **변경 不可**.
    - 다중 할당, 값 교환, 그룹화, 함수 다중 반환 값 등 내부 동작에 주로 활용.
- 특징
    - 단일 요소 튜플은 반드시 Trailing Comma(후행 쉼표) 필요.
    - 본체는 Comma(,)에 있음
- 코드
    ```python
    # tuple
    tpl_1 = ()
    tpl_2 = (1,)
    tpl_3 = 1,
    tpl_4 = (1, 'a', 2, 'b')

    # Length
    print(len(tpl_4))   # 4

    # Indexing
    print(tpl_4[0])     # 1

    # Slicing
    print(tpl_4[:3])    # [1, 2, 'hello']
    print(tpl_4[::2])   # [1, 'hello']
    print(tpl_4[::-1])  # [['my', 'world'], 'hello', 2, 1]

    # 불변
    # TypeError: 'tuple' objeect does not support item assignment
    tpl_4[0] = 100
    ```

#### 5) `range`
- 개념
    - 연속된 정수 시퀀스 생성, **변경 不可**.
    - 주로 반복문과 활용.
- 특징
    - 양수 증가 시, 시작 값 < 끝 값.
    - 음수 증가 시, 시작 값 > 끝 값.
- 코드
    ```python
    # range(시작, 끝, 증가)
    rng_1 = range(4)
    rng_2 = range(1, 3)
    rng_3 = range(5, 0, -1)

    # 기본 print
    print(rng_1)        # range(0, 4)

    # 형 변환 후 print
    print(list(rng_1))  # [0, 1, 2, 3]
    print(list(rng_2))  # [1, 2]
    print(list(rng_3))  # [5, 4, 3, 2, 1]
    ```

### 4. Non-Sequence Type
#### 1) ⭐ `dict`
- 개념
    - key-value 쌍, **순서 無, 중복 無, 변경 可**.
- 특징
    - key : 변경 不可 자료형(str, int, float, tuple, range, ...).
    - value : 모든 자료형.
    - <span style="color:red">해당 dict의 마지막 key는 무엇이냐?</span> ❌ ; 순서 無.
- 코드
    ```python
    # dict
    dct_1 = {}
    dct_2 = {'key' : 'value'}
    dct_3 = {'apple' : 12, 'list' : [1, 2, 3]}

    # add
    dct_3['banana'] = 50
    print(dct_3) # {'apple' : 12, 'list' : [1, 2, 3], 'banana' : 50}

    # change
    dct_3['apple'] = 100
    print(dct_3) # {'apple' : 100, 'list' : [1, 2, 3], 'banana' : 50}
    ```

#### 2) set
- 개념
    - **순서 無, 중복 無, 변경 可**.
- 특징
    - 집합 연산을 위한 자료형.
    - <span style="color:red">해당 set의 첫 번째 요소는 무엇이냐?</span> ❌ ; 순서 無.
- 코드
    ```python
    # set
    set_1 = set() # 중괄호는 dict!
    set_2 = {1, 1, 3}
    set_3 = {3, 5, 7}

    # check
    print(set_1)         # set()
    print(set_2)         # {1, 3}
    print(set_3)         # {3, 5, 7}

    # 값 변경
    set_1.add(2)         # {2}
    set_1.remove(2)      # set()

    # 합집합
    print(set_2 | set_3) # {1, 3, 5, 7}

    # 차집합
    print(set_2 - set_3) # {1}

    # 교집합
    print(set_2 & set_3) # {3}
    ```

### 5. Other Types
#### 1) `None`
- 개념
    - in 파이썬, **'값이 없음'**을 표현.
- 코드
    ```python
    # None
    val_1 = None
    print(val_1) # None
    ```

#### 2) `Boolean`
- 개념
    - **True**와 **False**를 표현.
- 코드
    ```python
    # None
    bool_1 = True

    print(bool_1)    # True
    print(3 < 1)     # False
    print(3 != '3')  # True
    ```

#### 3) Collection
- 개념
    - 여러 개의 항목 / 요소를 담는 자료 구조.
- 특징
    |구조|값 변경 可|순서 有|
    |:--:|:-------:|:----:|
    |str|X|O|
    |list|O|O|
    |tuple|X|O|
    |dict|O|X|
    |set|O|X|
- 코드
    ```python
    # None
    bool_1 = True

    print(bool_1)    # True
    print(3 < 1)     # False
    print(3 != '3')  # True
    ```

### 6. 형변환 (Type Conversion)
#### 1) 암시적 형변환 (Implicit Type Conversion)
- 개념
    - 파이썬이 자동으로 수행하는 형변환.
- 특징
    - Boolean & Numeric Type 可. 
    - in 정수 & 실수 연산 可 (정수 → 실수).
- 코드
    ```python
    print(3 + 5.0)   # 8.0
    print(True + 3)  # 4
    ```

#### 2) 명시적 형변환 (Explicit Type Conversion)
- 개념
    - 프로그래머가 직접 지정하는 형변환.
    - 암시적 형변환이 아닌 모든 경우.
- 코드
    ```python
    # str → int : 형식에 맞는 숫자 可.
    print(int(3.5))        # 3
    print(float('3.5'))    # 3.5
    # print(int('3.5'))    # ValueError

    # int → str : 모두 可.
    print(str(3) + '등')   # 3등
    ```

## **[3] 연산자**
### 1. 연산자
#### 1) 산술 연산자
- 종류
    - `+`, `-`, `*`, `/`, `//`, `%`, `**`
- 우선순위
    |우선순위|연산자|
    |:----:|:----:|
    |↑|**|
    | |- (음수)|
    | |*, /, //, %|
    |↓|+, -|

#### 2) 복합 연산자
- 개념
    - <span style="background-color:lightgray"> $a = a + b$</span> → <span style="background-color:lightgray"> $a += b$ </span>
- 종류
    - `+=`, `-=`, `*=`, `/=`, `//=`, `%=`, `**=`

#### 3) 비교 연산자
- 종류
    - `<`, `<=`, `>`, `>=`, `==`, `!=`, `is`, `is not`
- <span style="color:red">`==` 와 `is`의 차이</span>

    ```python
    # ==
    print(2.0 == 2)   # True
    print(1 == True)  # True
        
    # is
    print(2.0 is 2)   # False
    print(1 is True)  # False
    ```
    
    - `==` : 값(데이터) 자체의 비교; 동등성(Equality)
    - `is` : 객체(주소) 자체의 비교; 식별성(Identity), **Singleton(None, True, False) 비교** 시 사용.

#### 4) 시퀀스형 연산자
- 종류
    - +(결합), *(반복)

#### 5) 멤버십 연산자
- 종류
    - in, not in

#### 6) 논리 연산자
- 종류
    - and, or, not

### 2. 단축 평가
#### 1) 단축 평가
- 개념
    - 논리 연산에서 두 번째 피연산자를 평가하지 않고 결과를 결정하는 동작.
- 동작
    - and
        - 첫 번째 피연산자 = True → 전체 표현식 = 두 번째 피연산자의 평가 결과.
        - 첫 번째 피연산자 = False → 전체 표현식 = False.
    - or
        - 첫 번째 피연산자 = True → 전체 표현식 = True.
        - 첫 번째 피연산자 = False → 전체 표현식 = 두 번째 피연산자의 평가 결과.
- 예시
    ```python
    exm = 'aeiou'

    print(('a' and 'b') in exm)  # False
    print(('b' and 'a') in exm)  # True
    # → True and True의 연산에서 마지막 피연산자만 넘겨줌.

    print(3 and 5)
    # 5 → True and True의 연산에서 마지막 피연산자만 넘겨줌.
    print(3 and 0)
    # 0 → True and False의 연산에서 마지막 피연산자만 넘겨줌.
    print(0 and 3)
    # 0 → False and True의 연산에서 앞의 0(False)에서 연산 멈춤.
    print(0 and 0)
    # 0 → False and True의 연산에서 앞의 0(False)에서 연산 멈춤.
    ```

# **250122 | \<Function\>**

## **[1] Function**
### 1. Function
#### 1) ⭐ Funciton
- 개념
    - 특정 작업을 수행하기 위한 **재사용 가능**한 코드 묶음.
- 사용 이유
    - 코드 중복 방지
    - 재사용성 / 가독성 / 유지보수성 ↑
- 구조
    - parameter (매개변수)
        - 함수에 전달되는 값; input.
    - function body
        - 함수 실행시 수행되는 코드.
    - Docstring
        - 선택적으로 작성하는 코드 설명서.
    - return value (반환 값)
        - 함수 실행 종료.

#### 2) 함수 호출 (Function Call)
- 개념
    - 함수의 코드 블록을 실행.
- 방법
    - 함수의 이름을 사용.
- 특징
    - 호출 부분에서 전달된 인자(argument)는 함수 정의 시 작성한 매개변수(parameter)에 대입.

#### 3) 함수 스타일 가이드 (Function Style Guide)
- 기본 규칙
    - 소문자와 언더스코어(_) 사용.
    - 동사로 시작하여 함수의 동작 설명.
    - 약어 사용 지양.
- 함수 이름 구성 요소
    - 동사 + 명사
    - 동사 + 형용사 + 명사
    - get / set 접두사

#### 4) 단일 책임 원칙 (Single Responsibility Principle)
- 개념
    - 모든 객체는 하나의 명확한 목적과 책임만을 가져야 함.
- 원칙
    - 명확한 목적.
    - 책임 분리.
    - 유지보수성.

### 2. 매개변수와 인자
#### 1) 매개변수 (parameter)
- 개념
    - <ins>함수 정의</ins> 시, 함수가 받을 값을 나타내는 변수.

#### 2) 인자 (argument)
- 개념
    - <ins>함수 호출</ins> 시, 실제로 전달되는 값.
- 종류
    1. **Positional Arguments (위치 인자)**
        - 개념
            - 함수 호출 시 인자의 위치에 따라 전달되는 인자.
        - 특징
            - 함수 호출 시 반드시 값을 전달해야 함.
    2. **Default Argument Values (기본 인자 값)**
        - 개념
            - 함수 정의 시 매개변수에 기본 값을 할당.
        - 특징
            - 함수 호출 시 인자를 전달X → 기본값이 매개변수에 할당.
    3. **Keyword Arguments (키워드 인자)**
        - 개념
            - 함수 호출 시 인자의 이름과 함께 값을 전달하는 인자.
        - 특징
            - 호출 시 키워드 인자는 위치 인자 뒤에 위치해야 함.
    4. **Arbitrary Argument Lists (임의의 인자 목록)**
        - 개념
            - 정해지지 않은 개수의 <ins>인자</ins>를 처리하는 인자.
        - 특징
            - 함수 정의 시 매개변수 앞에 '*'를 붙여 사용.
            - 여러 개의 인자를 <ins>tuple</ins>로 묶어 처리.
    5. **Arbitrary Keyword Argument Lists (임의의 키워드 인자 목록)**
        - 개념
            - 정해지지 않은 개수의 <ins>키워드 인자</ins>를 처리하는 인자.
        - 특징
            - 함수 정의 시 매개변수 앞에 '**'를 붙여 사용.
            - 여러 개의 인자를 <ins>dictionary</ins>로 묶어 처리.
    - 함수 인자 권장 작성 순서
        - 위치 → 기본 → 가변 → 가변 키워드.
            ```python
            # 인자의 모든 종류를 적용한 예시
            def func(pos1, pos2, default_arg='default', *args, **kwargs):
                print('pos1:', pos1)
                print('pos2:', pos2)
                print('default_arg:', default_arg)
                print('args:', args)
                print('kwargs:', kwargs)


            func(1, 2, 3, 4, 5, 6, key1='value1', key2='value2')
            """
            pos1: 1
            pos2: 2
            default_arg: 3
            args: (4, 5, 6)
            kwargs: {'key1': 'value1', 'key2': 'value2'}
            """
            ```

### 3. 재귀 함수
#### 1) 재귀 함수
- 개념
    - 함수 내부에서 자기 자신을 호출하는 함수.
- 특징
    - *특정 알고리즘 식*을 표현 시, 변수의 사용 ↓, 코드의 가독성 ↑.
    - 1개 이상의 base case(종료되는 상황)가 존재하고 수렴하도록 작성.
- 예시
    - 팩토리얼
        - $n ! = n * (n - 1) ! = n * (n - 1) * (n - 2)! = ...$

### 4. 내장 함수
#### 1) 내장 함수 (Built-in Function)
- 개념
    - 파이썬이 기본적으로 제공하는 함수.
- 특징
    - 별도의 import 없이 바로 사용 可.
- 유용한 함수
    - map
        - 개념
            - 순회 가능한 데이터 구조(iterable)의 모든 요소에 함수를 적용 → 그 결과를 map object로 반환.
        - 예시
            ```python
            # map(function, iterable)
            result = map(str, [1, 2, 3])
            print(result) # <map object at 0x00000239C915D760>
            print(list(result)) # ['1', '2', '3']
            ```
    - zip
        - 개념
            - 임의의 iterable을 모아 튜플을 원소로 하는 zip object를 반환.
        - 활용
            - 2차원 리스트의 같은 컬럼(열) 요소를 동시에 조회 可.
        - 예시
            ```python
            # zip(*iterables)
            girls = ['jane', 'ashley']
            boys = ['peter', 'brian']
            pair = zip(girls, boys)
            print(pair)  # <zip object at 0x000001C76DE58700>
            print(list(pair))  # [('jane', 'peter'), ('ashley', 'brian')]
            ```

### 5. 함수와 Scope
#### 1) 함수와 범위 (Scope)
- 개념
    - 함수는 코드 내부에 *local scope*를 생성하며, 그 외의 공간인 *global scope*로 구분.
- 범위와 변수의 관계
    - *global scope*
        - 코드 어디에서든 참조할 수 있는 공간.
        - global variable.
    - *local scope*
        - 함수가 만튼 scope; 함수 내부에서만 참조 가능.
        - local variable.

#### 2) 변수 수명 주기
- Built-in Scope
    - 파이썬이 실행된 이후부터 영원히 유지.
- Global Scope
    - 모듈이 호출된 시점 이후 / 인터프리터가 끝날 때까지 유지.
- local scope
    - 함수가 호출될 때 생성되고, 함수가 종료될 때까지 유지.

#### 3) global 키워드
- 개념
    - 변수의 Scope를 전역 범위로 지정하기 위해 사용.
- 특징
    - 일반적으로 함수 내에서 전역 변수를 수정하려는 경우 사용.
    - global 키워드 선언 전에 참조 不可.
    - 매개변수에는 global 키워드 사용 不可.

## **[2] Packing & Unpacking**
### 1. Packing & Unpacking
#### 1) Packing
- 개념
    - 여러 개의 값을 하나의 변수에 묶어서 담는 것.
- 예시
    ```python
    # ex1
    packed_values = 1, 2, 3, 4
    print(packed_values) # (1, 2, 3, 4)

    # ex2
    numbers = [1, 2, 3, 4, 5]
    a, *b, c = numbers
    print(a) # 1
    print(b) # [2, 3, 4]
    print(c) # 5

    # ex3
    def my_func(*args):
            print(args)        # (1, 2, 3, 4, 5)
            print(type(args)   # <class 'tuple'>
    my_func(1, 2, 3, 4, 5)

    # ex4
    print() # 위치 인자가 없는 함수.
    ```

#### 2) Unpacking
- 개념
    - Packing된 변수를 풀어서 개별 변수나 함수 인자로 전달.
- 예시
    ```python
    # Unpacking
    packed_values = 1, 2, 3, 4, 5
    a, b, c, d, e = packed_values
    print(a, b, c, d, e)  # 1 2 3 4 5

    # list Unpacking
    def my_function(x, y, z):
    print(x, y, z)

    names = ['alice', 'jane', 'peter']
    my_function(*names)  # alice jane peter

    # dict Unpacking; Value 기준.
    def my_function(x, y, z):
    print(x, y, z)

    my_dict = {'x': 1, 'y': 2, 'z': 3}
    my_function(**my_dict)  # 1 2 3
    ```

## **[3] Lambda Expressions**
### 1. Lambda Expressions
#### 1) Lambda Expressions
- 개념
    - 익명 함수 / 간단한 한 줄 함수를 정의하는 데 사용되는 표현식.
- 예시
    ```python
    # lambda 매개변수 : 표현식

    # ex1.
    numbers = [1, 2, 3, 4, 5]
    squared = list(map(lambda x : x**2, numbers))
    print(squared) # [1, 4, 9, 16, 25]
    ```

# **250123 | <모듈 / 조건문 / 반복문>**

## **[1] 모듈**
### 1. 모듈
#### 1) 모듈(Module)
- 개념
    - 한 파일로 묶인 변수와 함수의 모음.
    - 특정한 기능을 하는 코드가 작성된 파이썬 파일(`.py`).
- 예시
    - `math`
        ```python
        import math

        print(math.pi)      # 변수 # 3.141592653589793
        print(math.sqrt(4)) # 함수 # 2.0
        ```
    - `random`
        ```python
        import random

        print(random.randint(1, 10))
        ```
    - `datetime`
        ```python
        import datetime

        print(datetime.datetime.now())
        ```
- 활용 방법
    - `import문`
        ```python
        import math
        print(math.sqrt(4))
        ```
    - `from절`
        ```python
        from math import sqrt
        print(sqrt(4))
        ```
    - 주의사항
        - 서로 다른 모듈이 같은 이름의 함수를 제공할 경우 문제 발생.<br>
            → 마지막에 *import*된 이름으로 대체.<br>
            → as 키워드를 사용하여 별칭(alias)을 부여.<br>
            → `import문` 권장.
- Dot('.') 연산자
    - 개념
        - 점의 왼쪽 객체에서 점의 오른쪽 이름을 찾아라.

#### 2) 사용자 정의 모듈
- 개념
    - 함수의 코드 블록을 실행.
- 방법
    - 함수의 이름을 사용.

### 2. 파이썬 표준 라이브러리
#### 1) 파이썬 표준 라이브러리 (Python Standard Library)
- 개념
    - 파이썬 언어와 함께 제공되는 다양한 모듈과 패키지의 모음.

#### 2) 패키지 (Package)
- 개념
    - 연관된 모듈들을 하나의 디렉토리에 모아 놓은 것.
- 종류
    - PSL 내부 패키지
        - 설치 없이 바로 *import*하여 사용.
    - 외부 패키지
        - *`pip`를 사용하여 설치 후 *import* 필요.
            > *`pip` : 외부 패키지들을 설치하도록 도와주는 파이썬의 패키지 관리 시스템.
- 설치
    ```bash
    $ pip install requests
    $ pip install requests==1.0.6
    $ pip install requests>=1.0.5
    ```
- 목록 확인
    ```bash
    $ pip list
    ```

## **[2] 제어문**
### 1. 제어문
#### 1) 제어문 (Control Statement)
- 개념
    - 코드의 실행 흐름을 제어하는 데 사용되는 구문.
    - 조건에 따라 코드 블록을 실행하거나 반복적으로 코드를 실행.
- 종류
    - 조건문
        - `if`, `elif`, `else`
    - 반복문
        - `for`, `while`
    - 반복문 제어
        - `break`, `continue`, `pass`

### 2. 조건문
#### 1) 조건문 (Conditional Statement)
- 개념
    - 주어진 조건식을 평가하여 해당 조건이 `True`인 경우에만 코드 블록을 실행 / 건너뜀.
- 키워드
    - `if`, `elif`, `else`.
- 예시
    ```python
    dust = 480

    if dust > 150:
        print('매우 나쁨')
        if dust > 300:
            print('위험해요!')
    elif dust > 80:
        print('나쁨')
    elif dust > 30:
        print('보통')
    else:
        print('좋음')
    ```

### 3. 반복문
#### 1) 반복문 (Loop Statement)
- 개념
    - 주어진 코드 블록을 여러 번 반복해서 실행하는 구문.
- 키워드
    - `for` : 반복 횟수.
    - `while` : 종료 조건.
- 반복 가능한 객체 (iterable)
    - 반복문에서 순회할 수 있는 객체.
    - Sequence Type & dict & set.

#### 2) for문
- 개념
    - 임의의 시퀀스의 항목들을 그 시퀀스에 들어있는 순서대로 반복.
- 예시
    ```python
    # 구조
    for variable in iterable:
        # code
    
    # list
    items = ['apple', 'banana', 'melon']
    for item in itmes:
        print(item)
    
    # string
    country = 'Korea'
    for char in country:
        print(char)
    
    # dict
    my_dict = {'x' : 10, 'y' : 20, 'z' : 30}
    for dict_key in my_dict:
        print(dict_key)
        print(my_dict[dict_key])
    
    # range
    numbers = [4, 6, 10, -8, 5]
    for i in range(len(numbers)):
        numbers[i] = numbers[i] * 2
    print(numbers) # [8, 12, 20, -16, 10]
    ```

#### 3) while문
- 개념
    - 주어진 조건식이 `True`인 동안 코드를 반복.
    - 주어진 조건식이 `False`가 될 때까지 코드를 반복.
- 예시
    ```python
    # 구조
    while Condition:
        # code
    
    # 예시
    number = int(input('양의 정수를 입력해주세요.: '))

    while number <= 0:
        if number < 0:
            print('음수를 입력했습니다.')
        else:
            print('0은 양의 정수가 아닙니다.')
        
        number = int(input('양의 정수를 입력해주세요.: '))
    
    print('잘했습니다!')
    ```

#### 4) 반복 제어
- 개념
    - `for`와 `while`은 매 반복마다 본문 내 모든 코드를 실행하지만 때때로 일부만 실행하는 것이 필요.
- 키워드
    - `break` : 반복을 즉시 중지.
    - `continue` : 다음 반복으로 건너뜀.
    - `pass` : 아무런 동작도 수행하지 않고 넘어감.
- 예시
    ```python
    # break
    number = int(input('양의 정수를 입력하시오. : '))
    while number <= 0:
        if number == -999:
            print('프로그램을 종료합니다.')
        if number < 0:
            print('음수입니다.')
        else:
            print('0은 양의 정수가 아닙니다.')
        number = int(input('양의 정수를 입력하시오. : '))
    
    # continue
    number = [1, 2, 3, 4, 5, 6, 7]
    for num in number:
        if num % 2 :
            continue
        print(num)
    
    # pass
    def function():
        pass
    ```

#### 5) List Comprehension
- 개념
    - 간결하고 효율적인 리스트 생성 방법.
- 예시
    ```python
    # 구조 1
    # [Expression for Variable in Iterable]
    numbers = [1, 2, 3, 4, 5]
    [num**2 for num in numbers]

    # 구조 2
    # [Expression for Variable in Iterable if Condition]
    [num**2 for num in numbers if num % 2]
    ```

#### 6) enumerate(iterable, start=0)
- 개념
    - iterable 객체의 각 요소에 대해 인덱스와 함께 튜플 형식으로 반환하는 내장함수.
- 예시
    ```python
    fruits = ['apple', 'banana', 'cherry']

    for idx, fruit in enumerate(fruits):
        print(idx, fruit)
    ```

# **250124, 250131 | <Data Structure/ Method / Copy>**

## **[1] Data Structure**
### 1. Data Structure
#### 1) Data Structure
- 개념
    - 여러 데이터를 효과적으로 사용 / 관리하기 위한 구조.
- 활용
    - 문자열, 리스트, 딕셔너리 등 각 데이터 구조의 *메서드*를 호출하여 다양한 기능 활용.

## **[2] Method**
### 1. Method
#### 1) Method
- 개념
    - 객체에 속한 함수.
    - 객체의 상태를 조작하거나 동작을 수행.
- 특징
    - 클래스(class) 내부에 정의되는 함수.
    - 클래스(class)는 파이썬에서 '타입을 표현하는 방법'.
- 예시
    ```python
    # str method
    print('hello'.capitalize()) # 'Hello'

    # list method
    numbers = [1, 2, 3]
    numbers.append(4)
    print(numbers) # [1, 2, 3 ,4]
    ```

#### 2) Method Chaining
- 개념
    - 여러 메서드를 연속해서 호출하는 방식.
- 주의사항
    - 메서드가 객체를 반환할 때만 Chaining 可.
    ```python
    # 잘못된 체이닝 방식 1
    numbers = [3, 1, 4, 1, 5, 9, 2]
    result = numbers.copy().sort()
    print(result)  # None (sort()는 None을 반환하므로 체이닝이 중단됨)
    print(numbers)  # [3, 1, 4, 1, 5, 9, 2] (원본은 변경되지 않음)

    # 잘못된 체이닝 방식 2
    result = numbers.append(7).extend([8, 9])  # AttributeError

    # 개선된 방식
    # 리스트 조작에서 메서드 체이닝을 사용할 때는 각 메서드가 적절한 값을 반환하는지 확인하고,
    # 필요한 경우 새로운 리스트 객체를 반환하는 함수를 사용하는 것이 좋음
    sorted_numbers = sorted(numbers.copy())
    print(sorted_numbers)  # [1, 1, 2, 3, 4, 5, 9]
    ```

### 2. Sequence Data Type
#### 1) `str` Method
- 확인 메서드
    - `s.find(x)`
        - *x*의 첫 번째 위치 반환, <ins>없으면 -1 반환</ins>.
    - `s.index(x)`
        - *x*의 첫 번째 위치 반환, <ins>없으면 오류 발생</ins>.
    - `s.isupper()`
        - 문자열 내의 모든 문자가 대문자인지 확인.
    - `s.islower()`
        - 문자열 내의 모든 문자가 소문자인지 확인.
    - `s.isalpha()`
        - 문자열 내의 모든 문자가 알파벳인지 확인</ins>.
    - code
        ```python
        # find
        text = 'banana'
        print(text.find('a')) # 1
        print(text.find('z')) # -1
                
        # index
        print(text.index('a')) # 1
        # print(text.index('z')) # ValueError: substring not find

        # isupper
        string1 = 'HELLO'
        string2 = 'Hello'
        print(string1.isupper())  # True
        print(string2.isupper())  # False

        # islower
        print(string1.islower())  # False
        print(string2.islower())  # False

        # isalpha
        string1 = 'Hello'
        string2 = '123heis98576ssh'
        print(string1.isalpha())  # True
        print(string2.isalpha())  # False
        ```
- 조작 메서드
    - `s.replace(old, new[, count])`
        - 바꿀 글자를 새로운 글자로 바꿔서 반환.
    - `s.strip([chars])`
        - 공백 / 특정 문자를 제거.
    - `s.split(sep=None, maxsplit=-1)`
        - *sep*를 구분자 문자열로 사용하여 문자열에 있는 단어들의 <ins>리스트를 반환</ins>.
    - `'separator'.join(ierable)`
        - 구분자(seperator)로 iterable의 문자열을 연결한 <ins>문자열을 반환</ins>.
    - code
        ```python
        # replace
        text = 'Hello, world! world world'
        new_text1 = text.replace('world', 'Python')
        new_text2 = text.replace('world', 'Python', 1)
        print(new_text1)  # Hello, Python! Python Python
        print(new_text2)  # Hello, Python! world world

        # strip
        text = '  Hello, world!  '
        new_text = None
        print(new_text)

        # split
        text = 'Hello, world!'
        words1 = text.split(',')
        words2 = text.split()
        print(words1)  # ['Hello', ' world!']
        print(words2)  # ['Hello,', 'world!']

        # join
        words = ['Hello', 'world!']
        new_text = '-'.join(words)
        print(new_text)  # Hello-world!
        ```

#### 2) `list` Method
- 값 추가 및 삭제 메서드
    - `lst.append(x)`
        - 마지막에 *항목 x*를 추가.
    - `lst.extend(m)`
        - *iterable m*의 모든 항목들을 마지막에 추가.
        - `+=`와 같은 기능.
    - `lst.insert(i, x)`
        - *리스트 인덱스 i*에 *항목 x*를 삽입.
    - `lst.remove(x)`
        - 첫 번째로 일치하는 *항목 x*를 제거.
    - `lst.pop([i])`
        - 지정한 인덱스(i; 기본값은 마지막 항목)의 항목을 제거하고 반환.
    - `lst.clear()`
        - 모든 항목을 제거.
    - code
        ```python
        # append
        my_list = [1, 2, 3]
        my_list.append(4)
        print(my_list)           # [1, 2, 3, 4]
        print(my_list.append(4)) # None

        # extend
        my_list = [1, 2, 3]
        my_list.extend([4, 5, 6])
        print(my_list)  # [1, 2, 3, 4, 5, 6]

        # append와의 비교
        my_list.append([4, 5, 6])
        print(my_list)  # [1, 2, 3, 4, 5, 6, [4, 5, 6]]

        # insert
        my_list = [1, 2, 3]
        my_list.insert(1, 5)
        print(my_list)  # [1, 5, 2, 3]

        # remove
        my_list = [1, 2, 3, 2, 2, 2]
        my_list.remove()
        print(my_list)  # [1, 3, 2, 2, 2]

        # pop
        my_list = [1, 2, 3, 4, 5]
        item1 = my_list.pop()
        item2 = my_list.pop(0)

        print(item1)  # 5
        print(item2)  # 1
        print(my_list)  # [2, 3, 4]

        # clear
        my_list = [1, 2, 3]
        my_list.clear()
        print(my_list)  # []
        ```
- 탐색 및 정렬 메서드
    - `lst.index(x)`
        - 첫 번째로 일치하는 *항목 x*의 인덱스를 반환.
    - `lst.count(x)`
        - 리스트에서 *항목 x*의 개수를 반환.
    - `lst.reverse()`
        - 리스트의 순서를 역순으로 변경(정렬 X).
    - `lst.sort()`
        - 원본 리스트를 오름차순으로 정렬.
        - `reverse = True` : 내림차순
    - code
        ```python
        # index
        my_list = [1, 2, 3]
        index = my_list.index(0)
        print(index)  # 1

        # count
        my_list = [1, 2, 2, 3, 3, 3]
        counting_number = my_list.count(3)
        print(counting_number)  # 3

        # reverse
        my_list = [1, 3, 2, 8, 1, 9]
        my_list.reverse()
        print(my_list.reverse())  #
        print(my_list)  # [9, 1, 8, 2, 3, 1]

        # sort
        my_list = [3, 2, 100, 1]
        my_list.sort()
        print(my_list)  # [1, 2, 3, 100]

        # sort(내림차순 정렬)
        my_list.sort(reverse=True)
        print(my_list)  # [100, 3, 2, 1]
        ```

### 3. Non-sequence Data Type
#### 1) `dict` Method
- 값 추가 및 삭제 메서드
    - `dct.get(k[, v])`
        - 키 *k*의 값 / 기본 값(*v*)을 반환(*v*가 없으면, None 반환).
    - `dct.update(other)`
        - `other`가 제공하는 키-값 쌍으로 갱신(기존 키는 덮어씀).
    - `dct.pop(k[, v])`
        - 키 *k* 제거하고 값 / 기본 값(*v*)을 반환 (*v*가 없으면, 오류).
    - `dct.keys()`
        - 키를 모은 객체를 반환.
    - `dct.values(x)`
        - 값을 모은 객체를 반환.
    - `dct.items()`
        - 키-값 쌍을 모은 객체를 반환.
    - `dct.clear()`
        - 딕셔너리의 모든 키-값 쌍을 제거.
    - code
        ```python
        dct = {'key1' : ['value1_1', 'value1_2'], 'key2' : 'value2'}

        # get
        print(dct.get('key'))            # None
        print(dct.get('key', 'default')) # default

        # keys
        print(dct.keys())                # dict_keys(['key1', 'key2'])
        
        # values
        print(dct.values())              # dict_values([['value1_1', 'value1_2'], 'value2'])
        
        # items
        print(dct.items())               # dict_items([('key1', ['value1_1', 'value1_2']), ('key2', 'value2')])

        # pop
        print(dct.pop('key2'))           # 'value2'
        # print(dct.pop('none_key'))     # KeyError: 'none_key'

        # setdefault
        # print(dct.setdefault('new'))   # None
        print(dct.setdefault('new', 'default')) # default
        print(dct)                       # {'key1': ['value1_1', 'value1_2'], 'new': 'default'}

        # update
        other_dct = {'key1' : 'value1', 'key2' : [1, 2, 3]}
        dct.update(other_dct)
        print(dct)                       # {'key1': 'value1', 'new': 'default', 'key2': [1, 2, 3]}
        dct.update(new='wow', **{'key3' : 'test'})
        print(dct)                       # {'key1': 'value1', 'new': 'wow', 'key2': [1, 2, 3], 'key3' : 'test'}
        ```

#### 2) `set` Method
- 값 추가 및 삭제 메서드
    - `st.add(x)`
        - *x*를 추가(이미 있으면 추가 X).
    - `st.update(iterable)`
        - *iterable* 요소를 추가.
    - `st.remove(x)`
        - *x*를 제거(없을 경우, Key Error).
    - `st.discard(x)`
        - *x*를 제거.
    - `st.pop()`
        - 임의의 항목을 반환 및 제거.
    - `st.clear()`
        - 모든 항목을 제거.
    - code
        ```python
        st = set(['a', 'b', 1, 2, 3])

        # add
        st.add(4)
        print(st)          # {1, 2, 3, 4, 'b', 'a'}

        # update
        st.update([5, 6])
        print(st)          # {1, 2, 3, 4, 5, 6, 'b', 'a'}

        # remove
        st.remove(4)
        # st.remove('c')   # KeyError: 'c'
        print(st)          # {1, 2, 3, 5, 6, 'b', 'a'}

        # discard
        st.discard('c')
        print(st)          # {1, 2, 3, 5, 6, 'b', 'a'}
        st.discard(6)
        print(st)          # {1, 2, 3, 5, 'b', 'a'}

        # pop
        st.pop()           # 1
        print(st)          # {2, 3, 'a', 5, 'b'}

        # clear
        st.clear()
        print(st)          # set()
        ```
- 집합 메서드
    - `set1.difference(set2)`
        - $set1 - set2$ ; 차집합.
    - `set1.intersection(set2)`
        - $set1 & set2$ ; 교집합.
    - `set1.union(set2)`
        - $set1 | set2$ ; 합집합.
    - `set1.issubset(set2)`
        - $set1 <= set2$; *set1*의 모든 항목 in *set2*?
    - `set1.issuperset(set2)`
        - $set1 >= set2$; *set2*의 모든 항목 in *set1*?
    - code
        ```python
        set1 = {0, 1, 2, 3}
        set2 = {1, 3, 5, 7}

        # set1 - set2
        print(set1.difference(set2))    # {0, 2}

        # set1 & set2
        print(set1.intersection(set2))  # {1, 3}

        # set1 | set2
        print(set1.union(set2))         # {0, 1, 2, 3, 5, 7}

        # set1 <= set2
        print(set1.issubset(set2))      # False

        # set1 >= set2
        print(set1.issuperset(set2))    # False
        ```

## **[3] Copy**
### 1. 객체와 참조
#### 1) 가변 / 불변 객체
- 개념
    - 가변(Mutable) 객체
        - 생성 후 내용을 변경할 수 있는 객체.
        - ex. `list`, `dict`, `set`.
    - 불변(immutable) 객체
        - 생성 후 내용을 변경할 수 없는 객체.
        - ex. `int`, `float`, `str`, `tuple`.

#### 2) 변수 할당과 참조
- 변수 할당
    - 의미
        - 변수 할당 → 객체에 대한 참조를 생성하는 과정.
        - 변수 → 객체의 메모리 주소를 가리키는 Label 역할.
        - 할당 → '=' 연산자를 사용하며, 할당 시 새로운 객체 생성 / 기존 객체에 대한 참조 생성.
- 변수 참조
    - 의미
        - 객체의 메모리 주소를 저장하기에 여러 변수가 동일한 객체 참조 可.

### 2. Copy
#### 1) 얕은 복사 (Shallow Copy)
- 개념
    - 객체의 **최상위 요소**만 새로운 메모리에 복사하는 방법.
    - 내부에 중첩된 객체가 있다면 그 객체의 참조만 복사됨.
- 방법
    - slicing, `copy()` 메서드, `list()` 함수.
- 한계
    - 2차원 리스트와 같이 **변경 가능한 객체 안에 변경 가능한 객체가 있는 경우**.
        ```python
        a = [1, 2, [3, 4, 5]]
        b = a[:]

        b[0] = 999
        print(a)  # [1, 2, [3, 4, 5]]
        print(b)  # [999, 2, [3, 4, 5]]

        b[2][1] = 100
        print(a)  # [1, 2, [3, 100, 5]]
        print(b)  # [999, 2, [3, 100, 5]]

        # a[2]와 b[2]가 같은 객체인가?
        print(a[2] is b[2])  # True
        ```

#### 2) 깊은 복사 (Deep Copy)
- 개념
    - 객체의 **모든 수준의 요소**만 새로운 메모리에 복사하는 방법.
    - 중첩된 객체가 있다면 그 객체까지도 모두 새로운 객체로 생성됨.
- 방법
    - copy 모듈에서 제공하는 `deepcopy()` 함수.
        ```python
        import copy
        original = {'a': [1, 2, 3],
                    'b': {'c': 4, 'd': [5, 6], }, }
        copied = copy.deepcopy(original)

        copied['a'][1] = 100
        copied['b']['d'][0] = 500

        print(f'원본: {original}')  # {'a': [1, 2, 3], 'b': {'c': 4, 'd': [5, 6]}}
        print(f'복사본: {copied}')  # {'a': [1, 100, 3], 'b': {'c': 4, 'd': [500, 6]}}
        # original["b"]와 copied["b"]가 같은 객체인가?
        print(original["b"] is copied["b"]) # False
        ```

# **250203-250204 | \<OOP\>**

## **[1] 프로그래밍 패러다임**
### 1. 절차 지향과 객체 지향
#### 1) 절차 지향 프로그래밍(Procedural Programming)
- 개념
    - 함수와 로직(절차) 중심으로 프로그램 구성.
    - 데이터를 함수에 전달하여 순차적으로 처리.
- 특징
    - 데이터와 함수(절차)의 분리.
    - 입력 → 처리 → 결과의 과정이 위에서 아래로 순차적인 명령어 실행.
    - 함수 호출의 흐름이 중요.
    - 데이터를 재사용 하기보다는 처음부터 끝까지 실행되는 결과물이 중요.
- 한계
    - 복잡성 증가 (데이터와 함수 / 전역 변수 관리 어려움)
    - 유지보수 문제

#### 2) 객체 지향 프로그래밍(Object Oriented Programming)
- 개념
    - 객체들을 조합하고 재활용하는 방식으로 프로그램 구성.
    - 데이터(변수)와 함수(메서드)를 하나의 단위(객체)로 묶어서 조직적으로 관리.
- 특징
    - 데이터와 함수(메서드)의 결합.

#### 3) 프로그래밍 패러다임
- 개념
    - 객체 지향은 기존 절차 지향을 기반으로 두고 보완하기 위해 객체라는 개념을 도입해 상속, 코드 재사용성, 유지 보수성 등의 이점을 가지는 패러다임.
- 결론
    - 절차 지향과 객체 지향은 대조되는 개념이 아니다.

### 2. 객체와 클래스
#### 1) 객체(Object)
- 개념
    - 실제 존재하는 사물을 추상화한 것.
    - '속성'과 '동작'을 가짐.

#### 2) 클래스(Class)
- 개념
    - 객체를 만들기 위한 설계도.
    - 데이터와 기능을 함께 묶는 방법을 제공.
    - 파이썬에서 타입을 표현하는 방법.

#### 3) 객체 특징
- 속성(Attribute)
    - 객체의 상태 / 데이터.
- 메서드(Method)
    - 객체의 행동 / 기능.
- 고유성
    - 각 객체는 고유한 특성을 가짐.

## **[2] 클래스 기초**
### 1. 클래스와 인스턴스
#### 1) 클래스(Class)
- 개념
    - 데이터와 기능을 하나의 틀로 묶어 관리하는 방법.
    - 사용자 정의 객체를 만드는 수단(; 설계도)이자 속성과 메서드를 정의.
- 정의
    ```python
    class MyClass: # 클래스 이름은 Pascal Case로 작성.
		def __init__(self, name, age):
				self.name = name # 인스턴스 속성
				self.age = age   # 인스턴스 속성
		 
		 def introduce(self):
        print(f'안녕하세요, {self.name}입니다. 나이는 {self.age}살입니다.')
    ```

#### 2) 인스턴스(Instance)
- 개념
    - 클래스를 통해 생성된 객체 (; 설계도로부터 실제로 만든 개별 물건).
- 정의
    ```python
    # alice는 Person의 인스턴스
    alice = Person('Alice', 25)
    alice.introduce()  # 안녕하세요, Alice입니다. 나이는 25살입니다.
    ```

#### 3) 클래스와 인스턴스
- 결론
    - 하나의 객체(object)는 특정 클래스의 인스턴스(instance)이다.
- 예시
    - `123`, `907`은 클래스 int의 인스턴스.
    - `'hello'`, `'brain'`은 클래스 str의 인스턴스.

### 2. 클래스 구조
#### 1) `__init__()` ; 생성자 메서드
- 개념
    - 인스턴스 생성 시 자동 호출되는 특별한 메서드.
    - 인스턴스 변수의 초기화 담당.
- 예시
    ```python
    class Circle:
        def __init__(self, radius): # 생성자 메서드
            self.radius = radius
    ```

#### 2) `self.변수명` ; 인스턴스 변수(속성)
- 개념
    - 각 인스턴스별 고유한 속성.
    - 인스턴스마다 독립적인 값 유지.
- 예시
    ```python
    class Circle:
            def __init__(self, radius):
                    self.radius = radius

    c1 = Circle(5)   # 인스턴스 생성
    print(c1.radius) # 인스턴스 변수(속성)
    ```

#### 3) 클래스 변수(속성)
- 개념
    - 모든 인스턴스가 공유하는 속성.
    - 클래스 내부에서 직접 정의.
- 예시
    ```python
    class Circle:
		pi = 3.14
		def __init__(self, radius):
				self.radius = radius

    c1 = Circle(1)
    c2 = Circle(2)
    print(c1.pi) # 3.14
    print(c2.pi) # 3.14
    ```

#### 4) 클래스 변수와 인스턴스 변수
- 특징
    - 클래스 변수와 동일한 이름으로 인스턴스 변수 생성 시 클래스 변수가 아닌 인스턴스 변수에 먼저 참조하게 됨.
        - `class.class_vairable`로 클래스 변수 참조 가능.

#### 0) 클래스와 인스턴스 간 이름 공간
- 개념
    - 클래스를 정의하면 클래스와 해당하는 이름 공간 생성.
    - 인스턴스를 만들면 인스턴스 객체가 생성되고 독립적인 이름 공간 생성.
    - 인스턴스에서 특정 속성에 접근하면 '인스턴스 → 클래스' 순으로 탐색.

## **[3] 메서드**
### 1. 메서드
#### 1) 메서드 (Method)
- 개념
    - 클래스 내부에 정의된 함수.
    - 해당 객체가 어떻게 동작할지를 정의.

### 2. 메서드 종류
#### 1) 인스턴스 메서드 (Instance Method)
- 개념
    - 클래스로부터 생성된 각 인스턴스에서 호출할 수 있는 메서드.
    - <ins>인스턴스</ins>의 상태 조작 / 동작 수행.
- 구조
    - 클래스 내부에 정의되는 메서드의 기본.
    - 반드시 첫 번째 인자로 인스턴스 자신(`self`)을 받음.
    - 인스턴스의 속성에 접근하거나 변경 가능.
- 활용
    ```python
    class Counter:
        def __init__(self):
            self.count = 0
            
            def increment(self):
                    self.count += 1

    c = Counter()  # 내부 동작 : Counter.__init__(인스턴스)
    print(c.count) # 0

    c.increment()  # 내부 동작 : Counter.increment()
    print(c.count) # 1
    ```

#### 2) 생성자 메서드(Constructor Method)
- 개념
    - 인스턴스 객체가 생성될 때 자동으로 호출되는 메서드.
    - 인스턴스 변수들의 초기값을 설정.
- 활용
    ```python
    class Person:
        def __init__(self, name):
            # 왼쪽 name : 인스턴스 변수 name
            # 오른쪽 name : 생성자 메서드의 매개변수 이름
            self.name = name
            print('인스턴스가 생성되었습니다.')

        def greeting(self):
            print(f'안녕하세요 {self.name}입니다.')

    person1 = Person('지민')  # 인스턴스가 생성되었습니다.
    person1.greeting()        # 안녕하세요. 지민입니다.
    # 내부동작 : Person.greeting(person1)
    ```

#### 3) 클래스 메서드(Class Method)
- 개념
    - <ins>클래스</ins>가 호출하는 메서드.
    - 클래스 변수를 조작하거나 클래스 레벨의 동작을 수행.
- 구조
    - `@classmethod` 데코레이터를 사용하여 정의.
    - 호출 시, 첫 번째 인자로 해당 메서드를 호출하는 클래스(`cls`)가 전달됨.
    - 클래스를 인자로 받아 클래스 속성을 변경하거나 읽는 데 사용.
- 활용
    ```python
    class Person:
    population = 0

    def __init__(self, name):
        self.name = name
        Person.increase_population()
		
		@classmethod
		def increase_population(cls): # 클래스 메서드
			cls.population += 1

    person1 = Person('Alice')
    person2 = Person('Brian')
    print(Person.population)  # 2
    ```

#### 4) 스태틱 메서드(Static Method)
- 개념
    - 클래스, 인스턴스와 상관없이 독립적으로 동작하는 메서드.
    - <ins>클래스</ins>가 사용.
- 구조
    - `@staticmethod` 데코레이터를 사용하여 정의.
    - 호출 시, 자동으로 전달 받는 인자가 없음.
    - 인스턴스나 클래스 속성에 직접 접근하지 않는 ‘도우미 함수’와 비슷한 역할.
- 활용
    ```python
    class MathUtils:
        @staticmethod
        def add(a, b):
            return a + b

    print(MathUtils.add(3, 5))  # 8
    ```

#### 0) 매직 메서드(Magic Method; Special Method)
- 개념
    - 특수한 동작을 위해 만들어져 있으며, 특정 상황에 자동으로 호출되는 메서드.
    - Double underscore('__')가 있는 메서드.
- 예시
    - `__str__(self)`

### 3. 활용 예시
#### 1) 입출금이 가능한 은행 계좌 클래스
- 코드
    ```python
    class BankAccount:
        interest_rate = 0.02  # 이자율

        def __init__(self, owner, balance=0):
            self.owner = owner      # 계좌 소유자
            self.balance = balance  # 초기 잔액

        # 입금
        def deposit(self, amount):
            self.balance += amount

        # 출금
        def withdraw(self, amount):
            if self.balance >= amount:
                self.balance -= amount
            else:
                print('잔액이 부족합니다!')
        
        # 이자율 설정
        @classmethod
        def set_interest_rate(cls, new_rate):
            cls.interest_rate = new_rate

        # 금액이 양수인지 검증
        @staticmethod
        def is_positive(amount):
            return amount > 0


    # 계좌 개설 (인스턴스 생성)
    alice_acc = BankAccount('Alice', 1000)
    print(alice_acc.owner)   # 'Alice'
    print(alice_acc.balance) # 1000

    # 입금 및 출금 (인스턴스 메서드 호출)
    # 잔액 확인 (인스턴스 변수 참조)
    alice_acc.deposit(500)
    print(alice_acc.balance) # 1500

    alice_acc.withdraw(300)
    print(alice_acc.balance) # 1200

    # 이자율 변경 (클래스 메서드 호출)
    BankAccount.set_interest_rate(0.03)
    print(BankAccount.interest_rate)  # 0.03

    # 잔액이 양수인지 확인 (정적 메서드 호출)
    print(BankAccount.is_positive(alice_acc.balance))  # True
    ```

## **[4] 상속**
### 1. 상속
#### 1) 상속(Inheritance)
- 개념
    - 한 클래스(부모)의 속성과 메서드를 다른 클래스(자식)가 물려받는 것.
- 필요성
    - 코드(속성과 메서드) 재사용 → 기능 확장 可.
    - 계층 구조 → 부모 클래스와 자식 클래스 간의 관계 표현.
    - 유지 보수의 용이성.
- 예시
    ```python
    class Person:
        def __init__(self, name, age):
            self.name = name
            self.age = age

        def talk(self):  # 메서드 재사용
            print(f'반갑습니다. {self.name}입니다.')


    class Professor(Person):
        def __init__(self, name, age, department):
            self.name = name
            self.age = age
            self.department = department


    class Student(Person):
        def __init__(self, name, age, gpa):
            self.name = name
            self.age = age
            self.gpa = gpa
    ```

#### 2) 메서드 오버라이딩(Method Overriding)
- 개념
    - 부모 클래스의 메서드를 <ins>같은 이름, 같은 파라미터</ins> 구조로 재정의하는 것.
- 참고
    - 오버로딩(Overloading) : <ins>같은 이름, 다른 파라미터</ins>를 가진 여러 메서드를 정의하는 것. (파이썬 미지원.)
- 예시
    ```python
    class Animal:
        def eat(self):
            print('먹는 중')

    class Dog(Animal):
        def eat(self):
            print('Dog가 먹는 중')

    my_dog = Dog()
    my_dog.eat()   # Dog가 먹는 중


    # 오버로딩 (파이썬 미지원)
    class Example:
        def do_something(self, x):
            print('첫 번째 do_something 메서드:', x)

        # 파이썬에서는 메서드가 "이름"이 같으면 앞선 정의를 덮어써버림
        def do_something(self, x, y):
            print('두 번째 do_something 메서드:', x, y)
    ```

### 2. 다중 상속
#### 1) 다중 상속
- 개념
    - 둘 이상의 상위 클래스로부터 여러 행동이나 특징을 상속받을 수 있는 것.
    - 상속받은 모든 클래스의 요소를 활용 가능.
    - 중복된 속성이나 메서드가 있는 경우 <ins>상속 순서에 의해 결정</ins>됨.
- 예시
    ```python
    class Person:
        def __init__(self, name):
            self.name = name

        def greeting(self):
            return f'안녕, {self.name}'


    class Mom(Person):
        gene = 'XX'

        def swim(self):
            return '엄마가 수영'


    class Dad(Person):
        gene = 'XY'

        def walk(self):
            return '아빠가 걷기'


    class FirstChild(Dad, Mom):
        def swim(self):
            return '첫째가 수영'

        def cry(self):
            return '첫째가 응애'


    baby1 = FirstChild('아가')
    print(baby1.cry())   # 첫째가 응애
    print(baby1.swim())  # 첫째가 수영
    print(baby1.walk())  # 아빠가 걷기
    print(baby1.gene)    # XY
    ```

#### 2) `super()` 메서드
- 개념
    - MRO 순서 상 부모 클래스(또는 상위 클래스)의 메서드를 호출하기 위해 사용하는 내장 함수.
- 기능
    - ***다이아몬드 문제(The diamond problem)** 가 발생하는 다중 상속 상황에서 유용.
        - ***다이아몬드 문제(The diamond problem)** : 두 클래스 B와 C가 A에서 상속되고 클래스 D가 B와 C 모두에서 상속될 때 발생하는 모호함.
    - ***MRO(Method Resolution Order)** 를 따름 → 여러 부모 클래스를 가진 자식 클래스에서 다음에 호출해야 할 부모 메서드를 순서대로 호출 可.
    - ***MRO**(**Method Resolution Order**; 메서드 결정 순서) : 파이썬이 메서드를 찾는 순서에 대한 규칙.<br>
        → 부모 클래스로부터 상속된 속성들의 검색을 깊이 우선으로 **왼쪽에서 오른쪽으로**, 계층 구조에서 겹치는 같은 클래스를 두 번 검색하지 않음.
- 사용 사례
    1. 단일 상속 구조
        - 클래스 이름 변경 / 부모 클래스 교체 시 `super()` 를 사용하면 코드 수정 적게 필요.
    2. 다중 상속 구조
        - MRO를 따른 메서드 호출.
        - 복잡한 다중 상속 구조에서 발생 가능한 문제 방지.
- 예시
    ```python
    class ParentA:
        def __init__(self):
            # super().__init__()
            self.value_a = 'ParentA'

        def show_value(self):
            print(f'Value from ParentA: {self.value_a}')


    class ParentB:
        def __init__(self):
            self.value_b = 'ParentB'

        def show_value(self):
            print(f'Value from ParentB: {self.value_b}')


    class Child(ParentA, ParentB):
        def __init__(self):
            super().__init__()    # ParentA 클래스의 __init__ 메서드 호출
            self.value_c = 'Child'

        def show_value(self):
            super().show_value()  # ParentA 클래스의 show_value 메서드 호출
            print(f'Value from Child: {self.value_c}')


    child = Child()
    child.show_value()
    """
    Value from ParentA: ParentA
    Value from Child: Child
    """
    print(child.value_c)  # Child
    print(child.value_a)  # ParentA
    print(
        child.value_b
    )  # AttributeError: 'Child' object has no attribute 'value_b'


    """
    <ParentA에 super().__init__()를 추가하면?>
    그 다음으로 ParentB의 __init__가 실행되어 value_b도 초기화할 수 있음.
    그러면 print(child.value_b)는 ParentB를 출력하게 됨.

    print(child.value_b)  # ParentB
    """
    ```

## **[5] 에러와 예외**
### 1. 디버깅
#### 1) 버그(Bug)
- 개념
    - 컴퓨터 시스템에서 발생하는 오류 / 결함을 지칭하는 용어.

#### 2) 디버깅(Debugging)
- 개념
    - SW에서 발생하는 버그를 찾아내고 수정하는 과정.
    - 프로그램의 오작동 원인을 식별하여 수정하는 작업.
- 방법
    - `print()`함수 활용.
    - 개발 환경(text editor, IDE) 등에서 제공하는 기능 활용.
    - Python tutor 활용.
    - 뇌 컴파일, 눈 디버깅 등.

### 2. 에러와 예외
#### 1) 에러(Error)
- 개념
    - 프로그램 실행 중에 발생하는 예외 상황.
- 유형
    1. 문법 에러(Syntax Error)
        - 프로그램의 구문이 올바르지 않은 경우 발생.
        - 오타, 괄호 및 콜론 누락 등의 문법적 오류.
    2. 예외(Exception)
        - 프로그램 실행 중에 감지되는 에러.

#### 2) 내장 예외(Built-in Exception)
- 개념
    - 예외 상황을 나타내는 예외 클래스들.
- 특징
    - 파이썬에 이미 정의되어 있으며, 특정 예외 상황에 대한 처리를 위해 사용.
- 종류
    - ZeroDivisionError : 나누기의 두 번째 인자가 0인 경우.
    - NameError : 지역 / 전역 이름을 찾을 수 없는 경우.
    - TypeError : 타입 불일치, 인자 누락 / 초과, 타입 불일치하는 경우.
    - ValueError : 부적절한 값을 인자로 받은 경우.
    - IndexError : 시퀀스 인덱스가 범위를 벗어난 경우.
    - KeyError : 딕셔너리에 해당 키가 존재하지 않는 경우.
    - ModuleNotFoundError : 모듈을 찾을 수 없는 경우.
    - ImportError : import하려는 이름을 찾을 수 없는 경우.
    - KeyboardInterrupt : 사용자가 강제 종료한 경우.
    - IndentationError : 잘못된 들여쓰기와 관련된 문법 오류가 발생한 경우.

### 3. 예외 처리
#### 1) 예외 처리(Exception Handling)
- 개념
    - 예외가 발생했을 때 프로그램이 비정상적으로 종료되지 않고, 적절하게 처리할 수 있도록 하는 방법.
- 구문
    - `try` : 예외 발생 가능 코드.
    - `except` : 예외 발생 시 실행할 코드.
    - `else` : 예외 미발생 시 실행할 코드.
    - `finally` : 예외 발생 여부와 상관없이 반드시 실행할 코드.
- 참고
    - try-except와 if-else를 함께 사용할 수 있음.
- 예시
    ```python
    try:
        x = int(input('숫자를 입력하세요: '))
        y = 10 / x
    except ZeroDivisionError:
        print('0으로 나눌 수 없습니다.')
    except ValueError:
        print('유효한 숫자가 아닙니다.')
    else:
        print(f'결과: {y}')
    finally:
        print('프로그램이 종료되었습니다.')
    ```

#### 2) 예외 처리 주의사항
- 예외 처리 주의사항
    - 내장 예외 클래스는 상속 계층구조를 가지기 때문에 `except` 절로 분기 시 반드시 하위 클래스를 먼저 확인할 수 있도록 작성해야 함.
    - https://docs.python.org/ko/3/library/exceptions.html#exception-hierarchy
- 예시
    ```python
    # 2번째 except 절에 이후로 도달하지 못함
    # ZeroDivisionError 클래스는 BaseException 클래스의 하위 클래스 중 하나이므로 ZeroDivisionError를 먼저 작성해야 함
    try:
        num = int(input('100으로 나눌 값을 입력하시오 : '))
        print(100 / num)
    except BaseException:
        print('숫자를 넣어주세요.')
    # ZeroDivisionError는 BaseException의 하위 클래스이므로 BaseException보다 먼저 작성해야 함
    except ZeroDivisionError:
        print('0으로 나눌 수 없습니다.')
    except:
        print('에러가 발생하였습니다.')


    # 옳은 코드
    # 가장 구체적인 예외부터 처리하고, 마지막에 범용 예외를 처리하도록 순서를 배치
    try:
        num = int(input('100으로 나눌 값을 입력하시오 : '))
        print(100 / num)
    # 1) 구체적인 예외부터
    except ZeroDivisionError:
        print('0으로 나눌 수 없습니다.')
    except ValueError:
        print('숫자를 넣어주세요.')
    # 2) 마지막에 광범위한 예외(Exception)
    except Exception:
        print('에러가 발생하였습니다.')
    ```

#### 3) 예외 객체 다루기
- 예외 객체
    - 예외가 발생했을 때 예외에 대한 정보를 담고 있는 객체.
- 예시
    ```python
    my_list = []
    try:
        number = my_list[1]
    except IndexError as error:
        # list index out of range가 발생했습니다.
        print(f'{error}가 발생했습니다.')
    ```

### 4. EAFP & LBYL
#### 1) EAFP & LBYL
- 개념
    1. EAFP(Easier to Ask for Forgiveness than Permission; 허락보다 용서 구하기)
        - 예외처리를 중심으로 코드를 작성하는 접근 방식.
        - *try-except*
    2. LBYL(Kook Before You Leap; 돌다리도 두들겨보고 건너기)
        - 값 검사를 중심으로 코드를 작성하는 접근 방식.
        - *if-else*
- 예시
    ```python
    my_dict = {'key': 'value'}

    # EAFP
    try:
        result = my_dict['key']
        print(result)
    except KeyError:
        print('Key가 존재하지 않습니다.')

    # LBYL
    if 'key' in my_dict:
        result = my_dict['key']
        print(result)
    else:
        print('Key가 존재하지 않습니다.')
    ```
