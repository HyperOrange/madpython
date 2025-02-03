# README for HW 1-1

12201966 최영준

hw 1-1은 main_da.cpp, dynamic_arr.h, dynamic_arr.cpp로 이루어져 있습니다.
문제 해결을 위해 강의노트 Dynamic arry를 참고하였습니다. 

## dynamic_arr.h
헤더 파일에서는 dynamicarray class를 정의하고 다양한 기능을 수행할 수 있는 함수들을 선언했습니다. 
각 함수는 다음과 같은 기능을 수행합니다.
pushBack = 입력받은 데이터 배열에 추가
insert = 입력받은 데이터를 입력받은 인덱스에 추가(삽입)
removeItem = 입력받은 데이터가 배열안에 있다면 배열에서 해당 데이터를 제거
print = 배열을 출력
getSize = 배열 안에 저장된 데이터의 개수 반환
getCapacity = 배열의 총 크기 반환

## dynamic_arr.cpp
cpp파일에는 위 함수들의 구현을 위한 코드가 존재합니다.
특히 데이터의 개수(size)와 capacity를 비교하여 capacity의 크기를 조절하는 함수인 
dyArrDoubleCapacity 함수와 dyArrHalfCapacity 함수도 정의하였습니다. 

우선 배열의 크기에 대한 입력값이 있다면 해당 크기만큼 데이터의 capacity를 설정하고, 이외의 경우에는 크기가 0이 되도록 DynamicArray의 생성자를 만들었습니다.

dyArrDoubleCapacity 는 배열의 capacity를 두배로 늘리는 함수입니다. 
구현을 위해서는 이전 데이터들과 그 사이즈를 각각 oldbuffer와 oldzize에 저장해둡니다.
이후 기존 배열의 capacity보다 capacity가 2배큰 배열을 만든 뒤 순서대로 기존 데이터를 옮깁니다.
마지막으로 필요가 없어진 oldbuffer를 삭제합니다. 

dyArrHalfCapacity 는 배열의 capacity를 절반으로 줄이는 함수입니다.
dyArrDoubleCapacity와 마찬가지로 이전 데이터들과 그 사이즈를 각각 oldbuffer와 oldzize에 저장해둡니다. 이후 기존 배열 capacity의 절반 크기의 capacity를 가진 배열을 만든 뒤 순서대로 기존 데이터를 옮깁니다.
마지막으로 필요가 없어진 oldbuffer를 삭제합니다. 

이 두 함수는 배열에 새로운 데이터를 삽입할 때 capacity가 부족하거나, 낭비되는 상황을 막기 위해 존재하며 pushBack, insert, removeItem 에서 사용됩니다. 

pushBack은 배열의 마지막에 새로운 데이터를 추가하는 함수입니다. 이때 배열에 남은 capacity가 없다면 dyArrDoubleCapacity를 실행하여 배열의 크기를 두배로 늘린 뒤 데이터를 추가합니다. 

insert는 원하는 인덱스에 원하는 데이터를 넣는 함수입니다. 만약 입력받은 인덱스가 0보다 작거나 기존에 존재하는 데이터의 수(size)보다 크다면 작동하지 않습니다.
데이터와 인덱스가 정절하게 입력되었다면 입력받은 인덱스값 이상 인덱스에 존재하던 데이터들을 한칸씩 뒤로 옮긴 뒤 해당 위치(입력받은 인덱스)에 입력받은 데이터를 넣습니다. 
그리고 이미 배열이 꽉 찬 상태라면 dyArrDoubleCapacity를 실행하여 배열의 크기를 두배로 늘린 뒤 작동합니다. 

removeItem은 입력받은 데이터가 배열 안에 존재한다면 그 데이터를 제거하는 함수입니다. 
입력받은 데이터가 배열에 있다면 데이터를 삭제한, 뒤 삭제된 데이터가 존재한 인덱스 이상 데이터를 한칸씩 앞으로 가져옵니다. 
이때 과제의 조건이었던 size가 capacity의 1/4 에 도달하면 배열의 capacity를 줄이는 기능을 구현하기 위해, size가 capacity의 1/4 보다 작거나 같고 동시에 capacity가 4보다 작지 않으면 dyArrHalfCapacity를 실행하여 배열의 크기를 절반으로 줄이도록 하였습니다. 

print는 배열에 저장된 모든 데이터값을 출력합니다.
getSize는 배열의 size를 반환합니다.
getCapacity는 배열의 capacity를 반환합니다. 

## main_da.cpp
main함수의 실행결과는 아래와 같습니다.
A
B
0
B
0
B
A
A
A
A
A
A
A
A
A
A
A
A
A
Current size and capacity: 15, 28
0
B
A
A
A
A
Current size and capacity: 6, 14