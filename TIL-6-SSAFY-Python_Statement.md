# 오늘 배운것

## set
두 자료 데이터를 비교할 때,
set으로 형 변환 하여, 차이를 쉽게 비교할 수 있다.
```python
  set_of_book = set(list_of_book)
  set_of_rental = set(rental_list)
  not_in_stock = set_of_rental - set_of_book
  if not_in_stock:
      for book in not_in_stock:
          print(f"{book} 은/는 보유하고 있지 않은 도서입니다.")
  else:
      print("대여 목록의 모든 도서를 보유하고 있습니다.")
``` 
```python
#반복문 방식
for book in rental_list:
    if book not in list_of_book:
        print(f"{book} 은/는 보유하고 있지 않습니다.")
        break

else:
     print("모든 도서가 대여 가능한 상태입니다.")
```

## 리스트 컴프리핸션
 [표현식 for 항목 in 반복가능한_객체 if 조건문]
 range() 를 꼭 쓰는건 아니다, 

 # 
  from avc.vad import EEE

  ## 배운것
  리스트안에 딕셔너리 있는구조. 잘 못하는듯
  리스트 의 [] 접근하는걸 생각하자

  ## len 구현법
  이중 반복문으로 세부사항 하나나 반복돌때 
  count +=1 으로 숫자를 세면 된다.
  안 반복문 끝나면 count를 출력시키고
  다시 count를 초기화 시켜야 한다.

  ## enumerate ()
  인덱스와 값을 함께 반환 하는 내장 함수

  ## url
  url 끝값만 바꿔서 여러개 호출해오고 싶으면 끝값만 f스트링과 반복문 활용해 호출해오면 된다.

  이러한 호출값을 입력할때, 호출할때마다 새로운값이 덮어씌어지다보니,
  누적해서 입력하는게필요한데

  변수.appen(입력값) 으로 해당 리스트에 누적해서 쌓는 방식으로 해야 한다.

  ## apend
   특정 조건에서만 appen 하게 해서 누적 리스트를 만들 수 있다.
   if문에서 and 쓰면된다.
   딕셔너리를 리스트로 입력 받을때
   일단 딕셔너리를 하나 만들고, 필요한 요소 하나 하나를 해당 딕셔너리에 할당한다.
   그 다음 그 딕셔너리를 리스트에 append 한다.

   데이터 수신 및 변환: requests로 API에서 데이터를 받아온 후, .json()으로 파이썬이 다루기 쉬운 **아주 큰 딕셔너리(parsed_data)**로 변환합니다.

정보 재가공: parsed_data에 있는 여러 정보 중 우리가 필요로 하는 값(회사명, 위도, 경도, 이름)만 뽑아서 person이라는 새롭고 간결한 딕셔너리를 만듭니다.

조건문 필터링: if 문을 사용해 person 딕셔너리에 담긴 위도(lat)와 경도(lng) 값이 특정 조건(위도 80 미만, 경도 -80 초과)에 맞는지 검사합니다.

리스트에 추가: 위 조건이 참(True)일 경우에만, 2번 단계에서 만들었던 person 딕셔너리 그 자체를 dummy_data라는 리스트에 **추가(append)**합니다.

```python
import requests
from pprint import pprint as print

dummy_data = []

for id in range(1,11):
# 무작위 유저 정보 요청 경로
    API_URL = f'https://jsonplaceholder.typicode.com/users/{id}'
# API 요청
    response = requests.get(API_URL)
    parsed_data = response.json()
    person = {'company' : parsed_data['company']['name'],
              'lat' : parsed_data['address']['geo']['lat'],
              'lng' : parsed_data['address']['geo']['lng'],
              'name' : parsed_data['name'],}
    if float(parsed_data['address']['geo']['lat']) < 80 and float(parsed_data['address']['geo']['lng']) > -80: 
        dummy_data.append(person)

print(dummy_data)
```