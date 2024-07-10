# find()
- find(찾을 문자, 찾기 시작할 위치, 찾기를 끝맺을 위치)
  ```
  h = '안녕'
  print(h.find('녕')) # 1
  ```
  - str 객체의 메서드로 사용 가능
  - 찾는 문자 없을 경우  `-1` 반환
 
# index()
- list, tuple, str 객체의 메서드로 사용 가능
- iterable 자료형에서 특정 원소의 인덱스를 반환해주는 함수 
- 찾는 문자 없을 경우 오류 발생

## 형식
- list.index(x) : 리스트에서 x의 인덱스 반환
- list.index(x, start) : 리스트[srat:]에서 x의 인덱스 반환
- list.index(x, start, stop) : 리스트[start:stop-1]에서 x의 인덱스 반환

## 예시
```python
# list a의 'c' 인덱스 찾기
a = ['a', 'b', 'c']
print(a.idnex('c')) # 2
```
