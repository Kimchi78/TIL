# 데이터 구조

## 메서드
 메서드도 사실 함수이다.
 객체에 속한 함수를 메서드라고 한다.
 데이터타입 객체. 메서드() 형식으로 사용한다.

## 문자열 조회 메서드
 s.find(x) :  x의 첫번쨰 위치를 반환한다. / 없으면 -1 반환  ex) apple -> 0 
 s.index(x) : find랑 똑같다 근데 / 없을때 반환대신 오류 나옴
 
 s.isupper() : 문자열 내 모든 문자가 대문자인지 확인 -> boolean 
 s.islower() : 문자열 내 모든 문자가 소문자인지 확인
 s.isalpha() : 문자열 내 모든 문자가 알파벳인지. 확인

## 문자열 조작 메서드
  s.replace (old, new[,count]) : 바꿀 대상의 문자를 새로운 글자로 바꿔서 반환
   * 새로운 문자열을 반환하는 개념이다. 카운트를 넣지 않으면 해당 문자 전부 다 바꿈, count = 바꿀개수.
  s.strip([chars]) : 앞이나 뒤에 공백들 제거해준다.
  s.split (바꿀 기준, 기본은 공백을 기준으로 나눈다) ex) s.split(,) or s.split('a')
  'separator'.join(iterable) : iterable의 문자열을 연결한 문자열을 반환한다.
   * text = '-'.join(words)
   * '-'같은 구분자로 문자열을 연결시켜 반환해준다.
   * 구분자 (seperator)는 공백이나 / 등등 자유롭게 원하는 방식으로 넣어서 이어주면 된다.

## 리스트 추가 삭제 메서드
  L.append(x) : 리스트 마지막에 항목 x를 추가
  L.extend(m) : 이터러블 m의 모든 항목들을 리스트 끝에 추가 (+=) 같은 기능
   * append는 값을 풀어낼 능력이 없다(해당x의 리스트 전부가 하나의 리스트 안에 들어가 중첩 리스트처럼 들어간다)
   * extend는 반복 가능한 개체 아니면 추가가 불가능하다 . ex)100을 넣으면 오류 남
  L.pop() : 가장 오른쪽 항목 반환 후 제거
  L.pop(i) : 지정한 인덱스 항목을 제거하고 반환한다.
   * remove는 제거만 해주는데, pop은 반환까지 해준다.

## 리스트 탐색 및 정렬 메서드
  L.reverse() : 리스트 순서 역순으로 변경 (정렬x)
  L.sort() : 리스트 정렬
   * .sort(revers=ture) : 내림차순으로 정렬


## 가변 불변 객체
  가변 객체 : 생성 후 내용 변경할 수 있는 객체 (리스트, 딕셔너리, 집합 등)
  불변 객체 : 생성 후 내용 변경할 수 없는 객체 ( 정수, 실수, 문자열, 튜플 등)
 **결국 값이 변경되었을때, 메모리 주소가 그대로 유지되는지, 새로운 공간에 생성하는지. 여부**

## 얕은 복사
  객체의 최상의 레벨만 복사가 된다.
  할당이 아니라, 복사가 되긴 되는거다
  얕은 복사 방법
   1) 리스트 슬라이싱 a[:]
   2) copy() 메서드 - a.copy(b)
   3) list() 함수 - a = list(b)
  **얕은 복사를 굳이 쓰는이유? 속도가 빠르고, 메모리를 적게 사용한다**

## 깊은 복사
  ``` python
  import copy
  반환본 = copy.deepcopy(원본)
  ```

## List Comprehension
  파이썬답게, 간결하게 리스트를 생성하는 방식이다.
  data1 = [[0] * (5) for _ in range(5)] = 
  * 0들어가면 5x5 배열 만들어서 알고리즘 풀때 사용
  리스트 생성방법
    1) for문
    2) 리스트 컴프리핸션
    3) map 

## 메서드 체이닝
  메서드가 계속 연결되는거,
  나눠서 해도 되는데 같이쓰면 코드 줄일 수 있으니까
  모든 메서드가 지원하는건 아니다.
  반홥값이 None이 나오면 중간에 끊겨서 오류 날 수 도 있다.

## 과제2
 Max, Min 함수
 ```python
 def find_min_max(input_list):
    a = 0
    for i in input_list:
        if i > a:
            a = i
    b = a
    for i in input_list:
        if b > i:
            b = i 
    return (b,a)
  ```
  return min(x),max(x)  ==> 도 가능

## 새롭게 배운 것

### sort()
sort() 정렬 메소드는 반환값이 None 이다.
정렬 후, 다시 그 리스트를 출력하면 정렬되어 있다.
정렬된 것을 다시 할당하고 싶으면 sorted 함수 사용

### range()
for문을 돌릴때 범위가 필요하다. 정수를 넣으면 안되고
range(len(data_2)) - 문자열 데이터의 경우 사이즈 변환 -> 범위 변환이 필요하다

### reversed()
 reverse() 하면, 하나하나 문자의 리스트가 생성된다.
 문자열로 reverse 가 하고 싶은거라면
 join으로 이어주면 된다.

 ### 리스트 중복 제거
  리스트를 SET으로 만든 뒤 다시 List로 만들면 중복이 제거된다.
  set는 중복을 허용하지 않기 때문이다.

### count()
문자열 카운트 str.count(char)

## 함수로 정렬하기
```python
def find_min_max(lst):
    """
    이 함수는 인자로 받은 리스트를 오름차순으로 정렬한 후,
    첫 번쨰와, 마지막 요소를 반환하는 함수
    """
    #원본 리스트 변경하지 않기 위해 복사본 지정
    sorted_lst = lst[:]

    #리스트의 길이만큼 반복
    for idx in range(len(sorted_lst)):
        #현재 인덱스를 최소값으로 인덱스로 가정
        min_index = idx
        # idx 뒤에 있는 나머지 원소들과 비교하기 위해 나머지 원소들을 순회
        for j in range(idx + 1, len(sorted_lst)):
            #j에서 더 작은 원소를 찾으면, 최소값의 인덱스 갱신(업데이트)
            if sorted_lst[min_index] > sorted_lst[j]:
                min_index = j
        sorted_lst[idx], sorted_lst[min_index] = sorted_lst[min_index], sorted_lst[idx] #스왑
    print(sorted_lst)
```

## 문자열 제거