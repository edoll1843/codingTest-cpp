# alias쓸거면 namespace std;다음줄에 쓰자!!!!!!
```C++
using pii = pair<int,int>;
typedef pii = pair<int,int>;
```

# limits / limits.h
```C++
using 함수 위에 
#define 변수명 INT_MAX   <--- 정수 상수에 대한 제한 int형식 변수의 최대값
#define 변수명 INT_MIN   <--- int 형식 변수의 최솟값
다른 변수형식도 사용이 가능하다.
```

# string.h
```C++
memset(셋팅하고자하는 메모리주소, 셋팅할 값, 메모리 주소의 사이즈); // 컴파일러 환경에 따라 for문보다 빠를 수가 있다.
memset은 0,-1로 밖에 초기화가 안된다. 다른값을 쓰고싶으면 fiil_n을쓴다.
fill_n(변경하려는메모리의시작주소, 변경하려는 원소 개수, 변경 값);
fill_n(arr,100,2);	<-- arr[0]부터 arr[100]까지 2로 초기화
fill_n(arr+1,99,2)	<--- arr[1]부터 99개 더 2로 초기화

fill(변경하려는메모리의시작주소,변경하려는원소의범위종료주소,변경값) 
```
# vector
```C++
#include <vector>
vector<int> v(3);					<---크기가 3인 벡터 0으로 초기화
vector<int> v(3,-1);					<---크기가 3인 벡터 -1로 초기화
vector<int> v = {1,2,3};				<---벡터의 초기화

vector<vector<int>> v(3,vector<int>(3,-1));		<--- 2차원벡터 행3,세로3을 -1로 초기화
vector<vector<int>> v(행크기,vector<int>(열크기));	 <--- 2차원벡터의 공간할당하는법 0으로 초기화
vector<vector<int>> v = {{1,2,3},{4,5,6}};	 	<--- 2차원벡터의 초기화

v.erase(v.begin())					<--- 맨앞을 지운다.
v.erase(v.begin()+a) 					<--- 특정 원소(인덱스)를 지운다.
v.erase(v.begin()+a, v.begin()+b) 			<--- 특정 원소들 a~b까지 지운다.

```
# cmath
```C++
#include <cmath>
sqrt(n)				<--- 루트n 구하는 함수
pow(숫자, 제곱할 횟수)		 <--- 제곱근 구하는 함수
sqrt(n)/1.00 == (int)sqrt(n)    <--- 루트n이 정수인지 판별하는 함수, 이건 같다는 가정
```
# cctype
```C++
isdigit			<--- 숫자인지 판별 (반환형은 int형, 틀리면 0 맞으면 1)
isspace			<--- 공백인지 판별(반환형은 int형, 틀리면 0 맞으면 1)
isalpha			<--- 알파벳인지 판별(반환형은 int형, 틀리면 0 맞으면 1)
isupper			<--- 대문자인지 판별(반환형은 int형, 틀리면 0 맞으면 1)
islower			<--- 소문자인지 판별(반환형은 int형, 틀리면 0 맞으면 1)
```
# sstream
```C++
#include<sstream>
istringstream은 문자열 자를때
ostringstream은 문자열 추가할떄
stringstream은 문자열 자르고 추가할떄
stringstream str("sdadsada") 				<--- 변수 선언 및 문자열 삽입(변수도 가능)
string str_cut;
str >> str_cut   					<--- 문자열 공백이나 tab 기준으로 자르기
str << int형변수 << "직접적인 문자열" << string변수      <--- 문자열 추가
while(str >> str_cut)					<--- 반복적으로 자를 수 있다 str_cut은 값이 바뀐다.
```
# string
```C++

bool cmp(string a, string b)
{// <는 오른쪽으로 갈수록 커진다. 즉 , 오름차순. >는 반대로 내림차순
	return a <b;
}
bool cmp(pair<int,int>a,pair<int,int>b)
{// a와 b가 둘다 첫번쨰가 같다면 뒤에 것을 기준으로 오름차순한다.
	if(a.first == b. first)
		return a.second<b.second;
	else//첫번째가 같지 않다면 첫번쨰 기준으로 오름차순한다. 반대도 가능함
		return a.first < b.first;
}
bool cmp(string a , string b)
{// 특정 문자를 기준으로 정렬할 수도 있다. a[j]b[j]가 같다면 사전순으로 정렬(오름차순)
	if(a[j] == b[j])
		return a<b;
	else// 같지 않으면 오름차순
	return a[j] < b {j};
}

#include <string>

string str;
str.replace(시작인덱스,바꿀끝인덱스까지,바꿀문자)	<--- 시작인덱스부터 바꿀인덱스까지 바꾼다.
str.replace(pos,count,str,pos2,npos)			<--- 기존문자열의 pos부터 count개의 문자들을 str의 pos2부터 count2개의 문자들로 치환한다.

string str;
auto i = str.find('a')					<--- a를 찾는다 있으면 인덱스 반환 없으면 (int)i 했을때 -1값 나옴
auto i = str.find("is");				<--- 문자열도 찾을 수 있다.
auto i = str.find("is",5);				<--- str의 5번째 문자부터 찾는다.

string str;
getline(cin,str);					<--- string을 공백포함해서 cin받는거

int num = stoi(str)					<--- string형을 int로 바꾸는 함수
stoi = string to int
stof = string to float
stol = string to long int
stod = string to double
stoul = string to unsigned int
stoll = string to long long
stoull = string to unsigned long long
stold = string to long double

int num = stoi("-1234")					<--- stoi 쓰면 -부호도 인식한다.
string str = to_string(num)				<--- int형을 string으로 바꾸는 함수
char a; int b = a - '0';				<--- char형 문자 하나를 int로 바꾸는거 stoi는 string문자열 전체, atoi는 char문자열 전체
int a; char b = a + '0';				<--- int숫자 하나를 char로 바꾼다.

string a = "0123456789abcdefghij"			<--- 문자열 선언
string sub1 = a.substr(10)				<--- a[10]부터 끝까지 저장
string sub2 = a.substr(5,3)				<--- a[5]부터 3개 저장
string sub3 = a.substr(a.size()-3 , 50)			<--- 두번째 인자가 사이즈보다크면 끝까지 저장
int tolower('A');					<--- 문자를 대문자->소문자로 바꿔준다.
int toupper('a');					<--- 문자를 소문자->대문자로 바꿔준다.

s.erase(0,5);						<--- s[0]부터 5개 지운다.
s.erase(find(s.begin(),s.end(),' '));			<--- 시작부터 끝 중에 ' '찾고자 하는 문자를 지운다.
```

# algorithm
```C++
#include <algorithm>

pair<자료형1, 자료형2> 변수				<--- pair의 선언
변수 = make_pair(자료형1,자료형2)			<--- make_pair로 값을 넣어줘도 된다.
변수 = {변수1,변수2} 					  <--- 이렇게도 사용한다.

int tmp[MAX];
sort(tmp,tmp+n);					<-- 배열로 쓸땐 이렇게함, (시작,끝)
sort(a.begin, a.end())					<--- 벡터 처음부터 끝까지 오름차순으로 정렬
sort(a.begin,a.end(),greater<>())			<--- 내림차순으로 정렬
sort(a.rbegin(),a.rend())				<--- 내림차순으로 정렬
sort(a.begin, a.end(),cmp)				<--- cmp를 이용하여 정렬. cmp()괄호는 뺴야한다.

bool cmp(pair<int,int>a, pair<int,int>b)		<--- pair형태일때 정렬하기 위한 cmp이다. 
{							<--- a는 현재원소, b는 다음 원소인데 cmp리턴값이 false면 swap한다. 왼쪽 함수는 first기준 오름차순이다.
	if(a.first == b.first)
		return a.second < b.second;
	else
		return a.first < b.first;
}
bool cmp(pair<int,int>a, pair<int,int>b)		<--- second 기준 오름차순의 cmp함수이다.
{				
	if(a.second == b.second)
		return a.first < b.fisrt;
	else
		return a.second < b.second;
}

unique(arr.begin(),arr.end())				<--- 배열의 연속된 값을 제거한다. 전체 중복 숫자 지우는거 아님. 
arr.erase(unique(arr.begin(),arr.end()),arr.end()) 	<--- 뒤에 남기 떄문에 지워줘야한다.전체 중복을 지우고 싶으면 sort하고 이 코드 실행

reverse(arr.begin(). arr.end())				<--- 벡터를 거꾸로 한다.

next_permutation()					<--- 순열을 구하는 함수. 최소값부터 나온다 정렬 도됨
do{							<--- !!!!꼭 sort를 하고 사용할 것 그렇지 않으면 중간 부터 값이 나옴
	for(int i =0; i < v.size(); i++)
		cout << v[i];
}while(next_permutation(v.begin(),v.end()));		<--- string 및 char, int 의 순열도 구할 수 있다.

auto min_num = min({a,b,c});				<-- a,b,c중에 min값을 찾아 min_num에 대입(3개 이상일 경우 {}로 감싸야한다.)
auto max_num = max({a,b,c});				<-- a,b,c중에 max값을 찾아 max_num에 대입(3개 이상일 경우 {}로 감싸야한다.)
pair<int,int> a1 = minmax(10,200);			<--- 최소값 first, 최대값 second로 들어간다
auto a2 = minmax(10,200);				<--- auto로해도 pair형식으로 들어간다.
pair<int,int> b1 = minmax({10,9,1,2,5,4,7,5,8})		<--- <1,10>이 반환된다.
auto b2 = minmax({10,9,1,2,5,4,7,5,8})			<--- 똑같이 반환된다.
auto max= max_element(v.begin(),v.end())-v.begin()	<--- 그냥 이렇게 쓰는게 나을거같다.
auto min= min_element(v.begin(),v.end())-v.begin()	<--- opteratot를 쓰기 떄문에 변수에 *를 붙이면 에러남 begin()을 뺴는게 맞다. 
auto f = find(v.begin(),v.end(),찾고자하는거)-v.begin()		<--- 찾으면 위치 인덱스 반환 못찾으면 벡터size()만큼index반환 위와 같은 이유로 뺴는게 맞음
```
# queue
```C++
#include <queue>
priority_queue<자료형> q;				      <--- 자료형에 대한 내림차순으로 정렬된다.
priority_queue<자료형,vector<자료형>,less<자료형>> q;	<--- 경우 int에 대한 MaxHeap, 나오는건 큰거부터
priority_queue<자료형,vector<자료형>,greater<자료형>> q; <--- 경우 int에 대한 MinHeap, 나오는건 작은거부터
priority_queue<자료형,vector<자료형>,greater<자료형>> q(v.begin(),v.end()); <---벡터에 있는 값을 바로 넣는다.
q.push(value)						<--- 큐에 값을 넣는다.

top = q.top();					<--- min heap은 가장 작은 값, max heap은 가장 큰 값 리턴한다.
size = q.size();				<--- q에 들어있는 원소의 개수를 반환한다.
empty = q.empty();				<--- 큐에 1개라도 들어있으면 true, 없으면 false리턴
q.pop(); 					<--- min heap은 가장 작은값, max heap은 가장 큰 값을 제거한다.
```
# stack
```C++
#include <stack>
```
# set
```C++
#include <set>
set <자료형> 변수				  <---set은 중복이 안된다. 오름차순으로 정렬을 해준다.
multiset <자료형> 변수			  <--- 중복이 허용되며 오름차순으로 정렬된다. 
변수.insert()				     <--- multiset/set의 삽입
변수.begin()
변수.end()
```
# map
```C++
#include <map>
map <자료형, 자료형> 변수			<--- map은 중복이 안된다.자동 정렬된다 pair형식으로 저장한다. key,값 이런 구조에 유용하다.
multimap<자료형,자료형> 변수			<--- multimap은 중복이 되며 자동 정렬된다.
변수.insert(pair<자료형,자료형>(값,값))	      <--- map/multimap의 삽입.
변수.begin()
변수.end()
변수.first
변수.second
```
# 기타
```C++
조건 ? A : B				       <--- 삼항연산자 조건이 참이면 A, 거짓이면 B를 반환한다.
48~57('0'~'9')65~90('A'~'Z')97~122('a'~'z') 	<--- 아스키 코드 

모듈러 연산의 속성
1. (a + b) % n == ((a % n) + (b % n)) % n
2. (a - b) % n == ((a % n) - (b % n)) % n 	<--- 이때 -연산을 이용할 떄 %를 쓰면 마지막에 +n으로 양수로 만들 수 있다.
3. (a * b) % n == ((a % n) * (b % n)) % n

3 1 4 5 2 를 공백포함하여 cin받고 싶으면 arr[MAX]선언후
for(int i =0; i< MAX; i++)		
	cin >> arr[i]; 이렇게 한다.
	
cout << fixed;
cout.precision(소수점개수);		<-- 123.4567이 123.458로 반올림되어 출력된다.

using 선언문
헤더 밑에 using namespace std; 와 같이
using 변수명 = pair<int,int> 형식처럼 포장할 수 있다.

namespace
모든 식별자(변수,함수,형식 등의 이름)가 고유하도록 보장하는 코드 영역을 정의
기본적으로 전역변수와 일반 함수는 전역 namespace에서 정의됨

예를 들어 main에서 A함수를 호출했을 떄 foo.h와 goo.h헤더 파일에서 각각 A함수가
전역 namespace에 정의되어있으므로 충돌이 발생한다.

두개 이상의 독립된 코드가 함께 사용될 때 서로 이름이 충돌하는 문제를 방지하기 위해
C++에서는 namespace를 사용하여 자체 namespace를 선언한다. 

```
# 코테

## 알고리즘
### DFS/BFS

```C++
그래프에서 방향성이면 v[x].push_back(y); 한쪽만 해도 되지만
무방향이면 
v[x].push_back(y);
v[y].push_back(x);
```
### GREEDY
```C++
```
### 최단 경로
```C++
최단 경로는 크게 두개
다익스트라 : 시작점으로부터 나머지 정점 최단경로
- 공간 복잡도 : V^2(인접행렬), V+E(인접리스트)
- 시간 복잡도 : V^2(인접행렬), E logV(인접리스트+우선순위 큐)

1. 출발점으로부터의 최단거리를 저장할 배열 d[v]를 만들고, 출발 노드에는 0을, 출발점을 제외한 다른 노드들에는 매우 큰 값 INF를 채워 넣는다.
(정말 무한이 아닌, 무한으로 간주될 수 있는 값을 의미한다.)
보통은 최단거리 저장 배열의 이론상 최대값에 맞게 INF를 정한다. 실무에서는 보통 d의 원소 타입에 대한 최대값으로 설정하는 편.

2. 현재 노드를 나타내는 변수 A에 출발 노드의 번호를 저장한다.

3. A로부터 갈 수 있는 임의의 노드 B에 대해, d[A] + P[A][B][7]와 d[B][8]의 값을 비교한다. INF와 비교할 경우 무조건 전자가 작다.
d[A](현재까지 알려진 A까지의 거리)P[A][B](A와 B사이의 거리)

4. 만약 d[A] + P[A][B]의 값이 더 작다면, 즉 더 짧은 경로라면, d[B]의 값을 이 값으로 갱신시킨다.

5. A의 모든 이웃 노드 B에 대해 이 작업을 수행한다.

6. A의 상태를 "방문 완료"로 바꾼다. 그러면 이제 더 이상 A는 사용하지 않는다.

7. "미방문" 상태인 모든 노드들 중, 출발점으로부터의 거리가 제일 짧은 노드 하나를 골라서 그 노드를 A에 저장한다.

8. 도착 노드가 "방문 완료" 상태가 되거나, 혹은 더 이상 미방문 상태의 노드를 선택할 수 없을 때까지, 3~7의 과정을 반복한다

위 작업을 마치고 도착노드에 저장된 값이 A로부터 최단거리다. 만약 이 값이 INF면 중간에 길이 끊긴것이다.

플로이드 와샬 : 각 정접간 최단 경로
- 공간 복잡도 : V^2
- 시간 복잡도 : V^3
장단점
- 간선이 많은 경우 플로이드가 유리할 수 있음
- 한점으로 부터 각 정점까지 최단 거리만 필요하면 다익스트라가 압도적으로 빠름

1. 양의 경로를 갖는 그래프
  1-1. 가중치가 1또는 0인 그래프에서 최단 경로
  	dfs나 bfs로 알 수 있다.
  1-2. 다른 가중치도 가지는 그래프에서 최단 경로
 
	- 단일 출발(single source)단일 노드에서 출발하여 -> 모든 노드 도착
	Dijkstra
	
	- 단일 도착(single detination)모든 노드들에서 출발-> 단일 노드 도착(모든 Edge를 뒤집으면 단일 출발과 동일)
	Dijkstra
	
	- 단일 쌍(single-pair)특정한 노드 u와v에 대해 u에서 v로 가는 최단 경로
	 시간 복잡도에서 1번보다 비효율적
	Dijkstra
	
	- 전체 쌍(all-pair) 모든 노드 쌍에 대한 최단 경로
	FLOYD-Warshall(사이클이 없다면 음의 가중치가 있어도 해결 가능)
	
2. 음의 경로를 갖는 그래프
	Bellman-Ford
	음의 가중치를 가진 경로에도 최단 거리를 구할 수 있다. 경로 추적 가능

SPFA(shortest path faster algorithm)
STL없이 간단하게 구현 가능하다. 평균적으로 빠른 속도를 가짐

```
### 문자열
```C++
```
### 완전탐색
```C++
```
### DP
#### 메모이제이션
메모이제이션(Memoization)
하위 문제를 해결 할 때 그 해결책을 저장해두고, 똑같은 문제가 발생했을 때 저장되어있던 해결책을 가지고 해결한다.
이렇게 동일한 문제를 반복해야 할 경우, 한 번 계산된 결과를 저장해 두었다가 활용하는 방식으로 중복 계산을 줄이는 것을 메모이제이션(Memoization)이라고 한다.
```C++
동적 계획법의 원리는 매우 간단하다. 일반적으로 주어진 문제를 풀기 위해서, 문제를 여러 개의 하위 문제(subproblem)로 나누어 푼 다음, 그것을 결합하여 최종적인 목적에 도달하는 것이다. 각 하위 문제의 해결을 계산한 뒤, 그 해결책을 저장하여 후에 같은 하위 문제가 나왔을 경우 그것을 간단하게 해결할 수 있다. 이러한 방법으로 동적 계획법은 계산 횟수를 줄일 수 있다. 특히 이 방법은 하위 문제의 수가 기하급수적으로 증가할 때 유용하다.

동적 계획 알고리즘은 최단 경로 문제, 행렬의 제곱 문제 등의 최적화에 사용된다. 이것은 동적 계획법은 문제를 해결하기 위한 모든 방법을 검토하고, 그 중에 최적의 풀이법을 찾아내기 때문이다. 문제가 가능한 모든 방법을 충분히 빠른 속도로 처리할 수 있는 경우, 동적 계획법은 최적의 해법이라고 말할 수 있다.

때로는 단순한 재귀함수에 저장 수열(이전의 데이터를 모두 입력하는 수열)을 대입하는 것 만으로도 최적해를 구할 수 있는 동적 알고리즘을 찾을 수 있다. 그러나 대다수의 문제는 이보다 훨씬 더 복잡한 프로그래밍을 요구한다. 그 중에 일부는 여러 개의 매개 변수를 이용하여 재귀 함수를 작성해야 하는 것도 있고, 아예 이러한 방법으로 동적 알고리즘을 짤 수 없는 문제 또한 존재한다. 이러한 퍼즐로는 대표적으로 Egg Dropping Puzzle이 있다.
```
### 시뮬레이션
```C++
```

```C++
cout 대신 printf를
cin 대신 scanf를 습관화하자
```


# 백준

```C++
/*
2021/09/14 프로그래머스
가장 먼 노드 (그래프) 레벨3
n개의 노드가 있는 그래프가 있다.
각 노드는 1부터 n까지 번호가 있다.
1번 노드에서 가장 멀리 떨어진 노드란 최단경로로
이동 했을 떄 간선의 개수가 가장 많은 노드들을 의미한다.
이때 1번 노드에서 가장 벌리 떨어진 노드의 개수를 반환한다.

문제를 보자마자 다익스트라가 떠올랐다.
노드간의 비용을 1로 통일하여
가장 멀리 떨어진 노드를 구하고 
cost배열에서 max값을 가진 index의 개수를 구해서 풀었다.
*/
#include <string>
#include <iostream>
#include <vector>
#include <queue>
#include <limits.h>
using namespace std;
using pii = pair<int, int>;
#define INF INT_MAX 

vector<pii>board[20001];
int cost[20001];
int answer = 0;
int max_cost;
int as;
void dijkstra()
{
    priority_queue<pii, vector<pii>, greater<pii>>pq;
    cost[1] = 0;
    pq.push({ 0,1 });

    while (!pq.empty())
    {
        int w = pq.top().first;
        int node = pq.top().second;
        pq.pop();
        if (max_cost < w)
            max_cost = w;
        for (int i = 0; i < board[node].size(); i++)
        {
            int nw = board[node][i].first;
            int nnode = board[node][i].second;

            if (nw + w < cost[nnode])
            {
                cost[nnode] = nw + w;
                pq.push({ cost[nnode],nnode });
            }
        }
    }
}
int solution(int n, vector<vector<int>> edge) {

    as = n;
    for (int i = 1; i <= n; i++)
        cost[i] = INF;
    for (int i = 0; i < edge.size(); i++)
    {
        board[edge[i][0]].push_back({ 1,edge[i][1] });
        board[edge[i][1]].push_back({ 1,edge[i][0] });
    }

    dijkstra();
    for (int i = 2; i <= n; i++)
    {
        if (max_cost == cost[i])
            answer++;
    }
    return answer;
}
int main()
{
    int a = solution(6, { {3, 6} ,{4, 3},{3, 2},{1, 3},{1, 2},{2, 4},{5, 2} });
    cout << a;
}
```
```C++
/*
2021/09/13
11726번 dp
2xn타일링 실버3
dp를 이용하여 풀었다.
다만 값이 너무 크기때문에  10007을 나눠서 정답을 제출했다.
모듈러 연산의 속성을 이용하여 매번 계산을 할 떄마다
10007을 나눴다.
*/
#include <iostream>
using namespace std;
long long dp[1001];
int n;

int func(int m)
{
    if (m == 1)
        return 1;
    if (m == 2)
        return 2;
    if (dp[m] == 0)
        dp[m] = (func(m - 1) + func(m - 2))%10007;
    return dp[m];
}
int main()
{
    cin >> n;
    dp[1] = 1;
    dp[2] = 2;

    cout << func(n);
}
```
```C++
/*
2021/09/13
9095번 dp
1,2,3 더하기 실버3

dp문제로
1로 시작하여 만들 수 있는 개수는 4
2는 2개, 3은 1개로 놓고
dp[1] = 4, dp[2] = 2, dp[3] = 1로 놓고 했을 땐 틀렸다.

1을 만드는 경우의 수는 1가지,
2는 2가지
3은 4가지의 경우의 수를 갖는 것으로 시작하여  top-down으로풀었다
즉, dp[1] = 1, dp[2] = 2, dp[3] = 4
초기값을 잡는 것이 중요한 것 같다.
*/
#include <iostream>
#include <vector>
#include <algorithm>

using namespace std;

int T;

int dp[12];
int dipr(int n)
{
    if (n == 1)
        return 1;
    else if (n == 2)
        return 2;
    else if (n == 3)
        return 4;

    if (dp[n] == 0)
        dp[n] = dipr(n - 1) + dipr(n - 2) + dipr(n - 3);
    
    return dp[n];
}
int main()
{
    cin >> T;
 
    for (int i = 0; i < T; i++)
    {
        int n;
        cin >> n;
        
        cout << dipr(n) << endl;
    }
}
```

```C++
/*
2021/09/13
1647번 MST
도시 분할 계획 골드4

프림알고리즘으로 구현했지만 한가지 조건이 붙은 문제였다.
MST를 두개로 나누는 것인데 그 중 하나는 노드가 하나만 있어도
된다. 직접 그려서 눈으로 비교하니 MST특성상 가장 큰 cost를
가지는 엣지를 지우면 두개의 tree가 만들어 진다.
max_cost를 선언하여 cost를 더할 때마다 가장 큰 수를 가지고 있다가
마지막에 빼는 식으로 풀었다.
*/

//n개 노드 M개 엣지 무방향

#include <iostream>
#include <vector>
#include <queue>

using namespace std;
using pii = pair<int, int>;
vector<pii> board[100001];
bool visit[100001];
int n, m;
int answer;
int max_cost;
void prime()
{
 
    priority_queue<pii, vector<pii>, greater<pii>> pq;
    pq.push({ 0,1 });
   
    while (!pq.empty())
    {
        int cost = pq.top().first;
        int node = pq.top().second;
        pq.pop();
        if (visit[node])
            continue;
        answer += cost;
        if (max_cost < cost)
            max_cost = cost;
        visit[node] = true;
        for (int i = 0; i < board[node].size(); i++)
        {
            int n_cost = board[node][i].first;
            int n_node = board[node][i].second;

            if (!visit[n_node])
                pq.push({ n_cost, n_node });
        }
    }
}
int main()
{
    cin >> n >> m;
    for (int i = 0; i < m; i++)
    {
        int a, b, c;
        cin >> a >> b >> c;
        board[a].push_back({ c,b });
        board[b].push_back({ c,a });
    }
    prime();
    cout << answer- max_cost;
}
```

```C++
/*
2021/09/12
1003번 dp
피보나치 함수 실버3

시간 제한이 0.25초이기 때문에
dp로 풀어야한다고 생각했다.
*/
#include <iostream>
using namespace std;
int dp[50];
int fibo(int n)
{
    if (n == 0)
        return 0;
    else if (n == 1)
        return 1;

    if (dp[n] == 0)
        dp[n] = fibo(n - 1) + fibo(n - 2);
    return dp[n];
}
int main()
{
    dp[0] = 0;
    dp[1] = 1;
    int t = 0;
    cin >> t;
    for (int i = 0; i < t; i++)
    {
      
        int tmp;
        cin >> tmp;
        if (tmp == 0)
            cout << 1 << " " << 0 << endl;
        else if (tmp == 1)
            cout << 0 << " " << 1 << endl;
        else
        { 
            cout << fibo(tmp - 1) << " " << fibo(tmp) << endl;
 
        }
    }
}



```
```C++
/*
2021/09/12 
1922번 네트워크 연결
골드4 MST

prime알고리즘으로 풀었따.
*/
#include <iostream>
#include <vector>
#include <queue>
#include <utility>

using namespace std;
using pii = pair<int, int>;
int n, e;
vector<pii> board[1001];
bool visit[1001];
long long cost;

void prime()
{
    priority_queue<pii, vector<pii>, greater<pii>> pq;
    pq.push({ 0,1 });
    while (!pq.empty())
    {
        int w = pq.top().first;
        int node = pq.top().second;

        pq.pop();
        if (visit[node])
            continue;
        cost += w;
        visit[node] = true;
        for (int i = 0; i < board[node].size(); i++)
        {
            int nw = board[node][i].first;
            int n_node = board[node][i].second;

            if (!visit[n_node])
                pq.push({ nw,n_node });
        }
    }
}
int main()
{
    cin >> n;
    cin >> e;
    for (int i = 0; i < e; i++)
    {
        int to, from, weight;
        cin >> to >> from >> weight;
        board[to].push_back({weight,from});
        board[from].push_back({weight, to});
    }
    prime();
    cout << cost;
}
```
```C++
/*
2021/09/12
1197번 최소스패닝트리
골드4 최소스패닝트리

전체적인 구조는 bfs와 다익스트라와 비슷하다
우선순위 큐로 최소한의 비용을 바로바로 알수있다.
*/
#include <iostream>
#include <vector>
#include <string>
#include <iostream>
#include <queue>
//1:35
using namespace std;
using pii = pair<long long int, int>; 

int v, e;
vector<pii>board[10001];
bool visit[10001];
long long int cost = 0;


void prime()
{
    priority_queue<pii, vector<pii>, greater<pii>> pq;
    pq.push({ 0,1 });
   
    while (!pq.empty())
    {
        long long int w = pq.top().first;
        int node = pq.top().second;
        pq.pop();

        if (visit[node])
            continue;
        visit[node] = true;
        cost += w;

        for (int i = 0; i < board[node].size(); i++)
        {
            long long int nw = board[node][i].first;
            int n_node = board[node][i].second;

            if (!visit[n_node])
                pq.push({ nw,n_node });
        }
    }
}
int main()
{
   // ios_base::sync_with_stdio(false); cin.tie(NULL);
    cin >> v >> e;

    for (int i = 0; i < e; i++)
    {
        int to, from;
        long long int weight;
        cin >> to >> from >> weight;
        board[to].push_back({ weight,from });
        board[from].push_back({ weight,to });
    }
    prime();
    
    cout << cost;
}

```
```C++
/*
2021/09/10
17413번 문자열
단어뒤집기2 실버3
17:50 ~ 18:14 = 24분
*/
#include <iostream>
#include <vector>
#include <algorithm>
#include <string>
using namespace std;

string str;
int main()
{
    getline(cin, str);
    string tmp;
    bool flag = false;
    string answer;
    for (int i = 0; i < str.length(); i++)
    {
        
        if (str[i] == '<' || str[i] == ' ')
        {
            if(str[i] == '<')
                flag = true;
            reverse(tmp.begin(), tmp.end());
            answer += tmp;
            answer += str[i];
            tmp = "";
        }
        else if (str[i] == '>')
        {
            flag = false;
            answer += str[i];
        }
        else
        {
            if (flag) {
                answer += str[i];
                continue;
            }
            else
            {
                tmp += str[i];
            }
        }
    }
    reverse(tmp.begin(), tmp.end());
    answer += tmp;
    cout << answer;
}
```
```C++
/*
2021/09/10
11656번 문자열
접미사 배열 실버4

접미사 배열은 문자열 S의 모든 접미사를 사전순으로 정렬해 놓은 배열이다.
문자열이 주어졌을 때 모든 접미사를 사전수으로 정렬한 다음 출력하라.
*/
#include <iostream>
#include <string>
#include <vector>
#include <algorithm>
using namespace std;
vector<string> v;
string str;

int main()
{
    cin >> str;
    for (int i = 0; i < str.length(); i++)
    {
        string tmp;
        for (int j = i; j < str.length(); j++)
        {
            tmp += str[j];
        }
        v.push_back(tmp);
    }
    sort(v.begin(), v.end());
    for (auto i : v)
        cout << i << endl;
}
```

```C++
/*
    2021/09/04
    5052번 전화번호 목록
    골드4
    이 문제는 주어진 여러개 전화번호 중에
    서로 포함되는 전화번호가 있으면 NO를
    없으면 YES를 출력하는 문제이다.
    string find를 사용하여 문제를 해결하려 했지만 시간초과가 떴다.
    반복문을 줄이는 방법을 생각해봐야겠다.
*/
#include <iostream>
#include <string>
#include <vector>
#include <algorithm>
using namespace std;
//16:10 ~

int T;
int main()
{
    cin >> T;
    
    for (int i = 0; i < T; i++)
    {
        int num_count;
        cin >> num_count;
        vector<string>s;
        int flag = 0;
        for (int j = 0; j < num_count; j++)
        {
            string str;
            cin >> str;
            s.push_back(str);
        }
        for (int j = 0; j < s.size(); j++)
        {
            for (int h = j + 1; h < s.size(); h++)
            {
                if(!s[h].find(s[j]))
                    flag = 1;
             //   if (find(s[h].begin(), s[h].end(), s[j]) == s[h].end())
                    
            }
        }
        if (flag == 1)
            cout << "NO" << endl;
        else
            cout << "YES" << endl;
    }
}

```

```C++
/*
2021/09/04
10610번 30
이 문제는 간단한 문자열 문제다.
주어진 문자열이 30의 배수가 되는지 확인하고
30의 배수일경우 문자를 조합하여 가장 큰 수를 출력하는 문제다.
각 자리수를 더했을 떄 3의 배수이면 그 수는 3의 배수 인 것을 이용하여 풀었다.
하지만 3이 아닌 30의 배수를 만들어야하기에
0이 포함이 안된다면 무조건 -1을 출력한다.
*/
#include <iostream>
#include <string>
#include <vector>
#include <algorithm>
//15:29 ~15:39  = 10분
using namespace std;

bool cmp(char a, char b)
{
    if (a > b)
        return true;
    return false;
}
int main()
{
    string str;
    cin >> str;
    long long int check = 0;
    int answer = 0;
    bool zero = false;
    string tmp;
    for (int i = 0; i < str.size(); i++)
    {
        if (str[i] == '0')
            zero = true;
        check += (str[i] - '0');
    }
    if (check % 3 != 0 || zero == false)
        cout << -1;
    else
    {
        sort(str.begin(), str.end(), cmp);
        cout << str;
    }
}

```
```C++
2021/09/02
1120번 문자열
이 문제는 a와 b문자열의 차이를 최소화 하는 문제다.
a문자열은 b문자열보다 길이가 같거나 작다
이때 a문자열에 앞이나 뒤에 아무 문자를 추가할 떄 둘의 차이가 가장 적은 경우를 반환하는 문제다.
처음엔 deque를 사용해서 풀까 생각했다. 하지만 머리속으로 그려보니
결국 처음 a문자열과 b문자열의 차이가 가장 적은 구간을 찾는 것이 문제였다. 사실 pair까지 쓸 필요도 없고 int로 반환하여 출력하면 끝인 문제이다.
#include <iostream>
#include <string>
#include <vector>
#include <set>
#include <utility>
#define MAX 51
using namespace std;
//19:40 ~ 08:17

pair<int, int> cmp(string a, string b)
{
	int answer = MAX;
	int index = 0;
	for (int i = 0; i < b.length(); i++)
	{
		int num = 0;
        if (a.length() > b.length())
            return { index,answer };
		for (int j = i; j < a.length(); j++)
		{
			
            if (a[j] == '!')
                continue;
			if (b[j] != a[j])
				num++;
		}
		if (answer > num)
		{
			answer = num;
			index = i;
		}
        a.insert(0, "!");
	}
	return { index,answer };
}
int main()
{
	string a, b;
	cin >> a >> b;
	pair<int, int> p;

	p = cmp(a, b);
	int index = p.first;
	int count = p.second;
    cout << count;
}
```

```C++
2021/08/22 +ADD

#include <iostream>
#include <vector>
#include <string>
#include <algorithm>
#include <deque>
using namespace std;

int main()
{
	ios_base::sync_with_stdio(0);
	cin.tie(0);

	int T;
	cin >> T;
	for (int i = 0; i < T; i++)
	{
		string com, arr;
		int arr_size;
		cin >> com >> arr_size >> arr;

		deque<int>q;
		string num;
		for (int j = 0; j < arr.length(); j++) {
			if (arr[j] == '[')
				continue;
			if (isdigit(arr[j]))
				num += arr[j];
			else
			{
				if (!num.empty())
				{
					q.push_back(stoi(num));
					num = "";
				}
			}
		}
		bool flag = true;//-->, 1 == <--
		bool error_flag = true;
		for (int j = 0; j < com.length(); j++)
		{
			if (com[j] == 'R')
				flag = !flag;
			else
			{//command == 'D'
				if (q.empty())
				{
					error_flag = false;
					cout << "error" << endl;
					break;
				}
				else
					flag ? q.pop_front() : q.pop_back();
			}
		}
		if (error_flag)
		{
			if (flag)
			{
				cout << '[';
				int qsize = q.size();
				for (int j = 0; j < qsize; j++)
				{
					if (j == qsize - 1)
						cout << q.front();
					else
						cout << q.front() << ",";
					q.pop_front();
				}
			}
			else
			{
				cout << '[';
				int qsize = q.size();
				for (int j = 0; j < qsize; j++)
				{
					if (j == qsize - 1)
						cout << q.back();
					else
						cout << q.back() << ",";
					q.pop_back();
				}
			}
			cout << "]" << endl;
		}
	}
}


////////////////////////////////////////////////////////////////////////////////////////


2021/08/19
5430번 AC
#include <iostream>
#include <vector>
#include <string>
#include <algorithm>
#include <deque>
using namespace std;

int T;
int main()
{
    cin >> T;
    for (int i = 0; i < T; i++)
    {
        string com,arr;
        int arr_size;
        cin >> com;
        cin >> arr_size;
        cin >> arr;
        deque<int>q;
        string num;
        bool error_flag = 0;
        if (arr_size == 0)
        {
            cout << "error" << endl;
            error_flag = true;
        }
        if (error_flag)
            continue;
        for (int j = 0; j < arr.size(); j++){
            if (arr[j] == '[')
                continue;
            if (isdigit(arr[j]))
            {
                num += arr[j];
            }
            else
            {
                q.push_back(stoi(num));
                num = "";
            }     
        }
        int flag = 0;//-->, 1 == <--
       
        
        for (int j = 0; j < com.size(); j++)
        {
            if (com[j] == 'R')
                flag == 0 ? flag = 1 : flag = 0;
            else
            {//command == 'D'
                if (!q.size())
                {
                    cout << "error" << endl;
                    error_flag = true;
                    break;
                }
                if (flag)
                {// <--
                    q.pop_back();
                }
                else
                {// -->
                    q.pop_front();
                }
            }
        }
        if (error_flag)
            continue;
        cout << '[';
        if (flag)
        {
            int qsize = q.size();
            for (int j = 0; j < qsize; j++)
            {
                if (j == qsize - 1)
                    cout << q.back();
                else
                    cout << q.back() << ",";
                q.pop_back();
            }
        }
        else
        {
            int qsize = q.size();
            for (int j = 0; j < qsize; j++)
            {
                if (j == qsize - 1)
                    cout << q.front();
                else
                    cout << q.front() << ",";
                q.pop_front();
            }
        }
        cout << "]" << endl;

    }
}


```
```C++
2021/08/16
2468번 dfs
장마철에 대비해서 다음과 같은일을 게획하고 있다. 어떤 지역의 높이 정보를 파악한다. 
각 높이에 따른 비가 왔을 떄 지역이 비높이 이하면 잠긴다고 하고 대각선일 경우를 
제외하고 좌우양옆으로 잠기지 않으면 그 지역은 하나라고 볼떄
모든 높이의 물이 찼을 떄 안전한 구역의 최대값을 구하는 문제이다. 
#include <iostream>
#include <vector>
#include <algorithm>
#include <queue>
using namespace std;


int n;
int board[101][101];
bool visit[101][101];
int dx[4] = { 0,0,1,-1 };
int dy[4] = { 1,-1,0,0 };
int max_count = 0;
void dfs(int high, int x, int y) {
   
    visit[x][y] = true;
    for (int i = 0; i < 4; i++){
        int nx = dx[i] + x;
        int ny = dy[i] + y;
        if (nx < 0 || nx >= n || ny < 0 || ny >= n)
            continue;
        if (!visit[nx][ny] && board[nx][ny] > high)
            dfs(high, nx, ny);
    }
}
int main() {

	cin >> n;
	int max_high = 0;
	for (int i = 0; i < n; i++) {
		for (int j = 0; j < n; j++) {
			int high;
			cin >> high;
			max_high = max(high, max_high);
			board[i][j] = high;
		}
	}
	int answer = 0;
	for (int i = 0; i <= max_high; i++) {
        for (int j = 0; j < n; j++){
            for (int h = 0; h < n; h++){
                if (!visit[j][h] && board[j][h] > i){
                    dfs(i, j, h);
                    max_count++;
                }
            }
        }
		answer = max(max_count, answer);
        max_count = 0;
        memset(visit, false, sizeof(visit));
	}
	cout << answer;
}
```

```C++
2021/08/16
2164번 큐

#include <iostream>
#include <deque>

using namespace std;

int main()
{
    deque <int>dq;

    int n = 0;
    cin >> n;
    for (int i = 1; i <= n; i++)
    {
        dq.push_front(i);
    }
    while (!dq.empty())
    {
        if (dq.size() == 1)
        {
            cout << dq.front();
            break;
        }
        dq.pop_back();
        int top = dq.back();
        dq.pop_back();
        dq.push_front(top);
    }
}

```

```C++
2021/08/12
1764번 문자열
A의 명단과 B의 명단이 주어졌을 떄
겹치는 이름을 사전순으로(오름차순) 출력한다.

set을 사용했다. 오름차순과 중복된 부분을 찾는 것은 set이 효율적이라 생각했다.
A를 입력받고 B를 입력 받을 떄 A에 find함수를 사용하여 중복여부를 체크하고다른 set에 넣어줌으로서
정렬역시 할 필요없게 되었다. 
#include <iostream>
#include <set>
#include <algorithm>
#include <string>
#include <vector>

using namespace std;

int main()
{
    int n, m;
    cin >> n >> m;
    set<string>s;
    set<string>answer;
    for (int i = 0; i < n; i++)
    {
        string str;
        cin >> str;
        s.insert(str);
    }
    for (int i = 0; i < m; i++)
    {
        string str;
        cin >> str;
        if (s.find(str) != s.end())
            answer.insert(str);
    }
    cout << answer.size() << '\n';
    for (auto i : answer)
        cout << i << '\n';
}

```

```C++
2021/08/12
1427번 문자열
숫자 N이 주어지면 각 자리수를 내림차순으로 정렬한다.

#include <iostream>
#include <string>
#include <vector>
#include <algorithm>
using namespace std;

int main(){
    string str;
    cin >> str;
    sort(str.begin(), str.end(),less<>);
    cout << str;
}
```

```C++
2021/08/04
3190번 구현(시뮬,디큐) 
게임 snake를 구현하는 문제이다.
뱀이 나와서 기어다니는데 사과를 먹으면 뱀 길이가 늘어난다.
게임 종료 조건은 벽, 자기자신의 몸과 부딪히면 게임은 끝난다.

게임은 NXN 보드에서 진행되고 사과가 있다.
사과를 먹으면 몸 길이가 늘어난다.
초기에 뱀은 0,0에 위치하고 뱀의 길이는 1이다.(꼬리-머리)가 1인줄 알았지만, 머리 하나만 있을때
1이였다. 뱀은 처음에 오른쪽으로 움직인다.

뱀은 매 초마다 움직이는데 다음 규칙이있다.
- 머리를 기준을 다음칸에 위치한다.
- 이동한 칸에 사과가 있다면 사과는 없어지고 꼬리는 그대로이며 몸길이는 1 증가한다.
- 이동한 칸에 사과가 없다면 몸 길이를 줄여 꼬리가 위치한 칸을 비워준다. 몸길이는 그대로다.

사과의 위치와 뱀의 이동 경로가 주어질 때 게임이 몇 초에 끝나는지 계산하는 문제이다.

이 문제는 deque로 풀었다. 처음엔 Linked list로 풀려고 했지만 그럴 필요가 없을 것 같아서
좀 더 생각 해본 결과 deque로 풀었다. 꼬리와 머리를 동시에 pop,push를 해줘야하는데
vector와 queue는 이 조건을 충족하지 못한다.

주석을 달아 놨지만 알고리즘은 다음과 같다.
먼저 input을 받는다. 사과는 board에 1로 표현하며, 뱀은 2로 표현한다.
방향이 전환하는 시점은 배열에 담아 index를 초, data를 방향으로 구분했다.
deque를 뱀으로 놓고 초기 값인 0,0을 담아줬다.
while문으로 턴은 진행된다.
0. time++
1. 좌표를 뱀의 방향으로 한칸 이동하여 게임 종료 조건을 확인한다.
2. 사과가 있을 떄
- board에서 사과를 지운다.
- deque에서 현재 좌표를 push_front하여 머리를 늘려준다. 
- 꼬리를 움직일 필요가 없다.
3. 사과가 없을 때
- 머리 부분을 board에서 2로 바꿔준다.
- 길이는 그대로이기에 deque의 맨 끝의 x,y좌표를 board에서 지워준다.
- deque에서 꼬리를 지우고(popback) 현재 좌표를 머리에 추가한다.(push_front)
4. 뱀의 방향 전환
- 뱀의 방향 전환을 위해 초기에 저장했던 방향전환 배열에 L이나D가 있는지 확인한다.
만약 있다면 방향 전환을 해주고 없다면 지금 방향 그대로 1칸 전진해준다.

#include <iostream>
#include <vector>
#include <deque>

using namespace std;
using pii = pair<int, int>;

int board[101][101];
int N, K, L;
char move_arr[10001];
int dx[4] = { 0,1,0,-1 };
int dy[4] = { 1,0,-1,0 };

int move(int d, char m)
{
    if (m == 'L')
    {
        if (d == 0)
            return 3;
        else
            return d - 1;
    }
    else if (m == 'D')
    {
        if (d == 3)
            return 0;
        else
            return d + 1;
    }
}
void input()
{
    cin >> N;
    cin >> K;
    for (int i = 0; i < K; i++) {
        int apple_x, apple_y;
        cin >> apple_x >> apple_y;
        board[apple_x-1][apple_y-1] = 1;
        // 사과는 1로 표현
    }
    cin >> L;
    for (int i = 0; i < L; i++) {
        int seconds;
        char direction;
        cin >> seconds >> direction;
        move_arr[seconds] = direction;
        // 방향 전화 배열을 만들어 index를 초, data는 방향
    }
}
int main()
{
    input();
    deque<pii>q;// 뱀의 몸체
    q.push_back({ 0,0 }); //뱀 초기값
    board[0][0] = 2; //맵에서 뱀은 2로 표현
    int x=0, y=0; //좌표
    int d=0; // 방향
    int time = 0; // 시간
    while (1)
    {
        time++;
        int nx = x + dx[d];
        int ny = y + dy[d];
        if (nx >= N || ny >= N || nx < 0 || ny < 0 || board[nx][ny] == 2)
            break; // 뱀의 이동이 맵을 벗어나거나 몸통에 닿을 때
        else if (!board[nx][ny])
        {//사과가 없을 때 - 맵은 0
            board[nx][ny] = 2;
            board[q.back().first][q.back().second] = 0;
            q.pop_back(); // 꼬리의 이동
            q.push_front({ nx,ny }); //머리의 이동
        }
        else if (board[nx][ny])
        {//사과를 먹을 떄 - 맵은 1
            board[nx][ny] = 0;
            q.push_front({ nx,ny });
        }
        if(move_arr[time] == 'L' || move_arr[time] == 'D') 
            d = move(d, move_arr[time]);//뱀의 방향전환
        x = nx;
        y = ny;
    }
    cout << time;
}

```

```C++
2021/07/28
15686번 구현
치킨 배달 골드5

NxN 도시가 있을 떄
0은 빈칸, 1은 집, 2는 치킨집으로 나타낸다.
이때 각 치킨집으로부터 최단거리의 집들을 구한다
치킨집에서 집까지 가장 많은 최소거리를 가진 치킨집 상위 M개의
집까지의 거리들을 모두 더하여 반환하는 문제이다.

처음에 최단 거리를 보고 bfs로 풀어보려고했다.
치킨집을 각 큐에 넣어 치킨집고유인덱스, 거리, x,y촤표를 구하여
정렬 후 M개를 뽑으려고했지만 실패했다. 뭔가 하면서도 잘못된걸 느꼈는데
디버깅 결과 집까지 거리를 계속 가지고 가기때문에 중복되는 거리가 존재하여
값이 더 많이 나온다는 것이다.
다익스트라 혹은 브루트포스로 풀어봐야겠다. 


///////////////////////07/31 add++ ///////////////////////
이전의 코드는 최소거리를 가지는 m개의 치킨집의 인덱스를 구했었다.
이 상태로 각 집까지 최소거리를 구하려고 했지만, 시간초과로 실패했다.

 알고리즘을 다시 설계했다.
m개의 치킨집을 가질 수 있는 모든 치킨집을 조합하여 집으로부터 값이 최소가 되게끔 하였다.
하지만 구현부분에서 애를 먹었고, 다른 사람의 코드를 참고하였다.
DFS로 푼 코드이다.
집0 - min(치킨집0,치킨집1)
집1 - min(치킨집0,치킨집1)
집2 - min(치킨집0,치킨집1)
집3 - min(치킨집0,치킨집1)
... 집.size()

집0 - min(치킨집0,치킨집2)
집1 - min(치킨집0,치킨집2)
집2 - min(치킨집0,치킨집2)
집3 - min(치킨집0,치킨집2)
... 집.size()
과 같은 형태로 값을 구하여 최솟 값을 반환한다.

#include <iostream>
#include <vector>
#include <algorithm>
using namespace std;
const int MAX = 50;
const int INF = 987654321;
int N, M;
int result;
int graph[MAX][MAX];
vector<pair<int, int>> house, chicken;
bool visited[13];
//맨해튼 거리
int distance(pair<int, int> a, pair<int, int> b)
{
    return abs(a.first - b.first) + abs(a.second - b.second);
}
void DFS(int idx, int selected)
{
    //조건 만족
    if (selected == M)
    {
      //  cout << "인덱스 : " << idx << endl;
        int tempResult = 0;
        for (int i = 0; i < house.size(); i++)
        {
            int dist = INF;
            for (int j = 0; j < chicken.size(); j++)
                if (visited[j]) {
                    dist = min(dist, distance(house[i], chicken[j]));
                  //  cout << "하우스" << i << " 치킨"<< j << " 거리는 : " << dist << endl;
                }
            tempResult += dist;
        //    cout << "최소 거리 : " << tempResult << endl;
         //   cout << endl;
        }
        result = min(result, tempResult);
     //   cout << "최솟 값 :" << result << endl;
        return;
    }
    //기저 사례
    if (idx == chicken.size())
        return;
    //프랜차이즈 선정
    visited[idx] = true;
    DFS(idx + 1, selected + 1);
    //프랜차이즈 선정 X
    visited[idx] = false;
    DFS(idx + 1, selected);
}

int main(void)
{
    ios_base::sync_with_stdio(0);
    cin.tie(0);
    cin >> N >> M;
    for (int i = 0; i < N; i++)
        for (int j = 0; j < N; j++)
        {
            cin >> graph[i][j];
            if (graph[i][j] == 1)
                house.push_back({ i, j });
            else if (graph[i][j] == 2)
                chicken.push_back({ i, j });
        }
    result = INF;
    DFS(0, 0);
    cout << result << "\n";
    return 0;
}

//////////////////////////////////////////////////////////

///////////////////////07/28 add++////////////////////////
브루트포스로 구현했다.
예외 처리 좀만 더 하면 될듯
#include <iostream>
#include <vector>
#include <queue>
#include <limits.h>
#include <algorithm>
#define INF INT_MAX;
using namespace std;

using pii = pair<int, int>;
int n; // 정사각형
int m; //상위 치킨 집 개수;
int board[501][501];

int get_dist(int x1, int y1, int x2, int y2){
    return abs(x1 - x2) + abs(y1 - y2);
}
int main()
{
    vector<pii> c;
    vector<pii> h;
    cin >> n >> m;
    for (int i = 0; i < n; i++) {
        for (int j = 0; j < n; j++) {
            cin >> board[i][j];
            if (board[i][j] == 1)
                h.push_back({ i,j });
            else if (board[i][j] == 2)
                c.push_back({ i,j });
        }
    }
    vector<pii>answer(h.size());
        for (int j = 0; j < h.size(); j++){
            answer[j] = { 0,2147483647 };
        }

    vector<int>ch(c.size());
    for (int i = 0; i < c.size(); i++) {
        for (int j = 0; j < h.size(); j++) {
           int dist =  get_dist(c[i].first, c[i].second, h[j].first, h[j].second);
           
           if (answer[j].second > dist) {
               answer[j].first = i;
               answer[j].second = dist;
           }  
        }
    }
    vector<int>real(c.size());
    for (int i = 0; i < answer.size(); i++)
    {
        int f = answer[i].first;
        int s = answer[i].second;
        real[f] += s;
    }
    sort(real.begin(), real.end());
    reverse(real.begin(), real.end());
    vector<int>ve;
   

}
//////////////////////////////초기 코드//////////////////////
#include <iostream>
#include <vector>
#include <queue>
#include <limits.h>
#include <algorithm>
using namespace std;

using pii = pair<int,pair<int, pair<int, pair<int, int>>>>;

int n; // 정사각형
int m; //상위 치킨 집 개수;
int board[501][501];
int visit[501][501];
int house_c = 0;
int chicken_c = 0;
int dx[4] = { 1,-1,0,0 };
int dy[4] = { 0,0,1,-1 };
int bfs(queue<pii>pq)
{
    
    while (!pq.empty()){
        int dist = pq.front().first;
        int c_c = pq.front().second.first;
        int cost = pq.front().second.second.first;
        int x = pq.front().second.second.second.first;
        int y = pq.front().second.second.second.second;
        pq.pop();

        if (house_c == 0)
            break;
        for (int i = 0; i < 4; i++){
            int nx = dx[i] + x;
            int ny = dy[i] + y;
            if (nx >= n || nx < 0 || ny >= n || ny < 0)
                continue;
            if (!visit[nx][ny] && board[nx][ny] != 2) {
              
                if (board[nx][ny] == 1) {
                    pq.push({dist+1, {c_c, { cost + dist,{nx,ny} } } });
                    house_c--;
                }
                else
                    pq.push({dist+1, { c_c,{cost,{nx,ny} } } });
                visit[nx][ny] = true;
            }
        }
    }
    
    
    vector<int> v(chicken_c);
    while (!pq.empty())
    {
        int c_c = pq.front().second.first;
        int cost = pq.front().second.second.first;
        pq.pop();
        v[c_c] += cost;
    }
    sort(v.begin(), v.end());
    int answer = 0;
    for (int i = 0; i < m; i++)
        answer += v[i];
    return answer;
}
int main()
{
    queue<pii>pq;
    cin >> n >> m;
    for (int i = 0; i < n; i++) {
        for (int j = 0; j < n; j++) {
            cin >> board[i][j];
            if (board[i][j] == 1)
                house_c++;
            else if (board[i][j] == 2) {
                pq.push({ 1,{chicken_c,{0,{i,j}}}});
                chicken_c++;
            }   
        }
    }
    cout << bfs(pq) << endl;

}
```

```C++
2021/07/27
14500번 구현
테트로미노 골드5

폴리오미노 = 1x1 정사각형을 여러개 이어 붙인 도형이다.
테트로미노 = 정사각형 4개를 이어붙인 폴리오미노.

테트리스처럼 ㅡ, ㅁ, ㄴ,ㄹ,ㅗ형태 5가지가있다.

각 칸안에 점수가 적힌 nxm 보드판위에 테트로미노를 대칭 및 회전을해서 보드판위에 올려놓고
놓인 칸에 있는 숫자들의 합을 최대로 하는 문제이다.

이 문제는 보자마자 브루트포스가 생각이 났다.
구조체로 테트로미노를 만들고 각 도형의 초기값을 설정하여 진행했다.
하지만 예제는 다 맞지만 틀렸다고 나온다. 반례를 찾아가며 다시 봐야겠다.

//////07/28 추가 add+/////////////////////
도형을 90도씩 돌린 건 생각 했지만
대칭일 경우를 고려 안한 것이 원인이였다.
총 6개의 데이터를 추가하여 문제를 해결했다.
다른 사람 코드와 비교해보니
도형의 초기값을 설정하는 것 똑같았다.
나는 구조체를 사용지만 dfs로 푼 사람들이 많았다.
/////////////////////////추가 코드 add++////////////////////////
#include <iostream>
#include <vector>
#include <algorithm>
#include <queue>
using namespace std;

using pii = pair<int, int>;
int answer = 0;
int n, m;
int board[501][501];
struct tetro {
	pii node1;
	pii node2;
	pii node3;
	pii node4;
};
tetro right(tetro te) {
	te.node1.second++;
	te.node2.second++;
	te.node3.second++;
	te.node4.second++;
	return te;
}
tetro down(tetro te) {
	te.node1.first++;
	te.node2.first++;
	te.node3.first++;
	te.node4.first++;
	return te;
}
bool range_check(tetro te) {
	int x1 = te.node1.first;
	int x2 = te.node2.first;
	int x3 = te.node3.first;
	int x4 = te.node4.first;

	int y1 = te.node1.second;
	int y2 = te.node2.second;
	int y3 = te.node3.second;
	int y4 = te.node4.second;
	if (x1 >= n || x1 < 0)
		return false;
	if (x2 >= n || x2 < 0)
		return false;
	if (x3 >= n || x2 < 0)
		return false;
	if (x4 >= n || x2 < 0)
		return false;

	if (y1 >= m || y1 < 0)
		return false;
	if (y2 >= m || y2 < 0)
		return false;
	if (y3 >= m || y3 < 0)
		return false;
	if (y4 >= m || y4 < 0)
		return false;

	return true;
}
int get_score(tetro te)
{
	int sum = 0;
	int x1 = te.node1.first;
	int x2 = te.node2.first;
	int x3 = te.node3.first;
	int x4 = te.node4.first;

	int y1 = te.node1.second;
	int y2 = te.node2.second;
	int y3 = te.node3.second;
	int y4 = te.node4.second;
	sum += board[x1][y1];
	sum += board[x2][y2];
	sum += board[x3][y3];
	sum += board[x4][y4];
	return sum;
}

int main()
{
	cin >> n >> m;
	for (int i = 0; i < n; i++) {
		for (int j = 0; j < m; j++) {
			cin >> board[i][j];
		}
	}
	tetro answer_temp;
	tetro te1; // ----
	te1.node1 = { 0,0 };
	te1.node2 = { 0,1 };
	te1.node3 = { 0,2 };
	te1.node4 = { 0,3 };
	tetro te2; // I
	te2.node1 = { 0,0 };
	te2.node2 = { 1,0 };
	te2.node3 = { 2,0 };
	te2.node4 = { 3,0 };

	tetro te3; //ㅁ
	te3.node1 = { 0,0 };
	te3.node2 = { 0,1 };
	te3.node3 = { 1,0 };
	te3.node4 = { 1,1 };

	tetro te4; // ㄴ
	te4.node1 = { 0,0 };
	te4.node2 = { 1,0 };
	te4.node3 = { 2,0 };
	te4.node4 = { 2,1 };

	tetro te5; // 
	te5.node1 = { 0,0 };
	te5.node2 = { 1,0 };
	te5.node3 = { 0,1 };
	te5.node4 = { 0,2 };

	tetro te6;
	te6.node1 = { 0,0 };
	te6.node2 = { 0,1 };
	te6.node3 = { 1,1 };
	te6.node4 = { 2,1 };

	tetro te7;
	te7.node1 = { 1,0 };
	te7.node2 = { 1,1 };
	te7.node3 = { 1,2 };
	te7.node4 = { 0,2 };

	tetro te8;//ㄹ
	te8.node1 = { 0,0 };
	te8.node2 = { 1,0 };
	te8.node3 = { 1,1 };
	te8.node4 = { 2,1 };

	tetro te9;
	te9.node1 = { 1,0 };
	te9.node2 = { 1,1 };
	te9.node3 = { 0,1 };
	te9.node4 = { 0,2 };

	tetro te10;//ㅗ
	te10.node1 = { 0,0 };
	te10.node2 = { 0,1 };
	te10.node3 = { 0,2 };
	te10.node4 = { 1,1 };

	tetro te11;
	te11.node1 = { 0,0 };
	te11.node2 = { 1,0 };
	te11.node3 = { 2,0 };
	te11.node4 = { 1,1 };

	tetro te12;
	te12.node1 = { 1,0 };
	te12.node2 = { 0,1 };
	te12.node3 = { 1,1 };
	te12.node4 = { 2,1 };

	tetro te13;
	te13.node1 = { 0,1 };
	te13.node2 = { 1,0 };
	te13.node3 = { 1,1 };
	te13.node4 = { 1,2 };

	tetro te14;
	te14.node1 = { 0,1 };
	te14.node2 = { 0,0 };
	te14.node3 = { 1,0 };
	te14.node4 = { 2,0 };

	tetro te15;
	te15.node1 = { 0,0 };
	te15.node2 = { 1,0 };
	te15.node3 = { 1,1 };
	te15.node4 = { 1,2 };

	tetro te16;
	te16.node1 = { 2,0 };
	te16.node2 = { 2,1 };
	te16.node3 = { 1,1 };
	te16.node4 = { 0,1 };

	tetro te17;
	te17.node1 = { 0,0 };
	te17.node2 = { 0,1 };
	te17.node3 = { 0,2 };
	te17.node4 = { 1,2 };
	
	tetro te18;
	te18.node1 = { 0,1 };
	te18.node2 = { 1,1 };
	te18.node3 = { 1,0 };
	te18.node4 = { 2,0 };

	tetro te19;
	te19.node1 = { 0,0 };
	te19.node2 = { 0,1 };
	te19.node3 = { 1,1 };
	te19.node4 = { 1,2 };

	queue<tetro>q;
	q.push(te1);
	q.push(te2);
	q.push(te3);
	q.push(te4);
	q.push(te5);
	q.push(te6);
	q.push(te7);
	q.push(te8);
	q.push(te9);
	q.push(te10);
	q.push(te11);
	q.push(te12);
	q.push(te13);
	q.push(te14);
	q.push(te15);
	q.push(te16);
	q.push(te17);
	q.push(te18);
	q.push(te19);

	while (!q.empty())
	{
		tetro temp = q.front();
		q.pop();
		int sum = get_score(temp);
		if (answer < sum)
		{
			answer = sum;
			answer_temp = temp;
		}
			
		tetro temp_fisrt = temp;
		while (1)
		{
			while (1)
			{
				temp = right(temp);
				if (range_check(temp))
				{
					sum = get_score(temp);
					if (answer < sum)
					{
						answer = sum;
						answer_temp = temp;
					}
						
				}
				else
					break;
			}
			temp = temp_fisrt;
			temp = down(temp);
			temp_fisrt = temp;
			if (range_check(temp))
			{
				sum = get_score(temp);
				if (answer < sum){
					answer = sum;
					answer_temp = temp;
				}
					
			}
			else
				break;
		}
	}
	cout << answer << endl;
	//cout << "(" << answer_temp.node1.first << " , " << answer_temp.node1.second << ")" << endl;
	//cout << "(" << answer_temp.node2.first << " , " << answer_temp.node2.second << ")" << endl;
	//cout << "(" << answer_temp.node3.first << " , " << answer_temp.node3.second << ")" << endl;
	//cout << "(" << answer_temp.node4.first << " , " << answer_temp.node4.second << ")" << endl;
}
/////////////////////////////////////////////////////////////////////////////////////////////////

#include <iostream>
#include <vector>
#include <algorithm>
#include <queue>
using namespace std;

using pii = pair<int, int>;
int answer = 0;
int n, m;
int board[501][501];
struct tetro {
	pii node1;
	pii node2;
	pii node3;
	pii node4;
};
tetro right(tetro te) {
	te.node1.second++;
	te.node2.second++;
	te.node3.second++;
	te.node4.second++;
	return te;
}
tetro down(tetro te) {
	te.node1.first++;
	te.node2.first++;
	te.node3.first++;
	te.node4.first++;
	return te;
}
bool range_check(tetro te) {
	int x1 = te.node1.first;
	int x2 = te.node2.first;
	int x3 = te.node3.first;
	int x4 = te.node4.first;

	int y1 = te.node1.second;
	int y2 = te.node2.second;
	int y3 = te.node3.second;
	int y4 = te.node4.second;
	if (x1 >= n || x1 < 0)
		return false;
	if (x2 >= n || x2 < 0)
		return false;
	if (x3 >= n || x2 < 0)
		return false;
	if (x4 >= n || x2 < 0)
		return false;

	if (y1 >= m || y1 < 0)
		return false;
	if (y2 >= m || y2 < 0)
		return false;
	if (y3 >= m || y3 < 0)
		return false;
	if (y4 >= m || y4 < 0)
		return false;

	return true;
}
int get_score(tetro te)
{
	int sum = 0;
	int x1 = te.node1.first;
	int x2 = te.node2.first;
	int x3 = te.node3.first;
	int x4 = te.node4.first;

	int y1 = te.node1.second;
	int y2 = te.node2.second;
	int y3 = te.node3.second;
	int y4 = te.node4.second;
	sum += board[x1][y1];
	sum += board[x2][y2];
	sum += board[x3][y3];
	sum += board[x4][y4];
	return sum;
}

int main()
{
	cin >> n >> m;
	for (int i = 0; i < n; i++) {
		for (int j = 0; j < m; j++) {
			cin >> board[i][j];
		}
	}
	tetro te1; // ----
	te1.node1 = { 0,0 };
	te1.node2 = { 0,1 };
	te1.node3 = { 0,2 };
	te1.node4 = { 0,3 };
	tetro te2; // I
	te2.node1 = { 0,0 };
	te2.node2 = { 1,0 };
	te2.node3 = { 2,0 };
	te2.node4 = { 3,0 };

	tetro te3; //ㅁ
	te3.node1 = { 0,0 };
	te3.node2 = { 0,1 };
	te3.node3 = { 1,0 };
	te3.node4 = { 1,1 };

	tetro te4; // ㄴ
	te4.node1 = { 0,0 };
	te4.node2 = { 1,0 };
	te4.node3 = { 2,0 };
	te4.node4 = { 2,1 };

	tetro te5; // 
	te5.node1 = { 0,0 };
	te5.node2 = { 1,0 };
	te5.node3 = { 0,1 };
	te5.node4 = { 0,2 };

	tetro te6;
	te6.node1 = { 0,0 };
	te6.node2 = { 0,1 };
	te6.node3 = { 1,1 };
	te6.node4 = { 2,1 };

	tetro te7;
	te7.node1 = { 1,0 };
	te7.node2 = { 1,1 };
	te7.node3 = { 1,2 };
	te7.node4 = { 0,2 };

	tetro te8;//ㄹ
	te8.node1 = { 0,0 };
	te8.node2 = { 1,0 };
	te8.node3 = { 1,1 };
	te8.node4 = { 2,1 };

	tetro te9;
	te9.node1 = { 1,0 };
	te9.node2 = { 1,1 };
	te9.node3 = { 0,1 };
	te9.node4 = { 0,2 };

	tetro te10;//ㅗ
	te10.node1 = { 0,0 };
	te10.node2 = { 0,1 };
	te10.node3 = { 0,2 };
	te10.node4 = { 1,1 };

	tetro te11;
	te11.node1 = { 0,0 };
	te11.node2 = { 1,0 };
	te11.node3 = { 2,0 };
	te11.node4 = { 1,1 };

	tetro te12;
	te12.node1 = { 1,0 };
	te12.node2 = { 0,1 };
	te12.node3 = { 1,1 };
	te12.node4 = { 2,1 };

	tetro te13;
	te13.node1 = { 0,1 };
	te13.node2 = { 1,0 };
	te13.node3 = { 1,1 };
	te13.node4 = { 1,2 };

	queue<tetro>q;
	q.push(te1);
	q.push(te2);
	q.push(te3);
	q.push(te4);
	q.push(te5);
	q.push(te6);
	q.push(te7);
	q.push(te8);
	q.push(te9);
	q.push(te10);
	q.push(te11);
	q.push(te12);
	q.push(te13);

	while (!q.empty())
	{
		tetro temp = q.front();
		q.pop();
		int sum = get_score(temp);
		if (answer < sum)
			answer = sum;
		tetro temp_fisrt = temp;
		while (1)
		{
			while (1)
			{
				temp = right(temp);
				if (range_check(temp))
				{
					sum = get_score(temp);
					if (answer < sum)
						answer = sum;
				}
				else
					break;
			}
			temp = temp_fisrt;
			temp = down(temp);
			temp_fisrt = temp;
			if (range_check(temp))
			{
				sum = get_score(temp);
				if (answer < sum)
					answer = sum;
			}
			else
				break;
		}
	}
	cout << answer << endl;
}
```
```C++
2021/07/26
1476번 구현
날짜 계산 실버5
어떤 나라는 수3개를 이용해서 연도를 나타낸다.
e,s,m으로 나타내는데  (1 ≤ E ≤ 15, 1 ≤ S ≤ 28, 1 ≤ M ≤ 19)의 범위를 가진다.

1년은 준규가 살고있는 나라에서는 1 1 1로 나타낼 수 있다. 1년이 지날 때마다, 세 수는 모두 1씩 증가한다.
만약, 어떤 수가 범위를 넘어가는 경우에는 1이 된다.

예를 들어, 15년은 15 15 15로 나타낼 수 있다. 하지만, 1년이 지나서 16년이 되면 16 16 16이 아니라
1 16 16이 된다. 이유는 1 ≤ E ≤ 15 라서 범위를 넘어가기 때문이다.
E, S, M이 주어질때 연도를 출력하는 문제이다.
#include <iostream>
#include <vector>
#include <algorithm>
#include <functional>
#pragma warning(disable : 4996)
using namespace std;

#define div_E 15
#define div_S 28
#define div_M 19

int E, S, M;
int main() {
    cin >> E >> S >> M;
    int year = 1;
    while (1) {
        int sub_E = ((year - 1) % div_E) + 1;
        int sub_S = ((year - 1) % div_S) + 1;
        int sub_M = ((year - 1) % div_M) + 1;
        if (sub_E == E && sub_S == S && sub_M == M) {
            printf("%d", year);
            return 0;
        }
        year++;
    }

    return 0;
}
```

```C++
2021/07/26
1475번 구현
방 번호 실버5

0~9까지 이뤄진 숫자 스티커가 있을때 방번호를 주었을 때 필요한 스티커 세트의 최솟값을 구한다.
6은 9로 9는 6으로도 사용할 수있다.

#include <iostream>
#include <vector>
#include <string>
#include <algorithm>
using namespace std;

int main()
{
    string str;
    cin >> str;
    vector<int> arr(10);
    for (int i = 0; i < str.size(); i++)
         arr[str[i] - '0']++;   
    int nine_six = arr[9]+ arr[6];
    if (nine_six % 2 == 1)
        arr[9] = (nine_six / 2) + 1;
    else
        arr[9] = nine_six / 2;
    arr[6] = 0;

    sort(arr.begin(), arr.end());
    cout << arr[arr.size()-1];
}
```

```C++
2021/07/26
1193번 구현
분수찾기 브론즈2

 나열된 분수들을 1/1 -> 1/2 -> 2/1 -> 3/1 -> 2/2 -> … 과 같은 지그재그 순서로 차례대로 1번, 2번, 3번, 4번, 5번, … 분수라고 하자.
x가 주어졌을때 x번째 분수를 구하는 문제다.

#include <iostream>

using namespace std;
using pii = pair<int, int>;
int main()
{

    int x;
    cin >> x;
    int count = 0;
    int sum = 0;
    while (1)
    {
        sum += count;
        if (sum >= x)
            break;
        count++;
    }
    sum -= count;
    if (count % 2)
    {//홀수
        int mo = count;
        int ja = 1;
        pii bunsu = {mo,ja};
        sum++;
        while (sum != x)
        {
            bunsu.first--;
            bunsu.second++;
            sum++;
        }
        cout << bunsu.first << "/" << bunsu.second << endl;
    }
    else
    {//짝수
        int mo = 1;
        int ja = count;
        pii bunsu = { mo,ja };
        sum++;
        while (sum != x)
        {
            bunsu.first++;
            bunsu.second--;
            sum++;
        }
        cout << bunsu.first << "/" << bunsu.second << endl;
    }
}
```

```C++
2021/07/24
1966번 구현
프린터 큐 실버3

<int,int>형 큐에 중요도를 따져 입력으로 받은 숫자는
몇 번쨰로 pop이 되는지 구현하는 문제이다.

#include <iostream>
#include <queue>
#include <vector>
#include <algorithm>
using namespace std;

using pii = pair<int, int>;

int main()
{
	int test_case;
	cin >> test_case;

	for (int i = 0; i < test_case; i++)
	{
		int n, m;
		cin >> n >> m;
		queue<pii>q;
		vector<int>im;
		int count = 1;
		for (int j = 0; j < n; j++)
		{
			int num;
			cin >> num;
			im.push_back(num);
			q.push({ num,j });
		}
		sort(im.begin(), im.end());

	tryAgain:
		int f = q.front().first;
		int s = q.front().second;
		int max = im[im.size() - 1];
		if (f < max)
		{
			q.pop();
			q.push({ f,s });
			goto tryAgain;
		}
		else if (f == max)
		{
			if (s == m)
			{
				cout << count << endl;
			}
			else
			{
				q.pop();
				im.pop_back();
				count++;
				goto tryAgain;
			}
		}
	}
}
```

```C++
2021/07/23
7568번 구현 
덩치 실버5

n명의 사람마다 키와 몸무게를 주어지고
키와 몸무게 둘다 동시에 다른 사람보다 크면 덩치가 크다고 한다.
만약 둘 중하나가 작고 크면 동급이라고 보고
둘다 작으면 덩치가 작다고 표현한다
각 사람의 등수를 출력하는 문제이다.

이 문제는 몸무게와 키를 벡터에 담아
CMP로 정렬을 하려 했으나
이중 포문을 이용해 한 사람마다 모든 사람과 비교하고 랭킹을 정하는 것으로 풀었다.

#include <iostream>
#include <algorithm>
#include <vector>
using namespace std;

int n;
using pii = pair<int, int>;
vector<pii>v;

int main()
{
    cin >> n;
    int ranking = 1;
    for (int i = 0; i < n; i++)
    {
        int w, h;
        cin >> w >> h;
        v.push_back({ w,h });
    }
    for (int i = 0; i < v.size(); i++)
    {
        for (int j = 0; j < v.size(); j++)
        {
            if (v[i].first < v[j].first && v[i].second < v[j].second)
                ranking++;
        }
        cout << ranking << " ";
        ranking = 1;
    }
}
```

```C++
2021/07/23
14503번 구현
로봇 청소기 골드5

구현문제이다. 로봇 청소기의 움직임을 조건으로 받는다.
조건에 만족하여 문제를 풀면 된다.
문제 설명을 잘 봐야 이해가 될 것 같다.

정답은 맞았지만 조금은 지저분하다는 생각이 들었다. 다른 사람 코드를 분석해봐야겠다.

#include <iostream>
#include <string>
using namespace std;

int dx[4] = {-1,0,1,0};
int dy[4] = {0,1,0,-1};
int room[51][51];
bool visit[51][51];

int turn_left(int w)
{
    if (w == 0)
        w = 3;
    else
        w -= 1;
    return w;
}
int main()
{
    int answer = 0;
    int n, m;
    cin >> n >> m;
    int robot_x, robot_y, way;
    cin >> robot_x >> robot_y >> way;
    for (int i = 0; i < n; i++)
    {
        for (int j = 0; j < m; j++)
        {
            int a;
            cin >> a;
            room[i][j] = a;
        }
    }
    int count = 0;

number1:
    if (!room[robot_x][robot_y] && !visit[robot_x][robot_y])
    {
        visit[robot_x][robot_y] = true;
        answer++;
    }
        
number2:
        way = turn_left(way);
        int nx = robot_x + dx[way];
        int ny = robot_y + dy[way];
        if (!room[nx][ny] && !visit[nx][ny])
        {
            robot_x = nx;
            robot_y = ny;
            count = 0;
            goto number1;
        }
        else if (visit[nx][ny] || room[nx][ny])
        {
            count++;
            if(count != 4)
                goto number2;
        }
        if (count == 4)
        {
            int way_tmp = way;
            if (way == 0)
                way = 2;
            else if (way == 1)
                way = 3;
            else if (way == 2)
                way = 0;
            else if (way == 3)
                way = 1;
            int tmp_x = robot_x + dx[way];
            int tmp_y = robot_y + dy[way];
            if (tmp_x < 0 || tmp_y < 0 || tmp_x >= n || tmp_y >= m || room[tmp_x][tmp_y])
            {
                cout << answer;
                return 0;
            }
            else
            {
                way = way_tmp;
                robot_x = tmp_x;
                robot_y = tmp_y;
                count = 0;
                goto number2;
            }  
        }  
}
```

```C++
2021/07/23
10845번 큐
큐 실버4

큐를 구현하는 문제이다.

*****주의*****
공백까지 온전한 한줄을 받아오려겨
string의 getline(cin,str)함수를 썼다.
하지만 cin >> n을 하고 바로 getline함수를 쓰면
n을 입력했던 버퍼에 엔터('\n')가 그대로 남아있어
getline()에 들어가기 떄문에 getline은 엔터를 인식하고
문자열을 입력 받지 않는다.

이를 해결하기위해 cin.ignore()이라는 함수를 사용한다.
이 함수는 입력 버퍼의 모든 내용을 제거해주어 getline이 정상적으로 동작 할 수있다.
***************
#include <iostream>
#include <queue>
#include <vector>
#include <string>
using namespace std;

int n;
int main()
{
    cin >> n;
    cin.ignore();
    queue<int>q;
    for (int i = 0; i < n; i++)
    {
        string str;
       
        getline(cin,str);
        string com;
        string num;
        for (int j = 0; j < str.size(); j++)
        {
            if (isalpha(str[j]))
                com += str[j];
            else if (isdigit(str[j]))
                num += str[j];
        }
        if (com == "push"){
            q.push(stoi(num));
        }
        else if (com == "pop") {
            if (q.size() == 0)
                cout << -1 << endl;
            else{
                cout << q.front() << endl;
                q.pop();
            }
        }
        else if (com == "size") {
            cout << q.size() << endl;
        }
        else if (com == "empty") {
            if (q.empty())
                cout << 1 << endl;
            else
                cout << 0 << endl;
        }
        else if (com == "front") {
            if (q.size() == 0)
                cout << -1 << endl;
            else
                cout << q.front() << endl;
        }
        else if (com == "back") {
            if (q.size() == 0)
                cout << -1 << endl;
            else
                cout << q.back() << endl;
        }
    }
}
```

```C++
2021/07/22
7576번 bfs
토마토 실버1

2차원 배열의 토마토 박스가 있을 떄
토마토가 없으면 -1, 안익었으면 0, 익었으면 1의 토마토 상태를 나타낸다.
이때 익은 토마토 상하좌우에 익지 않은 토마토가 있으면 하루가 지나면 익게 된다.
전체 토마토가 익으려면 며칠이 걸리는가.
만약 다 익을 수 없는 상황이라면 -1을 출력하고, 이미 다 익었으면 0을 출력한다.

//고찰// 
bfs로 구현했지만
상화좌우로 익을때마다 큐에 들어가게되어 날짜도 하루가 아닌 하루에 익은 토마토 만큼
더 늘어났다.
이 부분만 해결하면 될 것 같다.

////////////////////07/23 추가 add+//////////////////////////////////
상하좌우로 토마토가 익은 숫자를 나누거나 뺴는 것으로 해결 하려 했으나
큐에 계속 들고다니는 것으로 문제를 해결 했다.
////////////////////////////////정답/////////////////////////////
#include <iostream>
#include <vector>
#include <queue>

using namespace std;

int box[1001][1001];
using pii = pair<int,pair<int, int>>;
bool visit[1001][1001];
int dx[4] = { 1,-1,0,0 };
int dy[4] = { 0,0,1,-1 };
int n, m;// n은 세로, m은 가로
int main()
{
    cin >> m >> n;
    queue<pii>q;
    int live = 0;
    for (int i = 0; i < n; i++){
        for (int j = 0; j < m; j++) {
            int tomato;
            cin >> tomato;
            box[i][j] = tomato;
            if (tomato == 1)
            {
                q.push({ 0,{ i,j } });
                visit[i][j] = true;
            }
            else if (tomato == -1)
                visit[i][j] = true;
            else
                live++;
        }
    }
    if (live == 0){
        cout << 0;
        return 0;
    }
    int return_day = 0;
    while (!q.empty())
    {
        int x = q.front().second.first;
        int y = q.front().second.second;
        int now_day = q.front().first;
        return_day = now_day;
        q.pop();
        for (int i = 0; i < 4; i++) {
            int nx = dx[i] + x;
            int ny = dy[i] + y;
            if (nx < 0 || ny < 0 || nx >= n || ny >= m)
                continue;
            if (!visit[nx][ny] && !box[nx][ny]) {
                q.push({ now_day + 1,{ nx, ny } });
                box[nx][ny] = 1;
                live--;
    
                visit[nx][ny] = true;
            }
        }
        if (q.size() == 0)
            break;
    }
    if (live != 0)
        cout << -1;
    else
        cout << return_day;
}
////////////////////////////////////////////////////////////////
#include <iostream>
#include <vector>
#include <queue>

using namespace std;

int box[1001][1001];
using pii = pair<int, int>;
bool visit[1001][1001];
int dx[4] = { 1,-1,0,0 };
int dy[4] = { 0,0,1,-1 };
int n, m;// n은 세로, m은 가로
int main()
{
    cin >> m >> n;
    queue<pii>q;
    int live = 0;
    for (int i = 0; i < n; i++){
        for (int j = 0; j < m; j++) {
            int tomato;
            cin >> tomato;
            box[i][j] = tomato;
            if (tomato == 1)
            {
                q.push({ i,j });
                visit[i][j] = true;
            }
            else if (tomato == -1)
                visit[i][j] = true;
            else
                live++;
        }
    }
    if (live == 0){
        cout << 0;
        return 0;
    }
    int day = 0;
    while (!q.empty())
    {
        int x = q.front().first;
        int y = q.front().second;

        q.pop();
       
        for (int i = 0; i < 4; i++) {
            int nx = dx[i] + x;
            int ny = dy[i] + y;
            if (nx < 0 || ny < 0 || nx >= n || ny >= m)
                continue;
            if (!visit[nx][ny] && !box[nx][ny]) {
                q.push({ nx, ny });
                box[nx][ny] = 1;
                live--;
                visit[nx][ny] = true;
            }
        }
        if (q.size() == 0)
            break;
        day++;
    }
    if (live != 0)
        cout << -1;
    else
        cout << day;
}
```
```C++
2021/07/20
11779번 최소비용 구하기2
다익스트라 골드3

n개의 도시가있고, 한 도시에서 출발하여 다른 도시에 도착하는 m개의 버스가 있다.
A도시->B도시로 갈때 버스비용을 최소화한다.
최소비용, 경로, 경로에 포함된 도시 개수를 출력하는 문제다.

이 문제는 일반 다익스트라 처럼 풀면 되지만
거쳐간 도시들을 반환하는 것이 다른 문제와 차별점이다.
처음엔 2차원인접행렬로 각 도시마다 체크를 해주었지만
그럴 필요 없이 큐를 pair<int,vector<int>> 형으로 선언하여 경로를 가지고 다니는 것으로
문제를 해결했다.
처음에는 시작점을 넣어주고 적은 비용을 업데이트 할 때
기존에 있던 벡터를 복사하여 다음 노드를 넣고 다시 큐에 넣는 방식으로 진행하였다.
다익스트라 함수 자체를 반환하여 size와 요소를 차례대로 출력하였다.
재미 있는 문제였다.

#define _CRT_SECURE_NO_WARNINGS
#include <iostream>
#include <vector>
#include <queue>
#include <limits.h>
#define INF INT_MAX
using namespace std;
using pii = pair<int,vector<int>>;

vector<pii>bus[100001];
int cost[1001];
int n, m;
int from, to;
vector<int>answer;
vector<int> dijkstra(int from, int to)
{
    priority_queue<pii, vector<pii>, greater<pii>>pq;
  
    pq.push({ 0,{from} });
    cost[from] = 0;

    while (!pq.empty())
    {
        int cur_node = pq.top().second[pq.top().second.size()-1];
        int cur_cost = pq.top().first;
        vector<int>cur_vector = pq.top().second;

        if (cur_node == to)
        {
            answer.push_back(cur_cost);
            return cur_vector;
        }
        pq.pop();
        if (cur_cost > cost[cur_node])
            continue;
        for (int i = 0; i < bus[cur_node].size(); i++)
        {
            if (bus[cur_node][i].second.size() == 0)
                continue;
            int next_node = bus[cur_node][i].second[bus[cur_node][i].second.size()-1];
            int next_cost = bus[cur_node][i].first;

            if (next_cost + cur_cost < cost[next_node])
            {
                vector<int>tmp(cur_vector);
                tmp.push_back(next_node);
                cost[next_node] = next_cost + cur_cost;
                pq.push({cost[next_node],tmp});

            }
        }
    }
}
int main()
{
    scanf("%d",&n);
    scanf("%d",&m);
    for (int i = 0; i <= m; i++)
    {
        if (i == m)
        {
            
            scanf("%d %d", &from,&to);
            break;
        }
        int a, b, c;
        scanf("%d %d %d",&a,&b,&c);
        vector<int>tmp;
        tmp.push_back(b);
        bus[a].push_back({ c,tmp });
    }
    for (int i = 1; i <= n; i++) { cost[i] = INF; }
   vector<int> road =  dijkstra(from,to);
    cout << answer[0] << endl;
    cout << road.size() << endl;
    for (auto i : road)
        cout << i << " ";
}

```

```C++
2021/07/20
2665번 미로만들기
다익스트라 골드4

nxn의 배열이 있다.
지나갈 수 있는 방은 1, 없는 방은 0이라 할 때 길이 막혀있다면 방을 뚫어야한다.
0,0에서 n-1,n-1까지 최소한의 방을 뚫어 개수를 반환한다.

얼마 전에 풀었던 문제와 유사 한 것 같다.
조심해야할 점은 다익스트라와는 다르게 bfs로 풀었기에
bfs는 q.push()하고 바로 visit[] = true;를 해줘야한다.
그렇지 않으면 하나의 노드에 대해 엄청난 양의 요소가 큐에 들어갈 것이고 메모리 초과로
이어진다.

#include <iostream>
#include <vector>
#include <queue>
#include <string>
#define MAX 51
using namespace std;
using pii = pair<int, pair<int, int>>;

int board[MAX][MAX];
bool visit[MAX][MAX];
int n;
int dx[4] = { 1,-1,0,0 };
int dy[4] = { 0,0,1,-1 };
int answer;
void dijkstra()
{
    priority_queue<pii, vector<pii>, greater<pii>>pq;
    pq.push({ 0,{ 0,0 } });
    visit[0][0] = true;
    while (!pq.empty())
    {
        int x = pq.top().second.first;
        int y = pq.top().second.second;
        int num = pq.top().first;
        pq.pop();
       
        if (x == n - 1 && y == n - 1)
            answer = num;
        for (int i = 0; i < 4; i++)
        {
            int nx = dx[i] + x;
            int ny = dy[i] + y;
            int nnum = 0;
            if (!board[nx][ny]) { nnum = 1; }
            if (nx < 0 || nx >= n || ny < 0 || ny >= n)
                continue;
            if (!visit[nx][ny])
            {
                pq.push({ num + nnum,{ nx,ny } });
                visit[nx][ny] = true;
            }
                
        }
    }
}
int main()
{
    cin >> n;
    for (int i = 0; i < n; i++) {
        string tmp;
        cin >> tmp;
        for (int j = 0; j < tmp.size(); j++) {
            board[i][j] = tmp[j] - '0';
        }
    }
    dijkstra();
    cout << answer;
}
```

```C++
2021/07/17
1939번 골드4
중량제한

N개의 섬으로 이뤄진 나라가 있다.
이 섬끼리는 다리가 설치되어있는데 각 다리마다 제한된 중량이 다르다.
공장1에서 공장2까지 물건을 운반할떄 최대 몇까지 실고 갈 수 있는지 찾는 문제이다.

기존의 다익스트라와는 다른 문제다.
공장1에서 공장2까지 어떠한 루트를 통해 갈때 최소의 값이 가장 큰 수를 구하는 문제이다.
다익스트라를 좀 변형해서 해봤지만 실패했다.
다른 방법을 찾아봐야겠다.

07/20 추가+
첫 번째와 두 번째 방법을 합쳐서 문제를 풀수 있었다.
첫 번째는 cost배열을 선언하여 모든 노드 중 가장 적은 가중치를 반환했고,
두 번째는 from에서 to로 가는 방법중 가장 큰 가중치를 반환했다. 하지만 시간이 초과되고 메모리를 너무 많이 썼던 것이 문제였다.
마지막 방법은 dijkstra로 풀되 노드마다 cost를 비교하여 가장 큰 가중치를 반환하였다.
결국 알고리즘은 첫 날에 생각했지만, 문제를 너무 어렵게 생각 했던 것 같다.

07/19 추가+
하나의 노드에서 다른 노드로 갈수있는 방법을 모두 벡터에 담아 가중치기준으로 정렬하고
가장 높은 가중치를 우선순위 큐에 담으면서 목표 노드에 도달하면 가중치를 반환하는 방법을 
구현했지만 메모리 초과가 떴다. 다른 방법을 생각해봐야겠다.
////////////////////////////add 07/20(정답)////////////////////////////////////
#define _CRT_SECURE_NO_WARNINGS
#include <iostream>
#include <vector>
#include <queue>
#include <limits.h>
#include <algorithm>
#define INF LLONG_MAX
using namespace std;
using pii = pair<long long, int>;
vector<pii>board[100001];
bool visit[100001];
int n, m;
int fac1, fac2;
long long answer;
void dijkstra(int from, int to)
{
	priority_queue<pii, vector<pii>, less<pii>>pq;

    pq.push({ INF,from });
   
    while (!pq.empty())
    {
        int cur_node = pq.top().second;
        long long min_cost = pq.top().first;

        pq.pop();
        visit[cur_node] = true;
        if (cur_node == to)
        {
            answer = min_cost;
            break;
        }
        for (int i = 0; i < board[cur_node].size(); i++)
        {
            int next_node = board[cur_node][i].second;
            long long next_cost = board[cur_node][i].first;
            long long temp = min_cost;
            if (!visit[next_node])
            {
                if (min_cost > next_cost)
                    temp = next_cost;
                pq.push({ temp,next_node });
                
            }
        }
    }
}
int main()
{
	scanf("%d %d", &n, &m);
	for (int i = 0; i <= m; i++)
	{
		if (i == m) {
			scanf("%d %d", &fac1, &fac2);
		}
		else
		{
			int a, b;
			long long c;
			scanf("%d %d %lld", &a, &b, &c);
			board[a].push_back({ c,b });
			board[b].push_back({ c,a });
		}
	}
    dijkstra(fac1, fac2);
    cout << answer;
}
///////////////////////////////////////////////////////////////////////////////

//////////////////////////////add 07/19/////////////////////////////////////////
#define _CRT_SECURE_NO_WARNINGS
#include <iostream>
#include <vector>
#include <queue>
#include <limits.h>
#include <algorithm>
#define INF LLONG_MAX
using namespace std;
using pii = pair<long long, int>;
vector<pii>board[100001];
bool visit[100001];
int n, m;
int fac1, fac2;
vector<int>answer;
int dijkstra(int from, int to)
{
	priority_queue<pii, vector<pii>, greater<pii>>q;

	q.push({ 0,from });

	while (!q.empty())
	{
		long long cur_cost = q.top().first;
		int cur_node = q.top().second;
		if (cur_node == to)
		{
			return cur_cost;
		}
		q.pop();
		//visit[cur_node] = true;
		vector<pii>tmp;
		for (int i = 0; i < board[cur_node].size(); i++)
		{
			long long next_cost = board[cur_node][i].first;
			int next_node = board[cur_node][i].second;
			//if (!visit[next_node])
				tmp.push_back({ next_cost ,next_node });
		}
		if (tmp.size() == 0)
			continue;
		sort(tmp.begin(), tmp.end(), greater<>());
		q.push({ tmp[0].first, tmp[0].second });

		for (int i = 0; i < tmp.size(); i++)
		{
			if (i == 0)
				continue;
			if (tmp[0].first == tmp[i].first)
				q.push({ tmp[i].first, tmp[i].second });
			else
				break;
		}
	}
    return 0;
}
int main()
{
	scanf("%d %d", &n, &m);
	for (int i = 0; i <= m; i++)
	{
		if (i == m) {
			scanf("%d %d", &fac1, &fac2);
		}
		else
		{
			int a, b;
			long long c;
			scanf("%d %d %lld", &a, &b, &c);
			board[a].push_back({ c,b });
			board[b].push_back({ c,a });
		}
	}
	cout << dijkstra(fac1, fac2);

}
/////////////////////////////////////////////////////////////////////

/////////////////////////////////////07/17///////////////////////////
#define _CRT_SECURE_NO_WARNINGS
#include <iostream>
#include <vector>
#include <queue>
#include <limits.h>

#define INF INT_MAX;
using namespace std;
using pii = pair<int, int>;
vector<pii> board[100001];
int cost[100001];
int n ,m;//a-b, b-a, limits c;
int fac1, fac2;

void dijkstra()
{
   // priority_queue<pii, vector<pii>, less<pii>>pq;
    priority_queue<int, vector<int>, less<int>>pq;
    pq.push(fac1);
   
    
    cost[fac1] = 0;
    while (!pq.empty())
    {
      //  int weight = pq.top().first;
        int node = pq.top();
        pq.pop();
        for (int i = 0; i < board[node].size(); i++)
        {
            int next_w = board[node][i].first;
            int next_n = board[node][i].second;
            if (next_w < cost[next_n])
            {
                cost[next_n] = next_w;
              //  pq.push({,});
                pq.push(next_n);
            }
        }
;    }
}
int main()
{
    scanf("%d %d",&n,&m);
    for (int i = 0; i <= m; i++){
        if (i == m) {
            scanf("%d %d", &fac1, &fac2);
        }
        else{
            int a, b, c;//1< a,b <= n; 1<=c <= 1000000000
            scanf("%d %d %d", &a, &b, &c);
            board[a].push_back({ c, b});
            board[b].push_back({ c, a });
        }
    }
    for (int i = 1; i <= n; i++) { cost[i] = INF; }
    dijkstra();

}
```

```C++
2021/07/15
4485번
녹색 옷 입은 애가 젤다지? 골드4

이차원 맵에 각 숫자가 있는데 0,0에서 n-1,n-1까지 갈때 지나치는 숫자들은 다 더한다.
이때 최단 비용을 구하라
bfs와 다익을 합친 느낌이였다.
수월하게 풀수있었다.

#define _CRT_SECURE_NO_WARNINGS
#include <iostream>
#include <vector>
#include <queue>
#include <string>
#include <limits.h>
using namespace std;
using pii = pair<int, pair<int,int>>;

#define INF INT_MAX
int dx[4] = { 1,-1,0,0 };
int dy[4] = { 0,0,1,-1 };
int board[126][126];
int cost[126][126];

int dijkstra(int n)
{
    priority_queue<pii, vector<pii>, greater<pii>>pq;
  
    pq.push({ board[0][0],{0,0} });
    cost[0][0] = board[0][0];
    while (!pq.empty())
    {
        int x = pq.top().second.first;
        int y = pq.top().second.second;
        int cur_cost = pq.top().first;
        if (x == n - 1 && y == n - 1) {
            return  cur_cost;
        }
        pq.pop();

        for (int i = 0; i < 4; i++)
        {
            int nx = x + dx[i];
            int ny = y + dy[i];
            int ncost = cur_cost + board[nx][ny];
            if (nx <0 || nx >=n || ny < 0 || ny >= n)
                continue;
            if (cost[nx][ny] > ncost)
            {
                cost[nx][ny] = ncost;
                pq.push({ ncost,{nx,ny} });
            }
              
            
        }
    }

}
int main()
{
    int count = 1;
    while (1)
    {
        int n;
        cin >> n;
        if (n == 0)
            break;
        
        
        for (int i = 0; i < n; i++)
        {
            for (int j = 0; j < n; j++)
            {
               
                int c;
                scanf("%d", &c);
                board[i][j] = c;
                cost[i][j] = INF;
            }
        }
        cout << "Problem " << count << ": " << dijkstra(n) << endl;
        count++;
    }
}
```

```C++
2021/07/15
1238번
파티 골드3
N개의 각 마을에 한명의 학생이 살고있다.
이 학생들이 X번 마을에 모여서 파티를 할때
각 학생들이 자기 마을에서 파티를 다녀올 때 왕복 시간이 가장 긴 학생의 최단소요시간을 출력한다.

이 문제는 다익스트라로 쉽게 풀었다.
다익스트라의 구조를 알고 있으면 간단한 문제이다.
각 학생이 X번째 마을에 갈때 최단시간을 저장하고
X번째 마을에서 각 학생의 마을까지 최단시간을 구해 더한다.
이 값중 가장 큰 값을 출력하면 문제는 해결된다.

#include <iostream>
#include <vector>
#include <queue>
#include <limits.h>
using namespace std;
#define INF INT_MAX
using pii = pair<int, int>;
vector<pii> city[1001];

int n, m, x;

int dijkstra(int node, int x)
{
    priority_queue<pii, vector<pii>, greater<pii>> pq;
    int cost[1001];
    for (int i = 1; i <= n; i++) cost[i] = INF;
    pq.push({ 0,node });
    cost[node] = 0;

    while (!pq.empty())
    {
        int cur_node = pq.top().second;
        int cur_cost = pq.top().first;
        pq.pop();

        if (cur_cost > cost[cur_node])
            continue;
        for (int i = 0; i < city[cur_node].size(); i++)
        {
            int next_node = city[cur_node][i].second;
            int next_cost = city[cur_node][i].first;

            if (next_cost + cur_cost < cost[next_node])
            {
                cost[next_node] = next_cost + cur_cost;
                pq.push({ cost[next_node],next_node });
            }
        }
    }
    return cost[x];
}
int main()
{
    cin >> n >> m >> x;

    for (int i = 0; i < m; i++)
    {
        int from, to, weight;
        cin >> from >> to >> weight;
        city[from].push_back({ weight, to });
    }
    vector<int>from_to((n+1));

    for (int i = 1; i <= n; i++)
    {
        if (i == x)
            continue;
       from_to[i] = dijkstra(i, x);
       from_to[i] += dijkstra(x, i);
    }
  
    int answer = 0;
    for (auto i: from_to){
        if (answer < i)
            answer = i;
    }
    cout << answer;
}
```
```C++
2021/07/11
13549번
숨바꼭질3 골드5

수빈이는 동생과 숨바꼭질을 할때 수빈이는 점 0<=수빈<=100000에 있고
동생도 같은 범위 내에 있다. 수빈이는 걷거나 순간이동을 할 수 있는데
만약 수빈이의 위치가 x일때 걷는다면 1초 후에 x-1 또는 x+1로 이동한다.
순간이동을 하면 0초 후에 2*x의 위치로 이동한다.
수빈이와 동생의 위치가 주어졌을 때, 수빈이가 동생을 찾을 수 있는 가장 빠른 시간이 몇 초 후인지 구하는
프로그램을 작성하는 문제이다.

dfs로 풀려고 했다. 하지만 시간초과, 런타임 에러를 거쳐 틀렸다고 나왔다.
다익스트라로 풀어야하나 싶다.

+추가)
코드를 올리고 바로 메인 함수를 바꿔줬는데 바로 맞았다.
만약 수빈이랑 동생이랑 같은 위치면 0을 출력하고
수빈이가 동생보다 더 오른쪽에 있을 때 수빈 - 동생을 하고
수빈이가 동생보다 왼쪽에있을때만 dfs를 돌았는데
이 조건문들을 지우고 모든 경우에 dfs를 돌게 바꾸니 바로 됐다.


#include <iostream>
#include <queue>
#include <vector>
#include <algorithm>
using namespace std;
using pii = pair<int, int>;
int n, k;
bool visit[100002];
int dx[3] = { 1,-1,2 };
int answer;
void bfs(int subin, int brother)
{
	priority_queue<pii, vector<pii>, greater<pii>> q;
	q.push({ 0,subin });

	while (!q.empty())
	{
		int x = q.top().second;
		int count = q.top().first;
		q.pop();
		visit[x] = true;
		// cout << x << ": 현재 위치" << endl;
		 //cout << count << ": 걸린 시간" << endl << endl;

		if (x == brother)
		{
			answer = count;
			break;
		}
		for (int i = 0; i < 3; i++)
		{
			int nx;
			//int ncount;
			if (i == 2)
			{
				nx = dx[i] * x;
			}
			else
			{
				nx = dx[i] + x;

			}

			if (nx < 0 || nx > 100001)
				continue;
			if (!visit[nx])
			{
				if (i == 2)
				{
					q.push({ count ,nx });
				}

				else
				{
					q.push({ count + 1, nx });
				}

			}
		}
	}
}
/*int main()
{
	cin >> n >> k;
	if (k == n)
		cout << 0;
	else if (k < n)
		cout << k - n;
	else
	{
		bfs(n, k);

		cout << answer;
	}
}*/
int main()
{//위가 아닌 이게 맞음, 정정 후 코드
    cin >> n >> k;
    bfs(n, k);
    cout << answer;
}
```
```C++
2021/07/07
1502번 dijkstra
특정한 최단 경로 골드4

방향성이 없는 그래프가 주어질때, 1->N번 정점으로 최단거리를 이동한다.
이때 두가지 조건을 만족하면서 이동한다.
1. 임의로 주어진 두 정점은 반드시 통과한다.
2. 한번 이동했던 정점은 물론, 한번 이동했던 간선도 다시 이동할 수 있다.

이 문제는 인접그래프와 dijkstra를 이용하여 풀었다.
처음엔 1->N을 갈 수있는 모든 방법을 탐색하여 두 정점을 지나는 경우에 작은 값을
출력하는 방식으로 했지만, 시간 초과가 일어났다. 당연한 결과지만 푸는 것에 집중하느라
고려하지 않았었다.

두번째 시도로
dijkstra를 여러번 나누어 시도했다. A와 B를 반드시 지나야할 노드라고 가정할 때,
1. 1-> A-> B-> N
2. 1-> B-> A-> B
이 두가지 경우로 나누어 최단거리를 구한 후 작은 값을 반환하는 방법이다.
1번,2번도 각 구간별로 나누어 dijkstra를 수행하여 최단거리를 저장하고 각 구간별로 거리의 합을 구해
대소비교를 통해 최단거리를 알아냈다.

마지막으로 노드끼리 연결되어있지 않아 탐색이 불가능한 경우 -1로 예외 처리를 해줘야한다.

추가1
다른사람의 코드와 비교해봤을 때, 다른코들은 전역에 dist배열을 선언하여 계속해서 업데이트를 해줬다. 나는 다익스트라 함수안에 dist배열을 선언하여
start,end노드끼리의 최단거리를 구하고 나중에 합하는 방법으로 진행했다.

#define _CRT_SECURE_NO_WARNINGS // scanf에러 방지
#include <iostream>
#include <vector>
#include <limits.h>
#include <queue>

#define INF INT_MAX // 최대값
using namespace std;

using pii = pair<int, int>;
vector<pii> board[801]; // 인접그래프

int n, e; // n 노드의 개수, e 간선의 개수
int node1, node2; //반드시 지나야할 노드들
int dijkstra(int start, int end)
{
    priority_queue<pii, vector<pii>, greater<pii>> pq;
    int dist_temp[801];
    for (int i = 0; i <= n; i++) dist_temp[i] = INF;
    dist_temp[start] = 0;

    pq.push({ 0,start });

    while (!pq.empty())
    {
        int node = pq.top().second;
        int node_cost = pq.top().first;
        if (node == end)// 만약 노드가 end까지 최단 거리를 구했으면 최단거리를 반환한다.
            return dist_temp[node];
        pq.pop();

        for (int i = 0; i < board[node].size(); i++)
        {
            int next = board[node][i].second;
            int next_cost = board[node][i].first;

            if (dist_temp[next] > next_cost + node_cost)
            {
                dist_temp[next] = next_cost + node_cost;
                pq.push({ dist_temp[next],next });
            }
        }

    }
    return INF;
}
int main()
{
    scanf("%d %d", &n, &e);
    for (int i = 0; i <= e; i++) {
        if (i == e)
            scanf("%d %d", &node1, &node2);
        else {
            int from, to, cost;
            scanf("%d %d %d", &from, &to, &cost);
            board[from].push_back({ cost,to });
            board[to].push_back({ cost,from });
        }
    }

    int onetoA = dijkstra(1, node1);
    int onetoB = dijkstra(1, node2);
    int AtoB = dijkstra(node1, node2);
    int BtoN = dijkstra(node2, n);
    int AtoN = dijkstra(node1, n);
    int error = -1;
    if (onetoA == INF || onetoB == INF || AtoB == INF || BtoN == INF
        || AtoN == INF) {
        printf("%d", error);
        return 0;
    }
    int sumA = onetoA + AtoB + BtoN;
    int sumB = onetoB + AtoB + AtoN;
    sumA > sumB ? printf("%d", sumB) : printf("%d", sumA);
}
```

```C++
2021/07/02
1261번 dijkstra
알고스팟 골드4

0과1로 이뤄진 2차원 배열이 있을 때
0,0에서 입력으로 주어진 n,m까지 갈때
0은 빈벽, 1은 벽이 있다고 가정한다.
n,m으로 갈 때 벽을 뚫고가야하는 최소한의 벽의 수를 구하라.

다익스트라는 노드 간선 문제에서한 사용한다고 생각했었다. 이런 map형식의 문제에서도
적용되는 것을 깨달았다.

수 차례 시도에도 무엇이 문제인지 인식하지 못했다.
디버깅을 통해 n,m이 x,y가 아닌 y,x으로 주어진 것을 알고 문제를 해결했다.
문제를 잘 읽자!!

#include <iostream>
#include <vector>
#include <queue>
#include <string>
#include <limits.h>
#define INF INT_MAX
using namespace std;
using pii = pair<int,pair<int,int>>;

int dx[4] = { 1,-1,0,0 };//아래,위,우,좌
int dy[4] = { 0,0,1,-1 };
int road[102][102];
int dist[102][102];
int n, m;
void bfs()
{
    priority_queue<pii, vector<pii>, greater<pii>> q;
    q.push({ 0,{ 0,0 } });
    dist[0][0] = 0;
    while (!q.empty())
    {   
        int x = q.top().second.first;
        int y = q.top().second.second;
        int d = q.top().first;
          
        q.pop();
        if (x == n - 1 && y == m - 1) break;
        if (d > dist[x][y])continue;
        
        for (int i = 0; i < 4; i++)
        {
            int nx = x + dx[i];
            int ny = y + dy[i];
            if (nx < 0 || ny < 0 || nx >= n || ny >= m)
                continue;

            if (dist[nx][ny] > dist[x][y] + road[nx][ny])
            {
                dist[nx][ny] = dist[x][y] + road[nx][ny];
                q.push({ dist[nx][ny],{ nx, ny } });
            }
        }
    }
    printf("%d\n", dist[n - 1][m - 1]);
}
int main()
{
    ios_base::sync_with_stdio(false);
    cin.tie(NULL);
    cout.tie(NULL);

    cin >> m >> n;
    for (int i = 0; i < n; i++){
        string temp;
        cin >> temp;
        for (int j = 0; j < m; j++) {
            road[i][j] = temp[j] - '0';
            dist[i][j] = INF;
        }
    }
    bfs();
    
}

```

```C++
2021/07/01
1916번 dijkstra
최소비용 구하기 골드5

이전 문제가 시작점에서 전체 노드까지의 최단거리를 구했다면
이 문제는 one to one의 최단거리를 구하는 문제다.
역시 dijkstra를 이용했고 도착점의 해당하는 비용만 출력하는 것으로 문제를 풀었다.

#define _CRT_SECURE_NO_WARNINGS
#include <iostream>
#include <vector>
#include <queue>
#include <limits.h>
#define  INF INT_MAX
using namespace std;

using pii = pair<int, int>;
int n, m; //도시의 개수
vector<pii>road[100001];
int cost[1002];

void dijkstra(int start)
{
    priority_queue<pii, vector<pii>, greater<pii>> pq;
    pq.push({ 0,start });
    cost[start] = 0;

    while (!pq.empty())
    {
        int node = pq.top().second;
        int node_cost = pq.top().first;

        pq.pop();

        if (node_cost > cost[node])
            continue;
        for (int i = 0; i < road[node].size(); i++)
        {
            int next = road[node][i].second;
            int next_cost = road[node][i].first;

            if (next_cost + node_cost < cost[next])
            {
                cost[next] = next_cost + node_cost;
                pq.push({ cost[next],next });
            }
        }
    }
}
int main()
{
    cin >> n;
    cin >> m;
    for (int i = 0; i < m; i++)
    {
        int from, to, weight;
        scanf("%d %d %d", &from, &to, &weight);
        road[from].push_back({ weight,to });
    }
    for (int i = 1; i <= 1001; i++) cost[i] = INF;

    int start, to;
    cin >> start >> to;
    dijkstra(start);

    cout << cost[to];

}
```

```C++
2021/06/29
1753번 dijkstra
최단경로 골드5

방향그래프가 주어졌을 떄 시작점에서 다른 모든 정점으로 최단경로를 구하는 문제다.
v는 정점의 개수 e는 간선의 개수

전형적인 다익스트라 방식으로 풀었다.

#define _CRT_SECURE_NO_WARNINGS
#include <iostream>
#include <vector>
#include <queue>
#include <limits.h>

#define INF INT_MAX

using namespace std;
using pii = pair<int, int>;
int v, e;
vector<pii>road[300001];
int dist[20002];

void dijkstra(int start)
{
    priority_queue < pii, vector<pii>, greater<pii>> pq; // pair(가중치, 노드)의 우선순위큐
    pq.push({0,start}); // 시작점은 0이므로 0,시작점에서 시작
    dist[start] = 0;

    while (!pq.empty())
    {
        int node_to = pq.top().second; //node
        int node_w = pq.top().first;  // cost

        pq.pop();

        if (node_w > dist[node_to]) // node의 가중치가 여태 노드의 가중치보다 많으면 건더뛴다.
            continue;
        for (int i = 0; i < road[node_to].size(); i++)
        { //방향성 그래프임으로 node에 연결된 모든 노드들을 돈다. 
            int next = road[node_to][i].second; //node에 연결된 다음 노드
            int next_w = road[node_to][i].first; //다음 노드의 가중치

            if (next_w + node_w < dist[next])
            { //현재 노드의 가중치와 다음노드의 가중치를 더했을 때 다음 노드의 가중치보다 적으면
                dist[next] = next_w + node_w; //최단거리로 초기화한다.
                pq.push({ dist[next],next }); // 다음 노드의 가중치, 다음노드 형식으로 우선순위 큐에 푸쉬
            }
        }
    }

}
int main()
{
    int start;
    cin >> v >> e;
    cin >> start;
    for (int i = 0; i < e; i++)
    {
        int from, to, w;
        scanf("%d %d %d", &from, &to, &w);
        road[from].push_back({w,to}); // 우선순위 큐에 가중치를 기준으로 들어가기때문에 
        //가중치를 앞으로 넣는다.
    }
    for (int i = 1; i < 20002; i++) dist[i] = INF; //거리 초기화

    dijkstra(start);

    for (int i = 1; i <= v; i++)
    {
        if (dist[i] == INF)
            cout << "INF" << endl;
        else
            printf("%d\n", dist[i]);
    }
}
```

```C++
2021/06/17
18352번 최단거리
특정 거리의 도시 찾기 실버2
1번 부터 N번까지 도시와 M개의 엣지가 있다. 모든 도로의 거리는 1이다.
이때 X로부터 출발하여 최단 거리가 정확히 K인 모든 도시들의 번호를 출력한다.
도시개수N, 도로개수M, 거리 정보K, 출발도시X

dfs로 풀려고 했다. 1부터 갈 수 있는 모든 노드를 돌면서
그 값을 dis배열에 넣고 값을 비교하여 최단거리를 최신화하는 알고리즘으로 풀었다.
테스트 케이스는 다 맞았지만 메모리에서 초과됐다.
아마 인접행렬을 사용해서 그럴것 같다.
30만개의 N이 있다면
메모리는 N^2으로 -> 9GB가 된다.
다른 사람들은 다 BFS로 풀었다. 메모리 초과로 인해 아직 풀지 못했다.
리스트로 바꾸는 방법을 써봐야겠다.

2021/06/28
정말 많은 오류가 있었다. 메모리 초과, 시간초과, 컴파일에러 등 내 ide에선 잘 돌아가는데
백준 컴파일러는 정이없다.
결국  우선순위 큐와 다익스트라를 사용하여 풀었다.
알고리즘은 이전과 비슷하지만 부가적인 사항에서 차이가 났나보다

#include <iostream>
#include <algorithm>
#include <vector>
#include <queue>
#include <limits> // 정수 상수에 대한 제한
#define INF INT_MAX // 정수 상수에 대한 제한 int형식 변수의 최대값

using namespace std;

using pii = pair<int, int>;
int n, m, k, x;
//도시,도로,가중치,시작노드
vector <pii> road[300001];
int dist[300001];

void dijkstra(int start)
{
    priority_queue<pii, vector<pii>, greater<pii>>pq;
    pq.push({ 0,start });
    dist[start] = 0;

    while (!pq.empty())
    {
        int cur = pq.top().second;
        int cost = pq.top().first;
        pq.pop();
        if (cost > dist[cur])
            continue;
        for (int i = 0; i < road[cur].size(); i++)
        {
            int next = road[cur][i].second;
            int nextcost = road[cur][i].first;
            if (cost + nextcost < dist[next])
            {
                dist[next] = cost + nextcost;
                pq.push({ dist[next],next });
            }
        }
    }
}
int main()
{
    cin >> n >> m >> k >> x;
    for (int i = 1; i <= n; i++)dist[i] = INF;
    for (int i = 0; i < m; i++)
    {
        int u, v;
        cin >> u >> v;
        road[u].push_back({1,v});//make_pair를 이런식으로도 쓰네
    }
    dijkstra(x);
    int flag = 0;
    for (int i = 1; i <= n; i++){
        if (dist[i] == k){
            printf("%d\n",i);
            flag = 1;
        }
    }
    if (!flag)
        cout << -1 << '\n';
}

//////////2021/06/17코드///////
#define _CRT_SECURE_NO_WARNINGS
#include <iostream>
#include <vector>

using namespace std;

int N, M, K, X;
vector<int>m[300001];
int dis[300001];
void dfs(int x,int cnt)
{
    for (int i = 0; i < m[x].size(); i++)
    {
        dfs(m[x][i],cnt+1);
    }
    if (dis[x] > cnt)
    {
        dis[x] = cnt;
    }
}
int main()
{
// 도시개수N, 도로개수M, 거리 정보K, 출발도시X
    
    cin >> N >> M >> K >> X;
    for (int i = 0; i < M; i++)
    {
        int x, y;
        scanf("%d %d", &x, &y);
        m[x].push_back(y);
    }
    fill_n(dis, 300001, 999);
    dfs(X,0);
    int flag = 0;
    for (int i = 0; i < sizeof(dis) / 4; i++)
    {
        if (i > N)
            break;
        if (dis[i] == K)
        {
            printf("%d\n", i);
            flag++;
        }
    }
    if (!flag)
        cout << -1;
}
```

```C++
2021/06/01
4963번 dfs
섬의 개수 실버2
정사각형으로 이루어져 있는 섬과 바다가 지도에 주어지고 섬의 개수를 세는 프로그램을 작성한다.
섬은 좌우양옆 대각선을 이동할 수 있다.

상하좌우는
int dx[4] = { 0,0,1,-1};
int dy[4] = { 1,-1,0,0};
이렇게 했지만
대각선까지 고려해야함으로
int dx[8] = { 0,0,1,-1,1,-1,-1,1 };
int dy[8] = { 1,-1,0,0,1,-1,1,-1 };
방향을 더 추가하였다.

#include <iostream>
#include <vector>
#include <string.h>

using namespace std;
int v[50][50];
bool visit[50][50];
vector<int>answer;
int dx[8] = { 0,0,1,-1,1,-1,-1,1 };
int dy[8] = { 1,-1,0,0,1,-1,1,-1 };
int cnt = 0;
void dfs(int n, int m ,int x, int y)
{
    visit[x][y] = true;
    for (int i = 0; i < 8; i++)
    {
        int nx = dx[i] + x;
        int ny = dy[i] + y;
        if (nx < 0 || ny < 0 || nx >= n || ny >= m)
            continue;
        else
        {
            if(v[nx][ny] && visit[nx][ny]== false)
                dfs(n, m, nx, ny);
        }
    }
}
int main()
{
    while (1)
    {
        int n, m;
        cin >> n >> m;
        if (n == 0 && m == 0)
            break;
        else
        {
            memset(v, 0, sizeof(v));
            memset(visit, false, sizeof(visit));
            for (int i = 0; i < m; i++)
            {
                for (int j = 0; j < n; j++)
                {
                    int a;
                    cin >> a;
                    v[i][j] = a;
                }
            }
            for (int i = 0; i < m; i++)
            {
                for (int j = 0; j < n; j++)
                {
                    if (visit[i][j] == false && v[i][j])
                    {
                        dfs(m,n,i, j);
                        cnt++;
                       
                    }
                }
            }
            answer.push_back(cnt);
            cnt = 0;
        }
    }
    for (auto i : answer)
        cout << i << endl;
}
```

```C++
2021/05/29
11724번 dfs
연결 요소의 개수 실버2

무방향 그래프가 주어졌을떄
연결 요소의 개수를 구하는 문제이다
dfs의 가장 기본적인 유형이다.
방향성이면 v[x].push_back(y); 한쪽만 해도 되지만
무방향이면 
v[x].push_back(y);
v[y].push_back(x);
양쪽다 연결해주어야한다.

문제를 처음 제출했을 땐 메모리 초과가 떴다.
2차원 벡터를 1차원 배열 백터로 바꿔주었더니 맞았다.
vector<vector<int>> v; ---> vector<int>v[1001];

#include <iostream>
#include <vector>
#include <string>

using namespace std;
vector<int>v[1001];
//vector<vector<int>>v(1001);   둘다 됨
bool visit[1001];
int cnt= 0;
void dfs(int x)
{
    visit[x] = true;
    for (int i = 0; i < v[x].size(); i++)
    {
        if (visit[v[x][i]] == true)
            continue;
        else
            dfs(v[x][i]);
    }
}
int main()
{
    int n, m;
    cin >> n >> m;
    for (int i = 0; i < m; i++)
    {
        int x, y;
        cin >> x >> y;
        v[x].push_back(y);
        v[y].push_back(x);
    }
    for (int i = 1; i <= n; i++)
    {
        if (visit[i] == true)
            continue;
        else
        {
            dfs(i);
            cnt++;
        }
    }
    cout << cnt;
}
```

```C++
2021/05/28
17298번 스택
오큰수 골드4

스택을 사용하여 풀어야하는건 알았지만 어떻게 해야하는지 오래 고민했다.
그러다가 스택은 이용하지 않고 벡터에 pair형식으로 index와 값을 저장하여 값을 기준으로
오름차순 정렬하고 0번째 index부터 first와 second가 둘다 클때 그값을 입히는 방법으로 문제를
풀었다. 할 수있는 예외처리는 하였고 반례를 찾아보려 해도 없기에 맞을 줄 알았더니 틀렸다고 나왔다.
결국 답을 보고 풀었다. 스택을 이용하여 스택에 인덱스를 넣어 하나씩 값을 찾는 방법이였다.

#include <iostream>
#include <vector>
#include <stack>
using namespace std;
#pragma warning(disable : 4996)
int main()
{
    int n;
    scanf("%d", &n);
    vector<int>v;
    vector<int>answer(n,-1);
    stack<int>s;
    for (int i = 0; i < n; i++)
    {
        int a;
        scanf("%d", &a);
        v.push_back(a);
    }
    for (int i = 0; i < v.size(); i++)
    {
        while (!s.empty() && v[s.top()] < v[i])
        {
            answer[s.top()] = v[i];
            s.pop();
        }
        s.push(i);
    }
    for (auto i : answer)
        printf("%d ", i);
}

```

```C++
2021/05/25
1874번 스택
스택 수열 실버3

첫 줄에 n이 주어지고 아래부턴 수열이 주어진다.
1 부터 n까지 1씩 증가할때 스택을 이용하여 주어진 수열을 만드는 문제다.
과정에서 스택의 push는 +로, pop은 -로 표현한다.
만약 주어진 수열로 만들 수 없다면 NO를 출력한다.

이문제는 시간초과에서 걸렸다.
n이 100,000까지 주어지기 때문에 cout과 cin을 사용한것이 원인이였다.
scanf와 printf로 바꿔주니 원활하게 돌아갔다.
앞으로 scanf와 printf를 사용해야겠다.

#include <string>
#include <iostream>
#include <stack>
#include <vector>
#include <queue>
using namespace std;
int main()
{
    queue<int>q;
    stack<int>s;
    vector<char> p;
    int n;
    scanf("%d", &n);
    for (int i = 0; i < n; i++)
    {
        int a;
        scanf("%d", &a);
        q.push(a);
    } 
    int num = 1;
    bool flag = false;
    while (!q.empty())
    {
        if (s.size() == 0)
        {
            s.push(num);
            p.push_back('+');
            num++;
        }
        if (s.top() > q.front())
        {
            flag = true;
            break;
        }
        else if (s.top() == q.front())
        {
            s.pop();
            q.pop();
            p.push_back('-');
        }
        else
        {
            s.push(num);
            p.push_back('+');
            num++;
        }
    }
    if (flag)
        cout << "NO";
    else
    {
        for (auto i : p)
            printf("%c\n", i);
    }
}
```

```C++
2021/05/19
4949번 스택
균형잡힌 세상 실버4
괄호의 균형을 찾는 기본적인 문제이다. 하지만 이중if문을 사용했을 땐 틀리고
&&논리연산자를 사용했을 땐 정답이라고 나온다. 이부분이 이해가 안돼서 질문 올렸다.
#include <string>
#include <vector>
#include <algorithm>
#include <stack>
#include <iostream>

using namespace std;
int main()
{
	while (1){
		string tmp;
		getline(cin, tmp);
        if (tmp == ".")
			break;
        stack<char>s;
        for (int j = 0; j < tmp.size(); j++) {
            if (tmp[j] == '(' || tmp[j] == '[')
                s.push(tmp[j]);
            else if (tmp[j] == ')') {
                if (s.size() && s.top() == '(') {
                        s.pop();
                }
                else
                    s.push(')');
            }
            else if (tmp[j] == ']') {
                if (s.size() && s.top() == '[') {
                        s.pop();
                }
                else
                    s.push(']');
            }
        }
        if (!s.empty())
            cout << "no" << endl;
        else
            cout << "yes" << endl;
		cin.clear();
	}
}
```

```C++
2021/05/19
10773번 스택
제로 실버4

#include <stack>
#include <iostream>
#include <string>

using namespace std;

int main()
{
    stack<int>s;
    int n;
    cin >> n;
    int sum = 0;
    for (int i = 0; i < n; i++)
    {
        int a;
        cin >> a;
        if (a == 0)
        {
            s.pop();
        }
        else
        {
            s.push(a);
        }
    }
    while (!s.empty())
    {
        sum += s.top();
        s.pop();
    }
    cout << sum << endl;
}

```

```C++
2021/05/18
10828번 스택 실버4

stack의 기능을 구현한다.
getline(cin,str)을 사용하여 입력 받았다.

#include <iostream>
#include <stack>
#include <vector>
#include <string>
#include <sstream>
using namespace std;

int main()
{
    vector<int>v;
    int n;
    cin >> n;
    for (int i = 0; i <= n; i++)
    {
        string str;
        getline(cin, str);
        cin.clear();
        string string_tmp;
        string num_tmp;
        for (int j = 0; j < str.size(); j++)
        {
            if (isalpha(str[j]))
                string_tmp += str[j];
            else if (isdigit(str[j]))
                num_tmp += str[j];
        }
        int num = 0;
        if(num_tmp.size() != 0)
            num = stoi(num_tmp);
        if (string_tmp == "push")
        {
            v.push_back(num);
        }
        else if (string_tmp == "pop")
        {
            if (!v.size())
                cout << -1 << endl;
            else
            {
                cout << v.back() << endl;
                v.pop_back();
            }
        }
        else if (string_tmp == "size")
        {
            cout << v.size() << endl;
        }
        else if (string_tmp == "empty")
        {
            if (v.empty())
                cout << 1 << endl;
            else
                cout << 0 << endl;
        }
        else if (string_tmp == "top")
        {
            if (v.size()==0)
                cout << -1 << endl;
            else
                cout << v.back() << endl;
        }
    }
}
```
```C++
2021/05/18
13305번 그리디/greedy
주유소 실버4

이 문제는 자동차가 각 도시를 이동할 떄마다 더 적은 값의 기름을
채워 최소비용을 계산하는 문제이다.
맨처음엔 차에 기름이 없다는 가정이라 무조건 기름을 채워 출발해야한다.
만약 그 다음 도시의 기름값이 이전보다 더 비싸면 이전도시에서 거리만큼 기름을 채워간다.
input이 10억까지 들어갈 수 있기에 long long 데이터 타입을 사용헀다.

#include <iostream>
#include <vector>
#include <string>

using namespace std;

int main()
{
    int n;
    cin >> n;
    vector<long long> dis;
    vector<long long> pay;
    for (int i = 0; i < n-1; i++)
    {
        long long tmp;
        cin >> tmp;
        dis.push_back(tmp);
    }
    for (int i = 0; i < n; i++)
    {
        long long tmp;
        cin >> tmp;
        pay.push_back(tmp);
    }
    long long now_pay = pay[0];
    long long sum = pay[0] * dis[0];
    for (int i = 1; i < pay.size()-1; i++)
    {
        if (pay[i] > now_pay)
        {
            sum += now_pay * dis[i];
        }
        else
        {
            sum += pay[i] * dis[i];
            now_pay = pay[i];
        }
    }
    cout << sum;
}

```

```C++
2021/05/16
1541번 그리디/greedy
잃어버린 괄호 실버2
#include <iostream>
#include <string>
using namespace std;
string str;
int minResult(void)
{
    int result = 0;
    string temp = "";
    bool minus = false;
    for (int i = 0; i <= str.size(); i++)
    {
        //연산자일 경우
        if (str[i] == '+' || str[i] == '-' || str[i] == '\0')
        {
            if (minus)
                result -= stoi(temp);
            else
                result += stoi(temp);
            temp = ""; //초기화
            //괄호를 뺄셈 이후에 치면 최소
            if (str[i] == '-')
                minus = true;
            continue;
        }
        //피연산자일 경우
        temp += str[i];
    }
    return result;
}
int main(void)
{
    cin >> str;
    cout << minResult() << endl;
    return 0;
}

```
```C++
2021/05/14
11399번 그리디/greedy
ATM 실버3

#include <iostream>
#include <vector>
#include <algorithm>

using namespace std;

int main()
{
    int n;
    cin >> n;
    vector<int>arr;
    for (int i = 0; i < n; i++)
    {
        int t;
        cin >> t;
        arr.push_back(t);
    }
    sort(arr.begin(), arr.end());
    int cnt_sum = 0;
    for (int i =0; i< n; i++)
    {
        int sum = 0;
        for (int j = i; j >= 0; j--)
        {
            sum += arr[j];
        }
        cnt_sum += sum;
    }
    cout << cnt_sum;
    
}
```

```C++
2021/05/14
1931번 그리디/greedy
회의실 배정 실버 2

회의실 한개가 있을 때 사용하고자하는 N개의 회의에 대하여 사용표를 만들려고할때,
각 회의에 대해 시작,끝시간이 주어지고 겹치지 않고 회의하여 최대 몇개의 회의를 할 수 있는지
찾는 문제이다.

처음엔 dfs로 풀어보려 했지만 시간초과 및 메모리초과가 일어났다. 결국 끝나는 시간을 기준으로 오름차순으로 정렬하여 제일 일찍 끝나는 회의를 현재로 잡고 시작하는 시간이 가장 가까운 회의를 다음으로 하는 방식으로 문제를 풀었다.

#include <iostream>
#include <vector>
#include <algorithm>
#include <string>

using namespace std;

bool compare(pair<int, int> a, pair<int, int> b)
{
    if (a.second == b.second)
        return a.first < b.first;
    else
        return a.second < b.second;
}
int main()
{
    vector<pair<int, int>> v;
    int n;
    cin >> n;
   
    for (int i = 0; i < n; i++)
    {
        int a, b;
        cin >> a >> b;
        v.push_back(make_pair(a, b));
    }
    sort(v.begin(), v.end(),compare);
    int cnt = 1;
    int now = v[0].second;
    for (int i = 1; i < n; i++)
    {
        if (now <= v[i].first)
        {
            cnt++;
            now = v[i].second;
        }
    }
    cout << cnt;
}
```

```C++
2021/05/12
11047번 그리디/greedy
동전 0 실버2

#define _CRT_SECURE_NO_WARNINSG

#include <iostream>
#include <string.h>
#include <algorithm>
#include <vector>
#include <string>
using namespace std;

int main()
{
    int arr[10];
    int n, k, cnt = 0;;
    cin >> n >> k;
    for (int i = 0; i < 10; i++)
        cin >> arr[i];
    for (int j = n - 1; j >= 0; j--)
    {
        if (k / arr[j] >= 1)
        {
            cnt += k / arr[j];
            k -= ((k / arr[j]) * arr[j]);
        }
    }
    cout << cnt;
}
```

```C++
2021/05/12
2447번 재귀
별찍기 실버1

#define _CRT_SECURE_NO_WARNINSG

#include <iostream>
#include <string.h>
#include <algorithm>
#include <vector>
#include <string>
using namespace std;

void star(int i, int j, int num)
{
    if ((i / num) % 3 == 1 && (j / num) % 3 == 1) {
        cout << ' ';
    }
    else
    {
        if (num / 3 == 0)
            cout << '*';
        else
            star(i, j, num / 3);
    }
}
int main() {
    int num;
    cin >> num;
    for (int i = 0; i < num; i++)
    {
        for (int j = 0; j < num; j++)
            star(i, j, num);
        cout << '\n';
    }
}
```

```C++
2021/05/11
2941번
크로아티아 알파벳 실버5

하나의 문자열을 문장 끝날때까지 돌려야하는 방법을 찾다가 다음과 같은 방법을 이용했다.
문자를 찾게 된다면 그때마다 다른 표시로 바꿔주면 결국엔 찾을 수 없을 때까지 while문을 도는
방법이다. 만약 지우게 된다면 지우는 문자 앞뒤가 합쳐져 또 크로아티아 문자가 될 수도 있기 때문에
erase는 쓸 수 없었다.

#define _CRT_SECURE_NO_WARNINSG

#include <iostream>
#include <string.h>
#include <algorithm>
#include <vector>
#include <string>
using namespace std;

int main()
{
    vector<string>change = { "c=","c-","dz=","d-","lj","nj","s=","z=" };
    string str;
    cin >> str;
    int cnt = 0;
    string tmp = str;
    for (int i = 0; i < change.size(); i++)
    {
        while (1)
        {//못찾을때까지도는데 찾을때마다 %로 바꿔주니까 없을 떄까지도는거지
            auto it = str.find(change[i]);
            if ((int)it == -1)
                break;
            else
                str.replace(it, change[i].length(), "%");
        }
    }
    cout << str.size();
}
```

```C++
2021/05/11
1065번
한수 실버4

#define _CRT_SECURE_NO_WARNINSG
#include <iostream>
#include <string.h>
#include <algorithm>
#include <vector>
#include <string>
using namespace std;

int main()
{
    int n;
    cin >> n;
    if (n < 100)
    {
        cout << n;
        return 0;
    }
    else
    {   //n>=100
        int cnt = 99;
        for (int i = 100; i <= n ; i++)
        {     
            string tmp = to_string(i);
            int cha1to2 = (tmp[1]-'0')-(tmp[0]-'0');
           // int cha2to3 = (tmp[1] - '0') - (tmp[2] - '0');
            if (cha1to2 + (tmp[1]-'0') == (tmp[2]-'0'))
                cnt++;
        }
        cout << cnt;
    }
}
```
```C++
2021/05/11
4673번
셀프 넘버 실버5

#define _CRT_SECURE_NO_WARNINSG
#include <iostream>
#include <string.h>
#include <algorithm>
#include <vector>
#include <string>
using namespace std;
#define MAX 10000
int arr[MAX];
int main()
{
    for (int i = 0; i < MAX; i++)
    {
        string tmp = to_string(i);
        int sum = i;
        for (int j = 0; j < tmp.size(); j++)
        {
            sum += tmp[j] - '0';
        }
        arr[sum] = 1;
    }
    for (int i = 0; i < MAX; i++)
    {
        if (arr[i] == 0)
            printf("%d\n", i);
    }
}
```

```C++
2021/05/07
1316번 문자열
그룹 단어 체커 실버5

문자열에 대해서 각 문자가 연속해서 나타나는 경우가 그룹단어라고 지칭한다.
ccazzzzbb는 모두 연속해서 나타내기때문에 그룹이지만
aabbca는 a가 떨어져 나타나서 그룹단어가 아니다.
그룹단어의 개수를 출력하는 프로그램을 작성한다.

먼저 단어의 개수와 단어를 벡터에 넣었다.
반복문을 돌며 check에 find를 사용하여 중복체크를 하고 없으면 넣어준다.
연속된 문자를 탐지하기 위해 char변수로 그전의 문자를 받아온다.
현재 문자가 check에 문자가 있지만 char변수와 같으면 연속된 문자기때문에 check에 넣어준다.
아닌경우는 그룹단어가 아니기에 n에서 -1를하고 break;로 단어 탐색을 즉시 종료해준다.

#include <iostream>
#include <string>
#include <vector>

using namespace std;

int main()
{ 
    int n;
    cin >> n;
    vector<string>arr;
    for (int i = 0; i < n; i++)
    {
        string tmp;
        cin >> tmp;
        arr.push_back(tmp);
    }
    for (int i = 0; i < arr.size(); i++)
    {
        string check; //검사가 완료된 문자
        char cha = arr[i][0];  //바로전의 문자를 담는다. 연속된 문자 체크
        for (int j = 0; j < arr[i].size(); j++)
        {
            auto it = check.find(arr[i][j]); //검사된 문자중에 중복여부를 찾는다.
            if ((int)it == -1)
            { // 없으면 
                check += arr[i][j]; // check에 넣어준다.
                cha = arr[i][j]; // 이전의 문자로 바꿔준다.
            }
            else if (cha == arr[i][j]) //check에 문자가 있지만 이전의 문자와 같으면
                check += arr[i][j]; //연속돈 문자로 치부하고 넣어준다.
            else
            { //check에 문자가 있고 이전의 문자와 같지 않으면 떨어진 중복 문자기때문에 그룹문자가아니다.
                n -= 1; // 그룹문자에서 차감하고
                break; // 탈출한다.
            }
        }
    }
    cout << n;
}
```

```C++
2021/05/07
11719번 문자열
그대로출력하기2 브로즈2

#include <iostream>
#include <string>
#include <vector>

using namespace std;
int main()
{
    vector<string>tmp;
    for (int i = 0; i < 100; i++)
    {
        string a;
        getline(cin, a);
        tmp.push_back(a);
    }
    for (auto i : tmp)
        cout << i << endl;
}
```
```C++
2021/05/05
1157번 문자열
단어 공부

#include <iostream>
#include <string>
#include <algorithm>
#include <vector>
using namespace std;
int main()
{
    vector<pair<int, char>> v(26);
    string a;
    cin >> a;
    sort(a.begin(), a.end());
    for (int i = 0; i < a.size(); i++)
        a[i] = tolower(a[i]);
    for (int i = 0; i < a.size(); i++)
    {
        v[a[i] - 'a'].first++;
        v[a[i] - 'a'].second = a[i];
    }
    
    sort(v.begin(), v.end());
    char tmp = toupper(v[v.size() - 1].second);
    if (v[25].first == v[24].first)
        cout << "?";
    else
        cout << tmp;
}
```

```C++
2021/05/04
1152번 문자열
단어의 개수 브론즈2

#include <iostream>
#include <string>
#include <sstream>
using namespace std;

int main()
{
    string tmp;
    getline(cin, tmp);
    stringstream str(tmp);
    string str_cut;
    int count = 0;
    while (str >> str_cut)
        count++;
    cout << count;
}
```

```C++
2021/05/02
11399번 greedy
ATM 실버3

#include <iostream>
#include <vector>
#include <string>
#include <algorithm>
using namespace std;

int main()
{
    int n;
    cin >> n;
    int tmp[1001];
    vector<int> arr;
    for (int i = 0; i < n; i++)
        cin >> tmp[i];//3 1 4 3 2 <--이런식으로 받을때 배열에 바로 넣어도됨
    sort(tmp,tmp+n);//<-- 배열로 쓸땐 이렇게함, (시작,끝)
    int answer = 0;
    for(int i =0; i< n; i++)
    {
        for (int j = 0; j <= i; j++)
            answer += tmp[j];      
    }
    cout << answer;
}
```

```C++
2021/05/02
8958번 문자열
OX퀴즈 브론즈2

#include <iostream>
#include <string>
#include <vector>

using namespace std;

int main()
{
    vector<string> arr;
    int n;
    cin >> n;
    for (int i = 0; i < n; i++)
    {
        string tmp;
        cin >> tmp;
        arr.push_back(tmp);
    }
    vector<int> answer(arr.size());
    for (int i = 0; i < arr.size(); i++)
    {
        int sum = 0;
        for (int j = 0; j < arr[i].size(); j++)
        {
            if (arr[i][j] == 'O')
            {
                sum++;
                answer[i] += sum;
            }
            else
                sum = 0;
        }
    }
    for (auto i : answer)
        cout << i << endl;
}
```

```C++
2021/04/30
9012번 문자열
괄호 실버4

#include <iostream>
#include <string>
#include <vector>
using namespace std;

string check(string str)
{
    int cnt = 0;
    for (int i = 0; i < str.size(); i++)
    {
        if (str[i] == '(')
            cnt++;
        else if (str[i] == ')')
            cnt--;
        if (cnt < 0)
            return "NO";
    }
    return cnt == 0 ? "YES" : "NO";
}
int main()
{
    int n;
    cin >> n;
    vector<string> str;
    
    for (int i = 0; i < n; i++)
    {
        string tmp;
        cin >> tmp;
        str.push_back(tmp);
    }
    for (int i = 0; i < n; i++)
    {
        str[i] = check(str[i]);
    }
    for (auto i : str)
        cout << i << endl;
}
```

```C++
2021/04/30
11720번 문자열
숫자의 합 브론즈2

#include <iostream>
#include <string>

using namespace std;

int main()
{
    int n;
    cin >> n;
    string str;
    cin >> str;
    int sum = 0;
    for (int i = 0; i < str.size(); i++)
        sum += str[i] - '0';
    cout << sum;
}
```

```C++
2021/04/29
2577번 문자열
숫자의 개수 브론즈2

#include <iostream>
#include <string>

using namespace std;

int main()
{
    int A, B, C;
    cin >> A;
    cin >> B;
    cin >> C;
    string num = to_string(A * B * C);
    int arr[10] = { 0, };
    for (int i = 0; i < 10; i++)
    {
        for (int j = 0; j < num.size(); j++)
        {
            if (num[j] - '0' == i)
                arr[i]++;
        }
    }
    for (int i = 0; i < 10; i++)
        cout << arr[i] << endl;
}
```

```C++
2021/04/29
2438번 문자열
별찍기 -1 브론즈3

#include <iostream>
using namespace std;
int main()
{
    int n;
    cin >> n;
    for (int i = 0; i < n; i++)
    {
        for (int j = 0; j <= i; j++)
        {
            printf("*");
        }
        printf("\n");
    }
}
```

```C++
2021/04/29
1463번 dp
1로 만들기 실버3 

정수 x에 사용할 수 있는 연산은 3가지다
1. x가 3으로 나누어 떨어지면 3으로 나눈다.
2. x가 2로 나누어떨어지면 2로 나눈다.
3. 1을 뺀다.
위 3가지 방법을 적절히 이용하여 1를 만들려고 할때, 연산을 사용하는 최솟값을 출력한다.

이 문제는 처음엔 점화식을 세워 풀어보려고했다.
1. 3혹은 2로 나누어떨어질때 나뉜 값에서  3혹은 2로 나누어떨어지는지 확인하여
나뉜다면 3혹은2로 나눈다. 나뉘지 않는다면 1를 뺸다.
2. 1번이 해당되지 않으면 -1을 뺀다.

이런식으로 1을 만들때 테스트케이스는 맞았다. 하지만 정답은 틀렸다고 나왔다.
오랬동안 규칙을 찾아 모든 경우를 압축시켰지만 정답을 맞추지 못했다.

모든 경우를 찾는 bfs를 이용하여 풀었다. 큐에 (x의 값, 연산의 수)를 담아 1이 된다면
반복문을 탈출하게 설계했다. 여기서 visit을 함으로 이미 진행한 연산을 체크함으로 더 빠른속도로
값을 찾을 수 있다.

#include <iostream>
#include <queue>
using namespace std;
bool visit[1000001];
int main()
{
	queue<pair<int, int>> q;
	int n, f, s;
	cin >> n;
	q.push(make_pair(n, 0));
	visit[n] = true;

	while (1)
	{
		f = q.front().first;
		s = q.front().second;
		q.pop();
		if (f == 1)
			break;

		if (f % 3 == 0 && !visit[f / 3])
			q.push(make_pair(f / 3, s + 1));
		if (f % 2 == 0 && !visit[f / 2])
			q.push(make_pair(f / 2, s + 1));
		if (f > 1 && !visit[f - 1])
			q.push(make_pair(f - 1, s + 1));
		visit[f] = true;
	}
	cout << s;
}


```

```C++
2021/04/28
2839번 dp/greedy
설탕 배달 브론즈1

5kg,3kg짜리 포대가 있을 때 Nkg의 설탕을 입력받아
설탕을 담을 수 있는 최소 포대 개수를 반환하는 문제이다.
모든 경우의 수를 도식화하여 풀었다.
모든 경우의 수는 다음과 같다.
n을 5로 나누면 나머지는 무조건 0,1,2,3,4 중에 하나가된다.
0일경우 --> 그대로 반환한다.
3일 경우 --> 3으로 나눈 값을 5로 나눈 값과 더하여 반환한다.
1,2,4일경우 --> 3으로 나누어도 나머지가 있기 때문에 n을 5로 나눈 값에서 한 포대를 풀어 나머지에 5를 더해준다.
그러면 6,7,9가 되는데 이 경우 3으로 다시 나누어 나누어 떨어지는 값이 생기면 반환한다.
이 과정을 n을 5로 나눈 값이 0아래로 내려가기 전까지 반복하여 값을 구한다.
만약 0아래로 내려가면 n은 담을 수 없다고 판단하여 -1를 반환한다.

1. 5/n을 했을 때 나머지가 0이면 그대로 반환한다.
2. 나머지가 있으면 3으로 나눈다. 나머지가 0이면 1번과 2번의 개수를 더하여 반환한다.
3. 나머지가 있으면 반복문을 돌면서 5/n에서 포대를 하나씩 뺴면서 나머지에서 5를 더해주며 3으로 나눠본다.
4. 3으로 나눠지는 구간이 있으면 그 개수를 더하여 반환한다.
5. 만약 5/n이 0아래로 내려가게 되면 입력받은 n은 담을 수 없다고 판단하여 -1를 반환한다.
 
#include <iostream>
#include <string>
#include <vector>

using namespace std;
int n, n_tmp, tmp, last;
int dp()
{
    if (n / 5 > 0 && n % 5 == 0)
        return n / 5;
    n_tmp = n;
    tmp = n_tmp / 5;
    last = n_tmp % 5;
    while (tmp >= 0)
    {
        if (last % 3 == 0)
            return tmp + last / 3;
        tmp--;
        last += 5;
    }
    return -1;
}
int main()
{
    cin >> n;
    cout << dp();
}
```

```C++
2021/04/25
2178번 bfs
미로 탐색 실버1

NxM 크기의 배열에 1이면 이동 가능 0 이면 이동 불가로 인식을 한다.
이때 0,0에서 n-1,m-1로 갈수 있는 최단 경우의 수를 반환하는 문제이다.


#include <iostream>
#include <string>
#include <vector>
#include <queue>
using namespace std;

int map[101][101];
bool visit[101][101];
int dx[4] = { 1,-1,0,0 };
int dy[4] = { 0,0,1,-1 };
int N, M;

int bfs(int x,int y, int cnt)
{
    queue<pair<pair<int,int>,int>>q;
    q.push(make_pair(make_pair(x, y), cnt));
    visit[x][y] = true;
    while (!q.empty())
    {
        int x_tmp = q.front().first.first;
        int y_tmp = q.front().first.second;
        int cnt_tmp = q.front().second;
        q.pop();
        if (x_tmp == N - 1 && y_tmp == M - 1)
            return cnt_tmp;
        
        for (int i = 0; i < 4; i++)
        {
            int nx = dx[i] + x_tmp;
            int ny = dy[i] + y_tmp;
            if (nx < 0 || nx >= N || ny < 0 || ny >= M)
                continue;
            if (map[nx][ny] && !visit[nx][ny])
            {
                q.push(make_pair(make_pair(nx, ny), cnt_tmp + 1));
                visit[nx][ny] = true;
            }
                
        }
    }
}

int main()
{
    cin >> N >> M;
    for (int i = 0; i < N; i++)
    {
        string tmp;
        cin >> tmp;
        for (int j = 0; j < M; j++)
        {
            map[i][j] = tmp[j] - '0';
        }
    }
    cout <<bfs(0,0,1);
}
```

```C++
2021/04/23
1260번 dfs/bfs
DFS와 BFS 실버2

그래프를 DFS와 BFS로 방문하여 방문 순서대로 출력하는 프로그램이다.
처음에 그래프로 안하고 노드로 직접 연결시켜서 했지만
방문하는 순서는 여러가지이기 때문에 순서가 달라 틀렸다.
결국 bfs같은 건 sort로 오름차순하여 돌리면 되지만
애초에 그래프로 푸는게 맞는것 같다.
코드 다 엎고 그래프로 다시 풀었다.

#include <iostream>
#include <vector>
#include <string>
#include <algorithm>
#include <string.h>
#include <queue>
using namespace std;
int arr[1001][1001];
bool visit[1001];
int N, M, V;

void dfs(int n)
{
	
    cout << n << " ";
	for (int j = 1; j <= N; j++)
	{
        if (!visit[j] && arr[n][j])
        {
            visit[j] = true;
            dfs(j);
        }
	}
}
void bfs(int n)
{

	queue<int> q;
	q.push(n);
	visit[n] = true;

	while (!q.empty())
	{
		n = q.front();
		q.pop();
        
        cout << n << " ";
		for (int i = 1; i <=N; i++)
		{
			if (!visit[i] && arr[n][i])
			{
				visit[i] = true;
				q.push(i);
                
			}
		}
	}
}
int main()
{

	// N은 정점의 개수
	// M은 간선의 개수
	// V은 탬색 시작 번호
	cin >> N >> M >> V;
	for (int i = 0; i < M; i++)
	{
		int x, y;
		cin >> x >> y;
        arr[x][y] = 1;
        arr[y][x] = 1;
	}
    visit[V] = 1;
	dfs(V);
    cout << endl;

	memset(visit, false, sizeof(visit));
	bfs(V);
    cout << endl;
}

```

```C++
2021/04/22
2178번 bfs
미로 탐색 실버1

n X m 크기의 배열로 표현되는 미로가 있다.

101111
101010
101011
111011

1은 이동할 수 있는 칸이고 0은 이동할 수 없는 칸이다.
이때 0,0에서 출발하여 n-1,m-1의 위치로 이동할 때 지나는 최소의 칸 수를 구하는 문제이다.

처음엔 dfs로 풀어보려고 했지만, visit을 계속 초기화해줘야하는 문제와
깊이로 탐색하기 때문에 모든 경우의 수를 구하느라 시간 복잡도에서 걸리는 문제가 있었다.
queue를 이용하여 넓이 우선 탐색으로 문제를 해결했다.

dfs는 한방향으로 쭉 탐색한다면, bfs는 한곳부터 여러방향으로 탐색하여 값을 찾는다.

#include <iostream>
#include <vector>
#include <string>
#include <algorithm>
#include <queue>
using namespace std;
int map[100][100];
bool visit[100][100];
vector<int> answer;

int dx[4] = { 1,-1,0,0 };
int dy[4] = { 0,0,1,-1 };
int n, m;

void bfs(int x, int y, int cnt)
{
    queue<pair<pair<int, int>, int>> que;
    que.push(make_pair(make_pair(x, y),cnt)); //큐를 만들어준다.(x,y),cnt)형태의 큐이다.

    while (!que.empty())
    { // 큐에 데이터가 존재하지 않을때까지 돈다.
        x = que.front().first.first; 
        y = que.front().first.second;
        cnt = que.front().second;
        que.pop();//값을 가져오면 맨 처음에 들어온 값을 pop으로 날려준다.

        if (x == n - 1 && y == m - 1)
        {//break조건이다. 큐에 값이 남아있더라도 정답을 찾으면 반환한다.
            answer.push_back(cnt);
            return;
        }
        for (int i = 0; i < 4; i++)
        {
            int nx = dx[i] + x;  // 4방향으로 탐색하여
            int ny = dy[i] + y;

            if (nx < 0 || nx >= n || ny < 0 || ny >= m) // 갈수없는 곳이면 패스
                continue;
            if (map[nx][ny] && !visit[nx][ny])
            {//map의 값이 1이고 , 방문하지 않은 곳이라면
                visit[nx][ny] = true; // 방문했다고 체크하고
                que.push(make_pair(make_pair(nx, ny), cnt + 1)); // 방문하지 않은 곳을 큐에 넣어준다.
            }
        }
    }
}

int main()
{

    cin >> n >> m;
    for (int i = 0; i < n; i++)
    {
        string tmp;
        cin >> tmp;
        for (int j = 0; j < m; j++)
        {
            map[i][j] = tmp[j] - '0';
        }
    }
    visit[0][0] = true; // 0,0은 방문했다고 한다.
    bfs(0,0,1); //시작점 0,0과 카운트 1
    if (answer.size() == 0)// 이건 dfs에서 사용할떄 모든 경우의 수를 구해 가장 짧은 경우를 구할때 쓰는것인데 bfs는 가장 짧은 경로를 만나자마자 반환하기 때문에 사실 필요없다. 
        cout << 0;
    else
    {
        sort(answer.begin(), answer.end());
        cout << answer[0];
    }
}
```

```C++
2021/04/22
1012번 dfs
유기농 배추 실버2
맵에서 상하좌우가 1로 인접할때 마다 벌레를 구입한다고 할때
구입해야하는 벌레 수를 구하는 문제이다.

얼마 전에 풀었던 1,-1,0,0 / 0,0,1,-1을 이용하여 수월하게 풀었다.
메인 함수에서 숫자를 받아오는게 조금 번거로웠던 문제였다.

#include <iostream>
#include <string>
#include <vector>
#include <algorithm>
using namespace std;

int bug_cnt;
int arr[50][50];
bool visit[50][50];
int dx[4] = { 1,-1,0,0 };
int dy[4] = { 0,0,1,-1 };
vector <int> answer;
void dfs(int x, int y, int row, int col)
{
    visit[x][y] = true;
    for (int i = 0; i < 4; i++)
    {
        int nx = dx[i] + x;
        int ny = dy[i] + y;
        if (nx < 0 || nx >= row || ny < 0 || ny >= col)
            continue;
        if (arr[nx][ny] && !visit[nx][ny])
            dfs(nx, ny, row, col);
    }
}
int main()
{
    int test_case;
    cin >> test_case;
    for (int i = 0; i < test_case; i++)
    {
        bug_cnt = 0;
        int row, col, one_cnt;
        cin >> row >> col >> one_cnt;
        memset(arr, 0, sizeof(arr));  //arr배열을 0으로 초기화한다. #include <string.h>가 필요하다.
        memset(visit, false, sizeof(visit)); //visit배열을 false으로 초기화한다. #include <string.h>가 필요하다.
        for (int j = 0; j < one_cnt; j++)
        {
            int x, y;
            cin >> x >> y;
            arr[x][y] = 1;
        }
        
        for (int j = 0; j < row; j++)
        {
            for (int z = 0; z < col; z++)
            {
                if (arr[j][z] == 1 && !visit[j][z])
                {// 만약 arr에 배추가 심어져있고, 방문하지 않았다면
                    bug_cnt++;
                    dfs(j, z,row,col);
                    
                }
            }
        }
        answer.push_back(bug_cnt);
    }
    for (int i : answer)
        cout << i << endl;
}


```

```C++
2021/04/22
2606번 dfs
바이러스 실버3

컴퓨터가 연결되어있다는 배열을 주었을 때
1번컴퓨터가 바이러스에 걸렸을 떄 연달아 걸리게 된 컴퓨터의 개수를 구하는 문제이다.

첫 줄에는 컴퓨터의 수, 컴퓨터의 수는 100이하이다. 각 컴퓨터에는 1번 부터 번호가 있다.
둘째 줄에는 네트워크 상에서 직접 연결되어있는 컴퓨터 쌍의 수가 주어진다.
이어서 한 줄에 한 쌍씩 네트워크 상에서 직접 연결되어있는 컴퓨터의 번호 쌍이 주어진다.

#include <iostream>
#include <string>
#include <vector>
#include <algorithm>
using namespace std;

int n;
int virus_cnt;
vector<int> arr[101];
bool visit[100];
int cnt;
void dfs(int N)
{
    visit[N] = true; //방문
    for (int i = 0; i <arr[N].size() ; i++)
    {//각 컴퓨터와 연결된 컴퓨터 전부 다 돈다.
        int y = arr[N][i]; 
        if (!visit[y]) // 만약 연결된 컴퓨터가 방문을 하지 않았으면
        {
            dfs(y); //dfs를 돈다.
            cnt++;
        }
      
    }
}
int main()
{

    cin >> n;
    cin >> virus_cnt;
    for (int i = 0; i < virus_cnt; i++)
    {
        int x, y;
        cin >> x >> y;
        arr[x].push_back(y);//데이터를 삽입 할 때 쌍으로 하는 것이 아니고 x번 컴퓨터와 연결된 컴퓨터를 넣는다.
        arr[y].push_back(x);//반대로 y번 컴퓨터와 연결된 컴퓨터를 넣어서 dfs를 돌린다.
    }
    dfs(1); //1번 돌아갈 때
    cout << cnt;
}
```

```C++
2667번 dfs
단지 번호 붙이기
7
0110100
0110101
1110101
0000111
0100000
0111110
0111000

0은 집이 없고 1은 집이 있다고 가정할 때
1이 이어진 군단을 찾아
군단의 개수와 각 군단의 집의 개수를 출력한다. 단 오름차순으로 정렬한다.
#include <iostream>
#include <string>
#include <vector>
#include <algorithm>
using namespace std;
int n;
int arr[25][25];
bool visit[25][25];
vector<int> answer;
int cnt;
int dx[4] = { 1,-1,0,0 };// 위 아래
int dy[4] = { 0,0,1,-1 };  // 좌우
void dfs(int x, int y)
{
    cnt++;
    visit[x][y] = true;
    for (int i = 0; i < 4; i++)
    {
        int nx = x + dx[i]; // 각 x의 위아래
        int ny = y + dy[i]; // 각 y의 좌우
        if (nx >= n || nx < 0 || ny >= n || ny < 0) // 만약 위아래 좌우 한곳이라도 범위를 벗어난 경우는 고려하지않는다.
            continue;
        if (!visit[nx][ny]&& arr[nx][ny]) // 그리고 1일 경우와 방문하지 않을 경우만 dfs로 탐색한다.
            dfs(nx, ny);
    }
}
int main()
{
    cin >> n;
    for (int i = 0; i < n; i++)
    {
        string temp;
        cin >> temp;
        for (int j=0; j < n; j++)
        {
            arr[i][j] = temp[j] - '0';
        }
    }

    for (int i = 0; i < n; i++)
    {
        for (int j = 0; j < n; j++)
        {
            if (arr[i][j] && !visit[i][j])
            {
                cnt = 0;
                dfs(i, j);
                answer.push_back(cnt);
            }
        }
    }
    sort(answer.begin(), answer.end());
    cout << answer.size() << endl;
    for (auto i : answer)
        cout << i << endl;  
}

```


# 프로그래머스

```C++
2021/07/12
베스트엘범 lv3
스트리밍 사이트에서 장르별로 가장 많이 재생된 노래를 두개씩 모아 엘범을 출시한다.
노래는 index로 구분하고 기준은 다음과 같다.
1. 한 장르에서 많이 재생된 장르를 먼저 수록
2. 장르 내에 많이 재생된 노래를 먼저 수록
3. 장르 내 재생 횟수가 같은 노래중 index가 낮은 노래 먼저 수록
장르는 100개 미만이고 장르에 곡이 하나밖에 없으면 하나만 선택한다.
모든 장르는 재생된 횟수가 다르다.

사람들의 테스트케이스 그리고 직접 생각한 케이스 전부 돌렸지만 맞다고 나왔다.
하지만 제출에는 40%만 맞았다고 나왔다.
무엇이 문젠지 다시 파악 후 코드 정리하고 다시 제출해봐야겠다.

#include <string>
#include <vector>
#include <set>
#include <algorithm>
#include <iostream>
using namespace std;
using pii = pair <int, string>;

vector<int> solution(vector<string> genres, vector<int> plays) {


	vector<pii>v;
	set<string>s;
	vector<pii>temp;
	for (int i = 0; i < genres.size(); i++)
	{
		v.push_back({ plays[i],genres[i] });
		s.insert(genres[i]);
	}
	for (auto i : s)
		temp.push_back({ 0 , i });
	for (int i = 0; i < temp.size(); i++)
	{
		for (int j = 0; j < genres.size(); j++)
		{
			if (temp[i].second == genres[j])
				temp[i].first += plays[j];
		}
	}
	sort(temp.begin(), temp.end());
	reverse(temp.begin(), temp.end());
	/////////////////////////////////////////
	vector<int>answer;
	for (int i = 0; i < temp.size(); i++)
	{
		int song1 = -1, song2 = -1, i1 = -1, i2 = -1;

		for (int j = 0; j < v.size(); j++)
		{
			if (temp[i].second == v[j].second)
			{
				if (v[j].first > song1)
				{
					int t = song1;
					int ti = i1;

					song1 = v[j].first;
					i1 = j;

					song2 = t;
					i2 = ti;
				}
                else if (song2 == -1)
                {
                    song2 = v[j].first;
                    i2 = j;
                }
                else if (v[j].first == song1)
                {
                    if (song1 > song2)
                    {
                        song2 = song1;
                        i2 = j;
                    }
                    else
                    {
                        song2 = song1;
                        if (i2 > j)
                            i2 = j;
                    }
                   
                }
			}
		}
		answer.push_back(i1);
		if (i2 != -1)
			answer.push_back(i2);
	}
	return answer;
}
int main()
{
	
    vector<int>s = solution({ "classic","classic","classic","classic","pop" }, { 500,150,800,800,2500
});
    for (auto i : s)
        cout << i << endl;
}
```

```C++
/*
2021/04/01
여행경로
항공권을 모두 이용하여 여행 경로를 짜ㅕ고한다.
항상 "ICN"공항에서 출발한다.
항공권 정보가 담긴 2차원배열 tickets가 변수로 주어질때,
방문하는 공항 경로를 배열에 담아 return한다.
1. 모든 공항은 알파벳 대문자 3글자로 이루어진다.
2. 주어진 공항수는 3개개 이상 10000개이하이다.
3. tickets의 각 행[a,b]는 a공항에서 b공항으로 가는 항공권이 있다는 의미이다.
4. 주어진 항공권은 모두 사용한다.
5. 만일 가능한 경로가 2개 이상일 경우 알파벳 순서가 앞서는 경로로 return한다.
6. 모든 도시를 방문 할 수 없는 경우는 주어지지 않는다.

모든 경로를 ans벡터에 담은 과정을 구현했지만
알파벳 순서대로 하는 방법은 미구현
또한, 여행경로가 끊어지게 되고 항공권이 남아있어도 모두 써야하는 부분도 고려해야한다.
*/
#include <string>
#include <vector>
#include <iostream>
#include <algorithm>

using namespace std;
vector<vector<string>> ans;
void dfs(vector<vector<string>> tickets, vector<string> tmp,string start, string end, int count,int index)
{
	tmp.push_back(start);
	start = tickets[index][0];
	end = tickets[index][1];
	if (count == tickets.size())
	{
		tmp.push_back(end);
		ans.push_back(tmp);
		return;
	}

	tickets[index][0] = "0";
	tickets[index][1] = "0";
	for (int i = 0; i < tickets.size(); i++)
	{
		//tickets[i][0] != "0" &&
		if (end == tickets[i][0])
		{
			dfs(tickets, tmp, tickets[i][0], tickets[i][1], count + 1,i);
		}
	}

}
vector<string> solution(vector<vector<string>> tickets) {

	for (int i = 0; i < tickets.size(); i++)
	{
		vector<string>tmp;
		if (tickets[i][0] == "ICN")
		{
			dfs(tickets, tmp, tickets[i][0], tickets[i][1], 1, i);
		}
	}

	vector<string> s(ans.size());
	for (int i = 0; i < ans[0].size(); i++)
	{
		for (int j = 0; j < ans.size(); j++)
		{
            

		}
	}
	vector<string> answer = ans[answer_index];
	return answer;
}
```
```C++
/*
2021/03/29
단어 변환
두개의 단어 begin, target과 단어의 집합 words가 있을때
다음과 같은 규칙을 이용하여 begin->target으로 변환하는 가장
짧은 변환 과정을 찾는 문제이다.
1. 한번에 한개의 알파벳만 변환할 수 있다.
2. words에 있는 단어로만 변환할 수 있다.

ex) "hit" -> "cog"로 변환 하려면
hot, dot, dog, lot, log, cog 가 words에 있을때
hit -> hot -> dot -> dog -> cog와 같이 4단계를 거친다.

이 문제는dfs로 풀었다.
먼저 solution함수에서 words안에 begin과 한개의 알파벳이 다른 단어들을 시작으로
반목문 한번을 돌린다. 여기서 단어 비교를 하는 함수는 따로 빼주었다.
dfs에선 단어를 변환 하면 "0"으로 바꿔서 visit을 체크해주었다.
그리고 target과 같은 경우 answer벡터에 증가한 count+1만큼 push한다.
다른 dfs에서 반복문을 통해 "0"이 아니고, 알파벳이 1개가 차이나는 알파벳으로 dfs에 값을
넣어 호출한다.
dfs를 나오면 변환하는 방법들의 개수가 answer에 들어가있고, 그 중 가장 작은 숫자를
반환하는 식으로 문제를 풀었다.
*/
#include <string>
#include <vector>
#include <algorithm>
using namespace std;
vector<int> answer;
int compare_num(string str, string st)
{
    if (st == "0")
        return 0;
	int c = 0;
	for (int i = 0; i < str.size(); i++)
	{
		if (str[i] != st[i])
			c++;
	}
	return c;
}
void dfs(string cw, string target,vector<string> word,int index,int count)
{
    cw = word[index];//변환한 단어로 대입
    if (cw == target)
    {//만약 taget과 현재 단어가 같다면 값을 넣고 return한다.
        answer.push_back(count+1);
        return;
    }
    word[index] = "0"; //visited
    for (int i = 0; i < word.size(); i++)
    {//"0"이 아니고 알파벳의 차이가 1개가 나는 단어일 경우 dfs를 호출한다.
        if (compare_num(cw, word[i]) == 1)
            dfs(cw, target, word, i, count + 1);
    }
}
int solution(string begin, string target, vector<string> words) {
 
    for (int i = 0; i < words.size(); i++)
    {//words에서 알파벳 차이가 1개가 나는 단어를 시작점으로 dfs에 넣기 위한 반복문
        if (compare_num(begin, words[i])==1)
            dfs(words[i],target,words,i,0);
    }
    if(answer.size() == 0)
        return 0;//찾지 못할 경우 예외처리
    sort(answer.begin(), answer.end()); //가장 작은 숫자를 반환
    return answer[0];
}
```
```C++
/*
2021/03/28
2 x n 타일링(피보나치)
가로 2, 세로 1인 직사각형을 이용하여
가로 n, 세로 2인 직사각형을 채우는 방법의 개수를 return하는 문제이다.
n을 1부터 4까지 했을 때 규칙성을 찾을 수 있었고
피보나치 수열인 것을 알았다.
앞전에 배운 모듈러의 속성을 이용하여 문제를 풀었다.
*/
#include <string>
#include <vector>
#include <iostream>

using namespace std;

int solution(int n) {
	int answer = 0;
    int num = 1000000007;
    int a = 1, b = 2;
    if (n == 1)
        return a;
    else if (n == 2)
        return b;
	else
	{
		for (int i = 1; i <= n - 2; i++)
		{
            answer = (a + b) % num ;
            a = b % num;
            b = answer % num;
		}
	}
	return answer;
}
```
```C++
/*
2021/03/24
단속카메라(탐욕법)
고속도로를 이동하는 모든 차량이 카메라에 한번은 만나게 하려고한다.
최소 몇대의 카메라를 설치해야하는지 return하는 문제이다.
*/
#include <string>
#include <vector>
#include <algorithm>

using namespace std;

int solution(vector<vector<int>> routes) {
    sort(routes.rbegin(), routes.rend());
    int answer = 0, flag = 30002;

    for(size_t i = 0; i < routes.size(); i++){
        if(flag > routes[i][1]){
            flag = routes[i][0];
            answer++;
        }
    }
    return answer;
}
```
```C++
/*
2021/03/06
네트워크(dfs/bfs)
네트워크는 컴퓨터 상호간에 정보를 교환할 수 있또록 연결된 형태이다.
컴퓨터 A와 B가 직접 연결되고 B와 C가 연결되면 A와 C도 간접적으로 연결되어있다.
따라서 ABC는 모두 같은 네트워크 상에 있다고 할 수 있다.
컴퓨터의 개수 n, 연결에 대한 정보가 담긴 2차원 배열이 매개변수로 주어질 때
네트워크의 개수를 return하는 문제이다.
* 컴퓨터의 개수 n은 1이상 200이하인 자연수
* 각 컴퓨터는 0부터 n-1인 정수로 표현
* i번 컴퓨터와 j번 컴퓨터가 연결되어있으면 computers[i][i]를 1로 표현한다.
* computers[i][i]는 항상 1이다.

이 문제는 dfs를 이용하여 풀었다. 처음엔 dfs말고 완전탐색으로 풀려고 했지만
반복문이 많아 시간복잡도에서 걸렸다.
결국 dfs를 사용하여 풀었는데 시간이 오래 걸렸다.
solution함수 for문은 [n][n]이 각 노드를 가르킨다는 성질을 이용하여 
노드는 존재하기만 하면 [n][n] == 1이다. 그러므로
각 컴퓨터를 기준으로 반복문에 들어간다. 
dfs함수로 들어가서 방문을 하면 1->0으로 바꿔준다.
dfs함수의 반복문은 연결된 컴퓨터를 탐색하는 반복문이다.
만약 [n][a]가 1이라면 컴퓨터 n과 a에 해당하는 알파벳의 컴퓨터가 연결되어
있다. 만약 연결이 되어있다면 dfs함수를 다시 불러 연결된 노드를 이어서 탐색한다.
만약 끊어졌다면 재귀를 탈출한다.
만약 이어졌다면 컴퓨터 끼리의 네트워크가 형성되었다는 뜻이므로 true를 반환한다.
solution에서 네트워크가 형성되었다는 ture를 반환받으면
answer를 증가해준다.

네트워크가 연결된 부분을 판별할 때 [n][n]외에도 [n][a]도 방문했다고 0으로 만들어줬으나
그렇게 된다면 A->B 연결을 확인하고 B->A의 확인을 할 수 없다. 즉 일방통행의 형태가 되어버린다.
어차피 A,B,C모두 한번씩 이어진 네트워크를 탐색하기에 0으로 만들어 줄 필요는 전혀 없다.
*/
#include <string>
#include <vector>
#include <iostream>
using namespace std;

bool dfs(vector<vector<int>> &com, int n)
{
 //방문한 노드는 재귀함수를 탈출한다.
    if (com[n][n] == 0)
        return false;
    com[n][n] = 0;//방문 체크
    for (int a = 0; a < com.size(); a++)
    {//노드의 수 만큼 반복하며
        if (com[n][a])//만약 com[n][a]가 1, 즉 연결이 되어있다면 재귀를 통하여 탐색을 이어간다.
            dfs(com, a);
    }
    return true; // 탐색을 마치면 true를 반환하여 answer의 값을 증가한다.
}

int solution(int n, vector<vector<int>> computers) {
    
    int answer = 0;
    for (int a = 0; a < computers.size(); a++)
    {
        if (computers[a][a] == 1 && dfs(computers, a))
            answer++;//순회하지 않은 노드 즉 [a][a]가 1이고 dfs 반환값이 true면 answer를 증가한다.
    }
    return answer;
}
```

```C++
/*
2021/03/02
N개의 최소공배수
N개의 숫자가 담긴 배열을 주었을 때
N개의 최소 공배수를 반환하는 문제이다.
sort를 사용하여 맨 뒤에 제일 큰 값을 넣고 곱하면서
앞에서부터 나누었을 때 나머지가 전부 0이면 반환하는 것으로 구현하였다.
*/
#include <string>
#include <vector>
#include <algorithm>
using namespace std;

int solution(vector<int> arr) {
    sort(arr.begin(), arr.end());
    int max = arr[arr.size() - 1];
    while (1)
    {
        int cnt = 0;
        for (int i = 0; i < arr.size() - 1; i++)
        {
            if (arr[arr.size() - 1] % arr[i] != 0)
                break;
            cnt++;
        }
        if (cnt == arr.size() - 1)
            return arr[arr.size() - 1];
        arr[arr.size() - 1] += max;

    }
}
```
```C++
/*
2021/03/02
JadenCase문자열 만들기
JadenCase는 모든 단어의 첫 문자가 대문자이고 그 외의 알파벳을 소문자이다.
주어진 문자열을 JadenCase로 만들어 반환하여라

처음에는 sstream을 사용하여 풀었다.
테스트 케이스는 맞았지만 streamstring은 이용하면 공백 혹은 탭을 기준으로
문자열을 자르기 때문에 중간에 연속된 문자열을 넣어줄 수가 없어서 히든케이스에서 실패했다.

결국 flag를 이용하여 단어 하나하나 접근하여 문제를 해결했다.
*/
#include <string>
#include <vector>

using namespace std;

string solution(string s) {
    int flag =1;
    for(int i =0; i < s.size(); i++)
    {
        if(s[i] == ' ')
        {
            flag = 1;
            continue;
        }
        if(flag == 1) 
        {
            s[i] = toupper(s[i]);
            flag = 0;
            continue;
        }
        s[i] = tolower(s[i]);
    }
    return s;
}
```
```C++
/*
2021/03/02
행렬의 곱셈
2차원 행렬 arr1과 arr2를 받아 arr1에 arr2를 곱한 결과를 반환한다.
i는 arr1의 세로 반복문
j는 arr2의 세로 반복문
x는 arr1의 가로와 arr2의 세로 반복문
*/
#include <string>
#include <vector>

using namespace std;

vector<vector<int>> solution(vector<vector<int>> arr1, vector<vector<int>> arr2) {
    vector<vector<int>> answer;
    for(int i = 0; i < arr1.size(); i++)
    {
        vector<int> tmp;
        for(int j =0; j< arr2[0].size(); j++)
        {
            int sum =0;
            for(int x= 0; x< arr1[i].size(); x++)
                sum += arr1[i][x]*arr2[x][j];
            tmp.push_back(sum);
        }
        answer.push_back(tmp); 
    }
    return answer;
}
```
```C++
/*
2021/03/01
피보나치 수
이 문제는 n번째의 피보나치 수를 구하는 문제이다.
피보나치는
f(0) = 0;
f(1) = 1;
f(n) = f(n-1) + f(n-2);
를 만족하는 수다.
피보나치를 구현하는 것은 어렵지 않았지만
이 문제의 포인트는 자료형의 크기를 넘어가기 때문에 n번째 수에
1234567을 나눈 값을 반환하는 것이다.
하지만 long long을 사용해도 값을 담을 수 없었고
구글링 해본 결과
44번 째 수만가도 2,971,215,073이기때문에 int의 범위를 넘어간다.
이 문제의 조건은 n은 100000까지 의 수다.
그렇기 때문에 int는 물론 long long을 범위를 넘어버린다.
그래서 모듈러 연산의 성질인

(A+B) % C == ((A % C) + (B % C)) % C

의 성질을 이용하여 풀었다.
피보나치의 수를 만들때마다 1234567을 각각 변수에 나눠도
n % 1234567의 값과 같다는 것이다.
공부한 내용으로는
어떤 값 A와 B가 n으로 나누었을 때 나머지가 같다면
A와 B는 모듈 C에 대한 합동 관계라고 한다.
그러한 A와 B는 A-B를 하였을 때 k*n과 같다.
즉
if (A%n == B%n)
위 조건을 만족 할 때
A - B == k * n가 성립하고
A,B는 모듈C에 대한 합동관계이다.
*/

#include <string>
#include <vector>

using namespace std;

int solution(int n) {
    int answer = 0;
    long long fn1 = 0;
    long long fn2 = 1;
    long long fn = 0;
       for (int i = 1; i < n; i++)
    {
        fn = fn1 + fn2;
        fn1 = fn2;
        fn2 = fn;
        fn1 %= 1234567;
        fn2 %= 1234567;
        fn %= 1234567;
    }
    answer = fn;
    return answer;
}
```

```C++
/*
2021/03/01
최솟값 만들기
이 문제는 크기가 같은 배열 두개를
배열의 사이즈 만큼 서로 곱하여 더했을 때 최솟값을 반환하는 문제이다.
A = 1,4,2
B = 5,4,4
일때 29가 최솟값이다.
sort를 사용하여 풀었다.
*/
#include <iostream>
#include<vector>
#include <algorithm>
using namespace std;

int solution(vector<int> A, vector<int> B)
{
    int answer = 0;
    sort(A.begin(), A.end());
    sort(B.begin(), B.end());
    for (int i = 0,j = A.size()-1; i < A.size(); i++,j--)
        answer += A[i] * B[j];
    return answer;
}
```

```C++
/*
2021/03/01
숫자의 표현
자연수 n을 연속한 자연수들로 표현하는 방법의 개수를 반환하는 문제이다.
예를들어 n이 15면
- 1+2+3+4+5 = 15
- 4+5+6 = 15
- 7+8 = 15
- 15 = 15
이렇게 4가지다.
*/
#include <string>
#include <vector>

using namespace std;

int solution(int n) {
    vector <int> tmp;
    int answer = 0;
    for (int i = 1; i <= n; i++)
        tmp.push_back(i);
    for (int i = 0; i < tmp.size(); i++)
    {
        int sum = tmp[i];
        for (int j = i + 1; j < tmp.size(); j++)
        {
            if (sum == n)
            {
                answer++;
                break;
            }
            if (sum > n)
                break;
            sum += tmp[j];
        }
    }
    return answer+1;
}
```
```C++
/*
2021/03/01
최댓값과 최솟값
문자열 s에 공백으로 구분된 숫자들이 저장되어있다.
이중 최소값 최대값을 찾아 반환한다.
*/
#include <string>
#include <vector>
#include <sstream>
#include <algorithm>
using namespace std;

string solution(string s) {
    string answer = "";
    stringstream str(s);
    string str_cut;
    vector <int> a;
    while (str >> str_cut)
        a.push_back(stoi(str_cut));
    answer += to_string(a[min_element(a.begin(), a.end()) - a.begin()]);
    answer += " ";
    answer += to_string(a[max_element(a.begin(), a.end()) - a.begin()]);
    return answer;
}
```

```C++
/*
2021/03/01
올바른 괄호
'('문자로 열었으면 ')'로 닫아야한다.
만약 닫혔으면 true, 아니면 false를 반환하는 문제이다.
수월하게 풀었다.
*/
#include<string>
#include <iostream>

using namespace std;

bool solution(string s)
{
    int cnt = 0;
    for(int i = 0; i< s.size(); i++)
    {
        if(s[i]== '(')
            cnt++;
        else
            cnt--;
        if(cnt <0)
            return false;
    }
    return cnt ==0 ? true : false;
}
```
```C++
/*
2021/03/01
땅따먹기
이 문제는 땅이 총 N행, 4열로 이루어져있고
1행부터 땅을 밟으며 한 행씩 내려올때 각 행의 4칸 중 한 칸만 밟으면서 와야한다.
단 같은 열을 연속해서 밟을 수 없다.
1 2 3 5
5 6 7 8
4 3 2 1
이 있다면
1행4칸(5)
2행3칸(7)
3행1칸(4)
를 밟아 16점이 최고점이 된다.
이 최고점을 반환하는 문제이다.

처음엔 우선순위 큐로 풀어보려고 했다. 페어를 선언하여
값과 인덱스를 데리고 다니면서 큐에 저장하는 방식으로 풀려고했다.
하지만 행을 내려갈때마다 큐를 비우거나 새로 만들어야하는데 이러면 메모리적인 측면에서 안좋다고
생각하여 정렬을 이용하여 풀어보려고했다.
매 행을 정렬하여 인덱스를 따로 포함하여 행마다 체크를 해주면서 풀려고했지만
다른 방법이 있을 것 같아서 좀 더 고민했다.
이전에는 land[i]와 land[i+1]를 비교하여 land[i]에 값을 바꾸면서 내려가려고 했지만
그렇게 되면 land[i+2]번째 행에서는 값을 비교하기 어려워진다.
그래서 반대로 두번째 행에서부터 위의 값을 받아 가기로 하여 max를 이용하여 풀었다.
max를 사용할 때 max(a,b) 처럼 두개를 비교할땐 그냥 쓰면 되지만
인자가 3개 이상일 땐 max({a,b,c})처럼 묶어줘야하는 걸 배웠다.
총 정리를 해보자면

우선순위 큐 -> 공간복잡도 높음
정렬 -> 코드의 가독성 낮음
dp(max) -> 최종 풀이
max() -> 인자가 3개 이상일때 {}로 감싸야한다.

*/
#include <iostream>
#include <vector>
#include <algorithm>
#include <queue>
using namespace std;

int solution(vector<vector<int> > land)
{
	int answer = 0;
    for (int i = 0; i < land.size()-1; i++)
    {
        land[i + 1][0] += max({ land[i][1],land[i][2], land[i][3] });
        land[i + 1][1] += max({ land[i][0],land[i][2], land[i][3] });
        land[i + 1][2] += max({ land[i][0],land[i][1], land[i][3] });
        land[i + 1][3] += max({ land[i][0],land[i][1], land[i][2] });
    }
    answer = max({ land[land.size()-1][0],land[land.size()-1][1],land[land.size()-1][2],land[land.size()-1][3] });
	return answer;
}
int main()
{
    vector <vector<int>> a = { {1,2,3,5},{5,6,7,8 },{ 4,3,2,1 } };
    int v = solution(a);
    cout << v;
	return 0;
}

```
```C++
/*
2021/02/24
다음 큰 숫자
자연수 n이 주어졌을 때 다음을 만족하는 숫자를 구하는 문제이다
1. 다음 숫자는 n보다 크다.
2. 다음 숫자와 n을 2진수로 변환했을때 1의 갯수가 같다.
3. 다음 숫자는 조건 1,2를 만족하는 수중 가장 작은 수다.

위와 같은 조건을 만족하는 숫자를 찾기 위해선 2진수로 변환해야했고
따로 함수를 뺴주었다.

ps -> n은 1,000,000이하의 자연수
*/
#include <string>
#include <vector>
#include <algorithm>
#include <iostream>
using namespace std;
int divide(int a)
{
	int one_cnt = 0;
	while (a != 1 && a != 0)
	{
		if (a % 2 == 1)
			one_cnt++;
		a /= 2;
	}
	return a == 1 ? one_cnt+1 : one_cnt;
}
int solution(int n) {
	int answer = n;
	int n_cnt = divide(n);
	while (1)
	{
		if (n_cnt == divide(++answer))
			break;
	}
	return answer;
}
```
```C++
/*
2021/02/20
가장 큰 정사각형 찾기
1과 0으로 채워진 표에
가장 큰 정사각형의 넓이를 구하여라
0 1 1 1
1 1 1 1
1 1 1 1
0 0 1 0
이렇게 있을떄 가장 큰 정사각형의 넓이는 9이다.
이 문제는 dp문제이다.
처음에 이중 포문은 두번쨰 가로 줄부터 보드를 도는 반복문이다.
최소한 정사각형이 되려면 위, 왼쪽, 왼쪽위를 봐야하기 떄문이다.
만약 본인, 위, 왼쪽, 왼쪽 위 중에 0 이있다면 min값에 1을 더하기 떄문에
그대로 1이 된다. 전부 1이면 2가되어 적어도 2의 길이를 가진 정사각형이
되는 것이다. 이런식으로 반복문을 돌면 중첩이 되어 가장 큰 정사각형의 맨 아래 오른쪽에
길이가 남을 것이다. 길이를 제곱해주고 반환하면 문제는 해결된다.
예외로 1이 없는 보드와 맨 윗줄에 1이 하나있는 경우가 있는데
1이 없는 보드는 0을 반환하고
맨 윗줄에 1이 하나있는 경우는 flag를 이용했다.
temp는 변하지 않지만 1을 만나 flag가 1이 된다면 정사각형의 최소 길이인 1을 반환한다.
*/

#include <iostream>
#include <vector>
#include <algorithm>
using namespace std;

int solution(vector<vector<int>> board)
{
	int col = board.size();
	int row = board[0].size();
	int temp = 0;
	int flag = 0;
	for (int a = 1; a < col; a++)
	{
		for (int b = 1; b < row; b++)
		{
			if (board[a][b] == 1)
			{
				board[a][b] = 1 + min({ board[a - 1][b - 1],board[a - 1][b],board[a][b - 1] });
				temp = max(temp, board[a][b]);
			}
		}
	}
	for (int a = 0; a < col; a++)
	{
		if (board[0][a] == 1)
			flag = 1;
	}
	if (flag == 1 && temp == 0)
		return 1;
	else
		return temp * temp;
}
int main()
{
	vector<vector<int>> b = { {1,0},{0,0} };
	int a = solution(b);
}
```
```C++
/*
2021/02/19
카펫
중앙이 노란색, 테두리 1줄은 갈색으로 칠해져있는 카펫이있을때
노란색 타일, 갈색 타일의 개수를 주었을때
가로와 세로의 길이를 반환한다.
단 가로 >= 세로이다.
이 문제는 갈색 + 노란색 == 세로*가로
즉 넓이를 이용하여 공약수를 이용하여 풀었다.
약수를 구하면서 세로와 가로의 길이를 임이로 정하여
가로 *2는 위 아래 갈색 타일의 개수
(세로-2)*2는 양옆 갈색 타일의 개수
이 둘을 더했을때 갈색 타일의 개수가 된다면 반환한다.
*/

#include <string>
#include <vector>

using namespace std;

vector<int> solution(int brown, int yellow) {
    int num = brown + yellow;
    for (int a = 1; a < num; a++)
    {
        if (num % a == 0)
        {
            int col = num / a;
            int row = num / col;
            if (col * 2 + (row - 2) * 2 == brown)
                return vector<int>{col, row};
        }
    }
}
```

```C++
/*
2021/02/19
H-index
과학자의 H-index의 값을 반환하는 문제이다.
논문 n편중 h번 이상 인용된 논문이 h편 이상이고 나머지 논문이 h번 이하 인용됐다면
h의 최대값이 과학자의 h-index이다. 부연설명을 하자면
인용논문 숫자가 논문 숫자와 같아지거나 인용논문 수가 논문수보다 작아지기 시작하는 숫자이다.
인용논문 <= 논문숫자 이시점을 캐치하여 반환하는게 핵심이다.
*/
#include <string>
#include <vector>
#include <algorithm>
using namespace std;

int solution(vector<int> citations) {
    sort(citations.begin(), citations.end());
    for (int a = 0; a < citations.size(); a++)
    {
        if(citations[a] >= citations.size() - a)
            return citations.size()-a;
    }
    return 0;
}
```

```C++
/*
2021/02/19
더 맵게
각 음식의 맵기를 담은 배열이 있을떄
모든 음식을 k보다 맵게 만들고 싶다.

섞은 음식= 가장 맵지 않은 음식 + (두번째로 맵지않은 음식 * 2)

형태로 모든 음식을 맵게 섞고 섞은 음식들은 제거한다.
섞는 횟수를 반환한다.
만약 섞어도 모든 음식이 k만큼 매워지지 않으면 -1를 반환한다.

이 문제는 우선순위 큐를 사용하여 풀었다.처음엔 벡터를 이용하여 정렬한뒤
문제를 풀려 했지만 섞고 나면 지속적으로 섞거나 MIN_ELEMENT를 해야하기 떄문에
시간 복잡도에서 실패를 맛봤다.

포인트로는 우선 순위 큐에 값을 집어넣고 가장 작은 값을 변수에 담아 pop을 두번 해줌으로 가장 안매운 음식과,두 번쨰로 안매운 음식을 제거했다.
이런식으로 우선순위 큐를 이용하여 풀었다.
q.top() +1 을 하게 되면 그 다음으로 맵지 않은 음식이 들어 갈줄 알았지만, 짧은 생각이였다.
말그대로 q.top()에 1을 더해준 값이 된다ㅋㅋ
이 기회로 queue에 대해 확실하게 정리했다.
*/
#include <string>
#include <vector>
#include <algorithm>
#include <iostream>
#include <queue>
using namespace std;

int solution(vector<int> scoville, int K) {
    int answer = 0;
    if(scoville.size() <= 1)
        return 0;
    priority_queue<int, vector <int>, greater<int>>q;
    for (int a : scoville)
        q.push(a);

    while (1)
    {
        if (q.top() >= K)
            return answer;
        if (q.size() == 1)
            return -1;
        int f = q.top();
        q.pop();
        int s = q.top();
        q.pop();
        int temp = f + (s * 2);
        q.push(temp);
        answer++;
    }
    return answer;
}
```

```C++
/*
2021/02/16
카카오 인턴 키패드 누르기
*/

#include <string>
#include <vector>
#include <cmath>
#include <iostream>
using namespace std;
struct point { //각 배열의 구조체를 선언하여 좌표와 숫자를 대입한다.
	int x = 0;
	int y = 0;
	int num = 0;
};
point get(int nu, vector<point>p)
{//노드의 위치를 키패드의 숫자 기반으로 비교하여 구조체를 반환한다.
	for (auto a : p)
	{
		if (a.num == nu)
			return a;
	}
}
string solution(vector<int> numbers, string hand) {
	string answer = "";
	vector <point> p;//구조체형태의 백터 선언
	point left, right; //현재 왼손과 오른손의 위치
	for (int a = 0; a < 4; a++)
	{//키패드 1~9까지의 숫자와 좌표를 벡터에 넣어 키패드 완성
		for (int b = 0; b < 3; b++)
		{
			point t;
			t.x = a;
			t.y = b;
			t.num = a * 3 + b + 1;
			p.push_back(t);
		}
	}
	p[10].num = 0;// 숫자 0은 따로 예외로 처리해준다.
	left = p[9]; //* 
	right = p[11]; //#

	for (int a = 0; a < numbers.size(); a++)
	{// numbers배열에 들어온 숫자를 돌면서 해당하는 손의 위치를 반환하는 반복문
		if (numbers[a] == 1 || numbers[a] == 4 || numbers[a] == 7)
		{//1,4,7일 경우 무조건 왼손이다
			answer += "L";
			left = get(numbers[a], p); //현재 왼손의 위치를 대입한다.
		}
		else if (numbers[a] == 3 || numbers[a] == 6 || numbers[a] == 9)
		{//3,6,9일 경우 무조건 오른손이다.
			answer += "R";
			right = get(numbers[a], p); //현재 오른손의 위치를 대입한다.
		}
		else
		{
			point n = get(numbers[a], p);// 2,5,8,0일경우 노드를 만든다.
			int dis_l = abs(left.x - n.x) + abs(left.y - n.y); // 왼손으로 부터 n까지의 거리를 구한다. x끼리, y끼리의 차이를 더한다.
			int dis_r = abs(right.x - n.x) + abs(right.y - n.y); // 위와 마찬기지로 오른손의 거리를 구한다.
			if (dis_l > dis_r)
			{ // 왼손의 거리가 더 멀면 오른손을 움직인다.
				answer += "R";
				right = get(numbers[a], p);
			}
			else if(dis_l < dis_r)
			{ // 오른손의 거리가 더 멀면 왼손을 움직힌다.
				answer += "L";
				left = get(numbers[a], p);
			}
			else
			{ // 왼손과 오른손의 거리가 같으면
				if (hand == "left")
				{ //왼손잡이면 왼손을 움직이고
					answer += "L";
					left = get(numbers[a], p);
				}
				else
				{ //오른손잡이면 오른손을 움직인다.
					answer += "R";
					right = get(numbers[a], p);
				}
			}
		}
	}
	return answer;
}
```

```C++
/*
2021/02/14
예산
배열의 원소를 각 부서의 신청금액이라고 했을떄 
정해진 금액이하의 예산에 맞춰 지원가능한 최대 부서의 숫자를 구하여라
*/
#include <iostream>
#include <stdio.h>
#include <string>
#include <vector>
#include <algorithm>
using namespace std;

int solution(vector<int> d, int budget) {
    int answer = 0;
    int sum =0;
    sort(d.begin(), d.end());
    for(int a : d)
    {
        sum += a;
        if(sum <= budget)
            answer++;
        else
            break;
    }
    return answer;
}
```

```C++
/*
2021/02/13
직사각형 별찍기
*/
#include <iostream>
using namespace std;
int main(void) {
    int a;
    int b;
    cin >> a >> b;
    //cout << a + b << endl;
    for(int i =0; i <b; i++)
    {
        for(int j =0; j<a; j++)
            cout << "*";
        cout << endl;
    }
    return 0;
}
```

```C++
/*
2021/02/13
x만큼 간격이 있는 n개의 숫자
정수 x와 자연수 n을 입력받아 x부터 시작해 x씩 증가하는 숫자를 n개 지니는
배열을 반환한다.
*/
#include <string>
#include <vector>

using namespace std;

vector<long long> solution(int x, int n) {
    vector<long long> answer;
    for(int a=1; a<=n; a++)
        answer.push_back(x*a);
    return answer;
}
```

```C++
/*
2021/02/12
행렬의 덧셈
2차원 벡터 2개를 더한 벡터를 리턴한다.
*/
#include <string>
#include <vector>

using namespace std;

vector<vector<int>> solution(vector<vector<int>> arr1, vector<vector<int>> arr2) {
    vector<vector<int>> answer(arr1.size(),vector<int>(arr2[0].size()));
    for(int a=0; a<arr1.size(); a++)
    {
        for(int b=0; b<arr2[a].size(); b++)
           answer[a][b]= arr1[a][b] + arr2[a][b];
    }
    return answer;
}
```

```C++
/*
2021/02/12
핸드폰 번호 가리기
뒷자리 4자리를 제외한 숫자를 전부 *로 바꾼다.
*/
#include <string>
#include <vector>

using namespace std;

string solution(string phone_number) {
    for(int a =0; a< phone_number.size()-4; a++)
        phone_number[a] = '*';
    return phone_number;
}
```

```C++
/*
2021/02/12
하샤드 수
양의 정수 x의 자릿수의 합으로 x가 나누어지면 하샤드의 수.
판별하는 함수를 구현한다.
*/
#include <string>
#include <vector>

using namespace std;

bool solution(int x) {
    string a = to_string(x);
    int temp =0;
    for(auto i : a)
        temp += i-'0';
    return x%temp==0 ? true : false;
}
```

```C++
/*
2021/02/12
평균 구하기
정수를 담고 있는 배열 arr의 평균 값을 리턴한다.
*/
#include <string>
#include <vector>

using namespace std;

double solution(vector<int> arr) {
    double answer = 0;
    for(auto a : arr)
        answer += a;
    answer = answer/arr.size();
    return answer; 
}
```

```C++
/*
2021/02/12
콜라츠 추측
어떤 숫자든 다음을 거치면 1이된다.
짝수면 2로 나눈다. 홀수면 3을 곱하고 1을 더한다.
작업한 횟수를 리턴한다. 500번이 넘어가면 -1을 반환한다.
*/
#include <string>
#include <vector>

using namespace std;

int solution(int num) {
    if (num ==1)
        return 0;
    long long a =(long long)num;
    for(int answer =1; answer <=500; answer++){
        a %2 ==0 ? a /= 2: a = (a*3) +1 ;
        if(a == 1)
            return answer;
    }
    return -1;

}
```

```C++
/*
2021/02/12
짝수와 홀수
짝수면 Even, 홀수면 Odd반환
*/
#include <string>
#include <vector>

using namespace std;

string solution(int num) {
    string answer = "";
   return num%2==0 ? answer = "Even" : answer = "Odd";
}
```

```C++
/*
2021/02/12
제일 작은 수 제거하기
정수를 저장한 배열에서 가장 작은수를 제거하고 반환한다.
빈 배열이거나 size가 1이면 -1를 반환한다.
*/
#include <string>
#include <vector>
#include <algorithm>
using namespace std;

vector<int> solution(vector<int> arr) {
    vector<int> answer;
    if(arr.size() <=1 )
    {
        answer.push_back(-1);
        return answer;
    }
    int min = *min_element(arr.begin(),arr.end());
    //int a = find(arr.begin(),arr.end(),min)-arr.begin();//find함수써서 찾는법
    for(int a =0; a< arr.size(); a++)
    {
        if(arr[a] == min)
            arr.erase(arr.begin()+a);
	    
    }
    return arr;
}
```

```C++
/*
2021/02/12
정수 제곱근 판별
임의의 양의 정수 n에 대해 n이 어떤 양의 정수x의 제곱인지 아닌지 판단하고
맞으면 x+1의 제곱을 리턴, 아니면 -1을 리턴한다.
*/
#include <string>
#include <vector>
#include <cmath>
using namespace std;

long long solution(long long n) {
    long long answer = 0;
    return sqrt(n) /1.00 != (int)sqrt(n) ? answer = -1 : answer = pow(sqrt(n)+1,2);
}
```

```C++
/*
2021/02/12
정수 내림차순으로 배치하기
n의 각 자릿수를 큰 것부터 작은 순으로 정렬한 정수 반환
*/
#include <string>
#include <vector>
#include <algorithm>

using namespace std;

long long solution(long long n) {
    long long answer = 0;
    string a = to_string(n);
    sort(a.begin(), a.end(),greater<>());
    answer += stoll(a);
    return answer;
}
```

```C++
/*
2021/02/12
자연수 뒤집어 배열로 만들기
자연수 n을 뒤집어 각 자리 숫자를 원소로 가지는 배열을 반환한다.
*/
#include <string>
#include <vector>
#include <algorithm>
using namespace std;

vector<int> solution(long long n) {
    vector<int> answer;
    string temp = to_string(n);
    for(auto a : temp)
        answer.push_back(a - '0');
    reverse(answer.begin(), answer.end());
    return answer;
}
```

```C++
/*
2021/02/12
자릿수 더하기
자연수 N이 주어지면 각 자리수의 합을 구한다.
*/
#include <iostream>
#include <string>
#include <cstdlib>
using namespace std;
int solution(int n)
{
    string a = to_string(n);
    int answer = 0;
    for (auto i : a)
        answer += i - '0';
    return answer;
}
```

```C++
/*
2021/02/12
이상한 문자 만들기
문자열 s는 한 개 이상의 단어로 구성되어있다. 각 단어는 하나 이상의 공백문자로 구분된다.
각 던어의 짝수번째 알파벳은 대문자로, 홀수는 소문자로 바꾸어 문자열을 반환하다.
이 문제는 toupper()과 tolower()를 이용하여 문제를 해결하였다.
flag를 사용하여 각 인덱스의 단어 순번을 나타냈다.
*/
#include <string>
#include <vector>
using namespace std;

string solution(string s) {

	string answer = "";
	int word = 0;
	for(int siz =0; siz < s.size(); siz++)
	{
		if (s[siz] == ' ')
		{
			answer += " ";
			word = 0;
			continue;
		}
		if (word == 0)
		{
			answer += toupper(s[siz]);
			word = 1;
		}
		else
		{
			answer += tolower(s[siz]);
			word = 0;
		}
	}
	return answer;
}

```

```C++
/*
2021/02/10
약수의 합
정수 n을 입력받아 n의 약수를 모두 더한 값을 반환한다.
*/
#include <string>
#include <vector>

using namespace std;

int solution(int n) {
    int answer = 0;
    for (int a = 1; a <= n; a++)
    {
        if(n%a ==0)
           answer += a;
    }
    return answer;
}
```

```C++
/*
2021/02/10
시저 암호
어떤 문장의 각 알파벳을 n만큼 오른쪽으로 밀어서 다른 알파벳으로 암호화한다.
Z를 넘어가면 돌아가서 A부터 민다.
z를 넘어가면 돌아가서 a부터 민다.
*/
#include <string>
#include <vector>

using namespace std;

string solution(string s, int n) {
    string answer = "";
    for (int a = 0; a < s.size(); a++)
    {
        if (s[a] == ' ')
        {
            answer += ' ';
            continue;
        }
        if(s[a] >='A' && s[a] <= 'Z')
        {
            if (s[a] + n > 'Z')
                answer += s[a] +n -'Z' +'A'-1;
            else
                answer += s[a] + n;
        }
        else if(s[a] >= 'a' && s[a] <= 'z')
        {
            if(s[a] + n > 'z')
                answer += s[a] +n -'z' + 'a'-1;
            else
                answer += s[a] + n;
        }
    }
    return answer;
}
```
```C++
/*
2021/02/10
문자열을 정수로 바꾸기
문자열을 정수로 바꾼다. 부호 +나 -도 인식해서 바꿔준다.
stoi를 사용하면 -나 +도 인식한다.
*/
#include <string>
#include <vector>

using namespace std;

int solution(string s) {
     int answer = stoi(s) ;
    return answer;
}
```


```C++
/*
2021/02/09
수박수박수박
길이가 n일떄 길이만큼 수박수박수박...의 형태로 반환한다.
*/
#include <string>
#include <vector>

using namespace std;

string solution(int n) {
    string answer = "";
    for(int a =0; a< n; a++)
        a %2 == 0 ?  answer += "수": answer += "박";
    return answer;
}
```

```C++
/*
2021/02/09
소수찾기Lv1
1부터 입력받은 숫자 n 사이에 있는 소수의 개수를 반환한다.
1은 소수가 아니다.
에라토스테네스의 체를 이용하여 풀었다.
다른 방법은 n^2의 시간 복잡도가 걸리는데 비해
에라토스테네스의 체는 nlogn의 시간복잡도가 있다.
즉 2부터 n까지의 하나씩 커지면서 배수들을 모조리 제외하는 방식이다.

*/
#include <string>
#include <vector>
#include <iostream>
using namespace std;
int solution(int n) {
	
    int answer = 0;
    //소수면 0, 소수가 아니면 1로 바꾸는 배열
    int vec[1000000] = { 0 };
    for (int i = 2; i <= n; i++)
    {//소수인지 확인하는 구간
        if (vec[i] == 0){
            answer++;
        for (int j = 1; i * j <= n; j++){//j를 곱하면서 늘려가면서 1로 바꾼다.
            vec[i * j] = 1;
        }
    }
}
    return answer;
}
```


```C++
/*2021/02/09
서울에서 김서방 찾기
문자열 배열에서 "Kim"을 찾으면 위치를 반환한다.
*/
#include <string>
#include <vector>

using namespace std;

string solution(vector<string> seoul) {
    string answer = "김서방은 ";
    for(int x = 0; seoul.size(); x++){
        if(seoul[x] == "Kim")
            return answer += to_string(x) + "에 있다";
    }
}
```

```C++
/*
2021/02/09
문자열 다루기 기본
문자열의 길이가 4 혹은 6이고 숫자로만 구성돼있으면 true를,
아니면 false를 반환한다.
*/
#include <string>
#include <vector>

using namespace std;

bool solution(string s) {
    for(auto a: s)
    {
        if(a<'0' || a>'9')
            return false;
    }
    return s.size() == 4|| s.size() == 6 ? true : false;
}
```

```C++
/*
2021/02/09
문자열 내림차순으로 배치하기
문자열을 내림차순으로 정렬하는 문제
*/
#include <string>
#include <vector>
#include <algorithm>
using namespace std;

string solution(string s) {
    string answer = "";
    sort(s.begin(),s.end());
    reverse(s.begin(),s.end());
    return s;
}
```

```C++
/*
2021/02/09
문자열 내 p와 y의 개수
대소문자 관계없이 문자열에서 p와 y의 개수가 같으면 true 다르면 false를 반환한다.
*/
#include <string>
#include <iostream>
using namespace std;

bool solution(string s)
{
    int p_cnt =0,y_cnt =0;
    for(auto a : s)
    {
        if(a == 'p' || a=='p'-32)
            p_cnt++;
        else if(a == 'y'||a=='y'-32)
            y_cnt++;
    }
    return p_cnt == y_cnt ? true : false;
}
```






```C++
/*
2021/02/09
문자열 내 마음대로 정렬하기
문자열로 구성된 리스트 string과 정수 n이 있고
각 문자열의 인덱스 n번쨰 글자를 기준으로 오름차순으로 정렬한다.
만약 인데스n번째 글자가 같다면 사전순으로 정렬한다.
이 문제는 이전에 공부했던 sort와 cmp를 이용하여 풀었다.
*/
#include <string>
#include <vector>
#include <algorithm>
#include <iostream>
using namespace std;
bool cmp(pair<string,char> a, pair<string,char> b)
{
    if(a.second == b.second)
        return a.first<b.first;
    else
        return a.second <b.second; 
}
vector<string> solution(vector<string> strings, int n)
{
    vector<string> answer;
    vector<pair<string,char>> temp;  
    for(auto a: strings)
        temp.push_back(make_pair(a,a[n]));
    sort(temp.begin(),temp.end(),cmp);
    for(auto a: temp)
        answer.push_back(a.first);
    return answer;
}
/* 코드를 정리하던 중 좀 더 나은 방식을 발견했다.
n을 전역변수로 받으면 pair로 가지고 다닐 필요가 없다.
아래가 정리한 코드인데 가독성도 늘어났을 뿐더러 훨씬 더 깔끔해졌다.
*/
#include <string>
#include <vector>
#include <algorithm>
#include <iostream>
using namespace std;

int j;
bool cmp(string a, string b)
{
    if(a[j] == b[j])
        return a<b;
    else
        return a[j] <b[j]; 
//삼항연산자를 이용할 경우 -> 조건 ? A : B -> 조건이 참이면 A를, 거짓이면 B를 반환한다.
// return a[j] == b[j] ?a<b: a[j] <b[j]; 
}
vector<string> solution(vector<string> strings, int n)
{
    j = n;
    sort(strings.begin(),strings.end(),cmp);
    return strings;
}
```

```C++
/*
2021/02/09
두 정수 사이의 합
두 정수 a,b가 주어졌을때 a,b를 포함하여 사이에 속한 모든 정수의 합을 리턴한다.
*/
#include <string>
#include <vector>

using namespace std;

long long solution(int a, int b) {
    long long answer = 0;
    if(a==b)
        return a;
    if(a >b)
    {
           for(int c =b; c<=a; c++)
        answer +=c; 
    }
    else if(a < b)
    {
           for(int c =a; c<=b; c++)
        answer +=c; 
    }
    return answer;
}
```
```C++
/*
2021/02/09
나누어 떨어지는 숫자 배열
배열의 각 요소 중 인자 divisor로 나누어 떨어지는 값을 오름차순으로 정렬하는 함수를 구현한다.
나누어떨어지는 요소가 없다면 -1을 반환한다.
매우 쉬운문제로
%과 sort함수를 이용하여 풀었다.
*/
#include <string>
#include <vector>
#include <algorithm>
using namespace std;

vector<int> solution(vector<int> arr, int divisor) {
    vector<int> answer;
    for(auto a: arr)
    {
        if(a%divisor == 0)
            answer.push_back(a);
    }
    if(answer.size()== 0)
        answer.push_back(-1);
    else
        sort(answer.begin(), answer.end());
    return answer;
}
```


![KakaoTalk_20210208_174634488](https://user-images.githubusercontent.com/45708825/107197274-08e67a80-6a37-11eb-9c70-5a2aebceb542.jpg)

```C++
/*
2021/02/08
같은 숫자는 싫어
배열에서 연속적으로 나타나는 숫자는 하나만 남기고 제거하는 문제이다.즉,
1,1,3,3,0,1,1 -> 1,3,0,1 이 된다.
제한 사항으로는 배열은 1,000,000 이하의 크기를 가졌다. 이말은
2중 포문을 쓰게되면 최악의 상황에 n^2의 1,000,000,000,000의 시간복잡도를를가진다.
1초에 1억의 연산을 하는데 10,000초의 시간이 걸린다.
반복문 한번에 끝내야하는 문제이다.나의 코드는 a가 각 자리를 돌면서
다음 숫자와 일치하면 다음 자리로, 일치하지 않으면 값을 answer에 담는 코드이다.
나름 잘 짰다고 생각했는데 한줄로 문제를 푼 사람도 있었다.
바로 erase와 unique를 사용했는데. 나는 벡터의 erase를 쓸경우 효율성 테스트에 실패 하기 떄문에
쓰는 것을 지양했었다
arr.erase(unique(arr.begin(),arr.end()),arr.end());
unique는 중복제거인 것은 알았지만 연속된 숫자만 제거하는 요구사항떄문에
배제하고 문제를 풀었다.
좀더 자세히 알고자 구글링을 하며 공부했다.
내가 이해한 것은 위과 같다.
unique함수는 배열을 돌며 연속되는 숫자를 만나면 뒤에 숫자를 앞으로 가져오고 그다음의 연속되지 않은 숫자를 바로 가져온다.
이런식으로 하면 건너뛴 숫자만큼 배열이 비게 되는데 이 부분은 원래 배열 인덱스에
속한 원소를 그래도 가져온다. 그래서 erase로 지워주는 것이다.
앞으로 아주 유용하게 사용할 것 같다.
아 그리고 unnique()를 쓰기 위해선 <algorithm>을 선언해야한다.
*/

#include <vector>
#include <iostream>

using namespace std;

vector<int> solution(vector<int> arr) 
{
    vector<int> answer;
    int a =0;
   while(a<arr.size()-1)
   {
       if(arr[a] != arr[a+1])
           answer.push_back(arr[a]);
    a= a+1;
   }
    answer.push_back(arr[arr.size()-1]);
    return answer;
}
```

```C++
/*
2021/02/06
3진법 뒤집기
자연수n이 있을때 n을 3진법으로 변환 후 뒤집은 후 이를 다시 10진법으로
표현한 수를 return하는 문제이다.
나는 이렇게 풀었지만
다른사람의 코드를 보면
마지막에 10진법을 구할때
벡터의 pop_back()을 쓰는 것을 봤다.
훨씬 간편해보였다.
*/

#include <string>
#include <vector>
#include <math.h>
using namespace std;

int solution(int n) {
    int answer = 0;
    vector <int> three;
    while(1)
    {
        if(n < 3)
        {
            three.push_back(n);
            break;
        }
        three.push_back(n%3);
        n = n/3;
    }
    for (int a = 0, b = three.size() - 1; a < three.size(); a++, b--)
    {
        answer += three[a] * pow(3,b);
    }
        
    return answer;
}
```

```C++
/*
2021/02/06
가운데 글자 가져오기
단어 s의 가운데 글자를 반환하는 함수를 구현한다.
단어의 길이가 짝수라면 두글자를 반환한다.
*/
#include <string>
#include <vector>

using namespace std;

string solution(string s) {
    string answer = "";
    int len = s.size();
    if(len%2 == 0)
        answer += s.substr(len/2-1,2);
    else
        answer += s.substr(len/2,1);
    return answer;
}
```
```C++
/*
2021/02/06
2016년
2016년 1월1일은 금요일일때
a월 b일은 무슨 요일인지 구하는 문제이다
벡터로 풀었다.
각 개월의 요일수를 포함하는 벡터
무슨 요일인지 구하는 벡터를 선언하여
1주일은 7일 인것을 이용하여 나머지를 구하여 해당하는
인덱스를 정답으로 리턴하였다.
*/
#include <string>
#include <vector>

using namespace std;

string solution(int a, int b) {
    string answer = "";
    int mon=0;
    int day =0;
    vector <int> year = {31,29,31,30,31,30,31,31,30,31,30,31};
    vector <string> an = {"THU","FRI","SAT","SUN","MON","TUE","WED"};
    for(int i = 0; i<a-1; i++)
        mon += year[i];
    mon = mon + b;
    day = mon % 7;
    answer = an[day];
    return answer;
}
```
```C++
/*
2021/02/06
두 개 뽑아서 더하기
정수 배열에서 서로 다른 인덱스에 있는 두개의 수를 뽑아
더해서 만들 수 있는 모든 수를 배열에 오름차순으로 담는다.
여기서 중복된 수는 없고
오름차순이라는 것이 문제를 푸는데 가장 큰 힌트였다.
set을 이용하여 풀었는데set은 중복된 수를 없애주고 오름차순으로 정렬을 해준다.
*/
#include <string>
#include <vector>
#include <set>
using namespace std;
//set의 특징은 중복이 없고 오름차순으로 정렬이 자동으로 된다.
vector<int> solution(vector<int> numbers) {
    vector<int> answer;
    set<int> c;
    for(int a =0; a< numbers.size(); a++)
    {
        for(int b = a+1; b< numbers.size(); b++)
        {
            c.insert(numbers[a]+numbers[b]);
        }
    }
    for(auto a: c)
    {
        answer.push_back(a);
    }
    
    return answer;
}
```


```C++
/*
2021/02/05
가장 큰 수(정렬)
0또는 양의 정수가 주어졌을 떄 이어붙여 만들 수 있는 가장 큰수를 반환하는 문제이다.
6,10,2가 주어지면
6102,6210,1062,1026,2610,2106을 만들 수 있고, 이중 가장 큰 수는 6210이다.

반복문을 돌면서 첫번째 자리수가 가장큰 수를 골라내면서 답을 완성하려고 했다.
만약 가장 큰 첫번째 숫자가 중복된다면 두번쨰 자리수를 비교, 세번째 자리수를 비교하여 반환하려고 했다.
하지만 구현이 쉽지 않았고 해야할 예외처리가 너무 많았다. 가령 1000과 0이라든지 세자리수와 한자리수의
비교가 예로 들 수있다. 한참 고민하다 구글링해서 해법을 알아냈는데
string 벡터를 만들고 값을 넣고 sort를 해주는 것까진 비슷했지만 cmp함수의 사용 여부였다.
cmp는 a+b > b+a 일때 true를 반환하는 함수다. 이해가 가지않아 디버깅을 하며 노트에 과정을 적어가며 습득했다. 
쉽게 말하면 a+b > b+a가 참일때 a와 b의 자리를 바꾼다. 만약 중간에 false인 조건을 만나게 되면
앞쪽 정렬이 된 상태의 숫자중 제일 뒤 즉, false일때 a의 왼쪽 숫자가 b가 되며 왼쪽으로 b가 바뀌면서 비교를 한다.
중간에 알맞은 자리를 찾으면 그 숫자와 자리 교환을 하는 방식이다. 꽤나 어려운 문제였고 코딩테스트에 요긴하게 사용할 것 같다.

*/
//////////////가장 큰 수/////////////////
#include <string>
#include <vector>
#include <iostream>
#include <algorithm>
using namespace std;
///string -> int  : stoi()
// int -> string  : to_string()
bool cmp(string a, string b)
{
    return a + b > b + a;
    //a+b>b+a가 참일때만 swap
}
string solution(vector<int> numbers) {
    string answer = "";

    vector<string> s_num;
    for (auto it : numbers)
        s_num.push_back(to_string(it));
    sort(s_num.begin(), s_num.end(),cmp);


    if (s_num[0] == "0")
        return "0";
    for (auto num : s_num)
        answer += num;


    return answer;
}


int main()
{

    vector <int> a = { 3,30,34,5,33,9 };
    string v = solution(a);
    cout << v;


}


```
```C++
/*
2021/02/03
K번쨰수(정렬)
배열의 i번째 숫자부터 j번째 숫자까지 자르고 정렬했을 때 K번째에 있는 수를 구하는 문제이다.
배열, [i,j,k]를 원소로 가진 2차원 배열을 주었을때
연산 결과를 배열에 담아 return한다.

문제는 한두번 읽어보면 쉽게 풀 수있을 만큼 난이도가 높지 않았다.
간단해서 금방 풀었던 문제이다.
처음에는 반복문 하나로 풀었다.
벡터 temp를만들어 array를 복사하고 sort함수 j,k를 인자로 넣어
정렬 시작과 끝을 지정해주고 풀었다.
두번째는 직관적으로 풀었다. 이중 반복문을 이용하였는데,
시작과 끝그리고 배열에 담을 포인트까지 변수로 받고
temp에 잘라서 넣고 temp를 정렬 시킨후 point를 answer에 넣어문제를 해결했다.
*/
/////////////K번째수///////////////
#include <string>
#include <vector>
#include <iostream>
#include <algorithm>
using namespace std;

vector<int> solution(vector<int> array, vector<vector<int>> commands) {
    vector<int> answer;
    for (int a =0; a < commands.size(); a++)
    {
        vector <int> temp;
        int start = commands[a][0]-1;
        int end = commands[a][1]-1;
        int point = commands[a][2]-1;
        for (int b = start; b <= end; b++)
            temp.push_back(array[b]);
        sort(temp.begin(), temp.end());
        answer.push_back(temp[point]);
    }
    return answer;
}

int main()
{
    vector<int> arr = {1,5,2,6,3,7,4};
    vector <int> a = {2,5,3};
    vector <int> b = {4,4,1};
    vector <int> c = {1,7,3};
    vector<vector<int>> d = {a,b,c};
 
    vector <int> sol = solution(arr, d);

    for (auto it : sol)
    {
        cout << it << ' ';
    }
}
```

```C++
/*
2021/02/02
위장(해시)
다른 옷을 조합하여 입을 수 있는 경우의 수를 구하는 문제이다.
만약
얼굴 - 동그란안경, 검정 선글라스
상의 - 파란색 티셔츠
하의 - 청바지
겉옷 - 긴코드
이렇게 있을때 각 종류마다 골라서 입을 수 있다.
단 아무것도 안입는 경우는 없다.
또한, 하나만 입을 수 있다.

먼저 옷 종류와 종류의 갯수를 나타내는 pair를 이용했다.
각각 종류와 개수를 pair로 담아 2차원 벡터에 담았다.
이 다음이 문제의 포인트이다.
순열을 이용하여 모든 조합의 갯수를 구해야하지만
하나씩 카운팅 하는 것보다 모든 경우의 수를 구해서 뺴면 더욱더 쉬운 문제가 되는것이다.
(옷의 갯수+1) * (옷의 갯수+1) * (옷의 갯수+1) ````(옷의 갯수+1)해주고
마지막에 -1을 해주면 되는데 +1은 입지 않은 경우를 포함 한 것이다. +1을 하는 것이
문제의 핵심이자 제일 어려웠던 부분이였다.
-1은 모두 안입는 경우는 없기에 -1을 해주는 것이다.
벡터를 이용하여 중복체크를 따로 만들어 줘서 그런지
낮은 점수가 나왔다. 다른 사람들은 hash_map을 이용하여 중복제거해주는 함수를 사용했다.
*/
////////////////위장///////////////

#include <string>
#include <vector>
#include <iostream>
#include <utility>
using namespace std;

int solution(vector<vector<string>> clothes) {
    int answer = 1;
    vector <pair<string, int>> count;//옷종류, 갯수 저장할 2차 벡터
    
    for (int a = 0; a < clothes.size(); a++)
    {//pair에 옷 종류랑 갯수 벡터에 푸쉬백 같을 경우 예외 처리
        string temp = clothes[a][1];
        int flag = 0;
        int num = 0;
        for (int c = 0; c < count.size(); c++)
        {//2차벡터에 중복되는 종류 체크
            if (temp == count[c].first)
                flag = 1;//flag로 분별
        }
        if (flag == 1)
            continue;
        for (int b = a; b < clothes.size(); b++)
        {//옷 종류의 갯수 늘려주기
            if (temp == clothes[b][1])
                num++;
        }
        pair<string, int> p = make_pair(temp, num);//종류,갯수 페어
        count.push_back(p);//푸쉬! 
    }
    for (int a = 0; a < count.size(); a++)
    {//벡터를 돌면서 정답에 조랍의 갯수를 적어준다.
        answer *= (count[a].second + 1);
    }//+1 은안입는 경우를 더한 것이다. 이부분 어려웠음
    /*
        만약 A,B,C의 종류가 있다면
        각각 입는 경우 + 1을 해주어 선택하지 않는
        경우를 고려한다.
    */
    answer = answer - 1;
    //아무 것도 안입는 경우는 없기에
    // 모든 조합중 선택 하지 않는 경우가 있기에 -1로 뺴준다.
    return answer;
}

int main()
{

    vector <string>a;
    vector <string>b;
    vector <string>c;
    vector <vector<string>> d;
    a.push_back("yellow_hat");
    a.push_back("headgear");
    b.push_back("blue_sunglass");
    b.push_back("eyewear");
    c.push_back("green_furban");
    c.push_back("headgear");

    d.push_back(a);
    d.push_back(b);
    d.push_back(c);

    cout << solution(d);

}


```
```C++

/*
2021/01/30
구명보트(탑욕법)
이 문제는 무인도에 갇힌 사람들을 보트를 이용해 구출하는 설정이다.
보트는 두명이 최대로 탈 수 있고 무게 제한도 있다.
사람들의 몸무게가 담긴 배열과 무게 제한을 줬을 때
모두를 구하기 위한 보트 개수의 최솟값을 return 한다.


처음에는 주어진 배열을 2차 for문으로 두명의 몸무게를 더하며 limit에 가장 가까운
두 사람을 보트에 태워 보내는 방식으로 풀었다.
하지만 효율성 테스트, 즉 시간 복잡도에서 모두 실패를 하였다.

두번째로 배열을 정렬하여 무인도에 남아있는 사람이 없을 떄 까지
반복문을 돌며 맨 처음과 끝을 더햐여 무게제한이 넘으면 가장 무거운 사람 혼자
태워 보내고 넘지 않으면 두명을 태워 보내는 방식으로 풀었다.
하지면 역시 효율성 테스트에서 실패를 했고 벡터의 erase()가 원인 인것을 알았다.

세번째로 위와 같은 방식으로 진행하되 벡터를 지우지 않고 head와 tail를 한칸을 이동하여
보트의 갯수를 세어주는 것으로 진행하였다.


직관적으로 보트를 태워보내는 즉 배열의 원소를 지우는 것에 집착했던것 같다.
문제는 보트의 개수를 구하는 것을 간과했다. 좀 더 효율적으로 문제를 푸는 방법을
배웠던 문제이다. 문제 난이도는 쉬웠다.
*/
/////////구명보트/////////1번 풀이
//#include <vector>
//#include <iostream>
//using namespace std;
//
//int solution(vector<int> people, int limit) {
//	int answer = 0;
//	int sit = 0;
//	for (int a = 0; a < people.size(); a++)
//	{
//		if (people[a] == 0)
//			continue;
//		int temp = limit;
//		for (int b = a + 1; b < people.size(); b++)
//		{
//			if (people[b] == 0)
//				continue;
//			if (people[a] + people[b] <= limit)
//			{
//				if (temp > limit - (people[a] + people[b]))
//				{
//					temp = limit - (people[a] + people[b]);
//					sit = b;
//				}
//			}
//		}
//		if (temp == limit)
//		{
//			people[a] = 0;
//			answer++;
//		}
//		else
//		{
//			people[a] = 0;
//			people[sit] = 0;
//			answer++;
//		}
//	}
//	return answer;
//}
//////////////구명보트///////2번 풀이
//
//#include <string>
//#include <vector>
//#include <iostream>
//#include <algorithm>
//using namespace std;
//
//int solution(vector<int> people, int limit) {
//	int answer = 0;
//	sort(people.begin(), people.end());
//	reverse(people.begin(), people.end());
//	while (people.size())
//	{
//		if (people.size() == 1)
//		{
//			answer++;
//			return answer;
//		}
//		if (people.front() + people.back() <= limit)
//		{
//			people.erase(people.begin());
//			people.erase(people.begin() + people.size()-1);
//			answer++;
//		}
//		else
//		{
//			people.erase(people.begin());
//			answer++;
//		}
//	}
//	return answer;
//}


#include <string>
#include <vector>
#include <iostream>
#include <algorithm>
using namespace std;

int solution(vector<int> people, int limit) {
	int answer = 0;
	int head = 0; 
	int tail = people.size() - 1;
	sort(people.begin(), people.end());
	reverse(people.begin(), people.end());
	while (head < tail)
	{
		if (people[head] + people[tail] > limit)
		{
			head++;
			answer++;
		}
		else
		{
			head++;
			tail--;
			answer++;
		}
	}
	if (head == tail)
	{
		answer++;
	}
	return answer++;

}

int main()
{
	vector <int> a;
	a.push_back(70);
	a.push_back(50);
	a.push_back(80);
	a.push_back(50);
	//a.push_back(50);
	//a.push_back(40);
	cout << solution(a, 100) << endl;

}


```

![ㅇㄹㄴ](https://user-images.githubusercontent.com/45708825/99902850-16c41380-2d04-11eb-949b-a72675f16917.jpg)

```C++
/*
2020/11/22
타겟 넘버(dfs/bfs)
이 문제는 n개의 음이 아닌 정수가 있을때
이 수를 적절히 더하거나 빼서 타겟의 넘버와 일치하는 경우의 수를 구하는 것이다.
알고리즘으로는 dfs를 써서 구현했다.
dfs는 깊이 탐색으로 노드의 끝까지 탐색하는 방법이다.
dfs를 이해하고자 디버깅을 해보고 손으로 값을 적어가면서 해봤지만 쉽지 않았다.
결국 이해를 하고자 노드를 그려 표현하며 이해를 했다. 생각보다 정말 간단하지만
코드로 이해하기엔 쉽지 않는 것 같다.
내가 이해한 노드는 위과 같다.
만약 [a,b,c,d,e]라는 숫자가 있다고 가정한다.
+a+b+c+d+e까지 와서 값을 비교하고 -e로 간다. 그 후 -d로 가서 같은 과정을 반복한다.
이로써 dfs에 대한 이해가 한 층 깊어졌다.
다른 문제와는 다르게 코드가 문제보다 쉬운 것 같다.
*/

#include <string>
#include <vector>
#include <iostream>


using namespace std;
int answer = 0;
void dfs(vector<int> numbers, int target, int sum, int count)
{
    if (count == numbers.size())
    { 
        if (sum == target)
        {
            answer++;
           
        }
        return;
    }
    dfs(numbers, target, sum + numbers[count], count+1);
    dfs(numbers, target, sum - numbers[count], count+1);
}

int solution(vector<int> numbers, int target) {

    dfs(numbers, target, 0, 0);
    return answer;
}

int main()
{
    vector <int> dfs;
    dfs.push_back(1);
    dfs.push_back(2);
    dfs.push_back(3);
    dfs.push_back(4);
    dfs.push_back(5);

    int a = solution(dfs, 5);
    cout << a;

}
```

```C++
/*
2020/11/21
소수찾기(완전탐색)
이 문제는 낱개의 숫자 조각들로 소수를 몇개 만들 수 있는지 알아내는 문제이다.
numbers는 각각의 숫자들이 적혀있는 문자열이다.

크게 가능한 모든 숫자 조합을 만드는 순열조합과 소수를 찾아 문제를 풀었다.
소수를 찾는 함수는 따로 빼두었다.
문자는 모든 조함으로 벡터에 삽입하여 중복된 숫자를 제거했다
next_permutation()이라는 함수는 문제를 해결하다가 찾은 함수이다.
순열을 찾아주는 함수다. 앞으로도 유용하게 쓰일것 같다.
먼저 char의 각 숫자에 아스키 코드를 뺀 값을 벡터에 삽입하였다.
그리고 2중 포문으로 모든 숫자 조합을 찾았다.
밖의 포문은 자리수가 되고 안의 포문은 각자리수의 순열을 찾는 반복문이다.
찾은 순열은 unique()함수로 중복된 숫자들을 제거했다. 제거하는 이유는 카운터가 중복되기 때문이다.
또한, unique()함수도 이 문제를 풀면서 알게 되었다.
메모를 하자면 v.erase(unique(v.begin(), v.end()), v.end());
이런식으로 사용한다.
마지막으로 중복을 제거한 숫자들을 미리 빼놓은 소수 찾는 함수를 거쳐 answer의 카운터를
올려주는 것으로 마무리를 하였다.
*/
#include <iostream>
#include <vector>
#include <algorithm>
#include <string>
#include <cmath>
using namespace std;
bool Isprime(int p);
int solution(string numbers)
{
    int answer = 0;
    vector<int> num;
    for (int a = 0; a < numbers.size(); a++)
    {
        num.push_back(numbers[a]-'0');
    }
    sort(num.begin(), num.end());
    vector<int>r_num;
    do{
        for (int a = 0; a <= num.size(); a++)
        {
            int temp = 0;
            for (int b = 0; b < a; b++)
            {
                temp = temp * 10 + num[b];
                r_num.push_back(temp);
            }

        }
  
    }while (next_permutation(num.begin(), num.end()));
    sort(r_num.begin(), r_num.end());
    r_num.erase(unique(r_num.begin(), r_num.end()), r_num.end());

    for (int a = 0; a < r_num.size(); a++)
    {
        if (Isprime(r_num[a]) == true)
            answer++;
    }

    return answer;
}
bool Isprime(int p)
{
    if (p < 2)
        return false;
    for (int a = 2; a*a <= p; a++)
    {
        if ((p % a) == 0)
            return false;
    }
    return true;
}
int main()
{
    cout <<solution("1234");
}
```


```C++
/*
2020/11/18
조이스틱(탐욕 알고리즘)
이 문제는 조이스틱으로 원하는 문자열을 만드는 문제이다.
조이스틱은 총 4가지의 방향으로 움직일수 있고 움직였을때 커맨드는 다음과 같다.
위 - 다음 알파벳
아래 - 이전 알파벳 (A에서 아래로 이동하면 Z)
왼 - 커서를 왼쪽으로 이동(첫 번째 위치에서 왼쪽으로 이동하면 마지막 문자에 커서)
오 - 커서를 오른쪽으로 이동

문자는 "A" x name.size()로 초기화 되어있다.
이름이 세 글자면 AAA, 네 글자면 AAAA이다.
위 와 같은 조건으로 조이스틱의 최소 조작 횟수를 반환하는 문제이다.
ex)
name = JAZ
- 첫 번쨰 위치에서 위로 9번 올려 J를 완성 --> +9
- 왼쪽으로 1번 조작하여 마지막 위치로 이동 --> +1
- 마지막 위치에서 아래로 1번 조작하여 Z를 완성 --> +1
answer == 11

생각보다 너무 어려웠던 문제이다.
테스트 케이스 3, 5, 11번을 끝내 맞추지 못하였다.
결국 다른 사람의 코드를 참고하였다.

나는 위 아래와 왼쪽 오른쪽을 따로 계산하여 값을 더해주는 방식으로 구현하였다.
위아래는 알파벳의 중간인 'N' 기준으로 작으면 아래로 움직이고 크면 올리는 방식이다.
왼쪽 오른쪽은 각각 A를 제외한 알파벳의 순서를 카운팅하여 왼쪽과 오른쪽을 비교하여 어느쪽으로 가는 것이 빠른지 계산하여 진행하였다.
하지만 생각보다 케이스가 자꾸 나왔고, 그때마다 코드를 추가해주니 코드가 더러워졌다.
*/

//////나의 코드////////////
#include <string>
#include <vector>
#include <iostream>
using namespace std;

int solution(string name) {
	int answer = 0;
	int a_count = 0, b_count = 0;
	for (int a = 0; a < name.size()-1; a++)
	{
		if (name[a] != 'A')
		{
			a_count++;
		}

	}
	for (int b = name.size() - 1; b > 0; b--)
	{

		if (name[b] != 'A')
		{
			b_count++;
		}
	}

	for (int a = 0; a < name.size(); a++)
	{
		if (name[a] > 'N')
		{
			answer += 'Z' - name[a] + 1;
		}
		else
		{
			answer += name[a] - 'A';
		}

	}
	if (a_count > b_count)
	{
		if (b_count != 0)
			answer += name.size() - 1;
	}
	else
	{
		int flag = 0;
		int A_count = 0;
		for (int a = 1; a < name.size(); a++)
		{
			if (a == name.size() - 2)
				break;
			if (name[a] == 'A')
				if (name[a + 1] != 'A')
				{
					flag = 1;
					A_count = a;
					break;
				}
			
		}
		if (flag == 1)
		{
			for (int a = name.size() - 1; a > A_count; a--)
			{
				answer++;
			}
		}
		else
		{
			if (a_count > 1 && b_count > 1)
			{
				answer += name.size() - 1;
			}
			else
				answer += b_count;
		}
			
		
	}

	return answer;
}



//////////////////////////////다른 사람의 코드 참고(멍청한 토끼님 : https://mungto.tistory.com/44)////
#include <string>
#include <vector>
#include <iostream>
using namespace std;
int solution(string name) {
	int answer = 0, i = 0;
	//A로 구성된 화면
	string temp(name.length(), 'A');
	while (true)
	{
		//바꾸고 있는 화면에 반영하고
		temp[i] = name[i];
		//둘중에 적은걸로 결과에 추가하기
		if (name[i] > 'N')
			answer += 'Z' - name[i] + 1;
		else
			answer += name[i] - 'A';
		//바꾼후 문자열이 동일하다면 계산 종료
		if (temp == name)
			break;
		//왼쪽으로 갈지 오른쪽으로 갈지 계산하기 
		for (int move = 1; move < name.length(); move++)
		{
			//오른쪽 이동이 빠르다면 오른쪽으로 이동하고 이동횟수 반영
			if (name[(i + move) % name.length()] != temp[(i + move) % name.length()])
			{
				i = (i + move) % name.length();
				answer += move;
				break;
			}
			//왼쪽으로 이동이 빠르다면 왼쪽으로 이동하고 이동횟수 반영
			else if (name[(i + name.length() - move) % name.length()] != temp[(i + name.length() - move) % name.length()])
			{
				i = (i + name.length() - move) % name.length();
				answer += move;
				break;
			}
		}
	}
	return answer;
}

int main()
{
	string a = "JAZ";
	cout << solution(a) << endl;
}

```



```C++
/*
2020/11/17
큰 수 만들기(탐욕 알고리즘)
number는 숫자들 k는 지우는 숫자의 개수
만약 number에서 k개 만큼의 숫자를 지웠을 떄
나오는 가장 큰 수를 뽑는 문제이다.
예를 들어 number = "1924", k = 2
2개를 지워서 만들 수 있는 수는
19,12,14,92,94,24 이다. 이중에 가장 큰 수는 94이므로 94가 정답이 된다.

min은 number의 개수에서 k개를 뺸 값으로 정답의 자리수가 된다.
maxnum은 가장 큰값이다.
첫 번쨰 포문은 min만큼 돌면서 answer에 한자리씩 값을 삽입하는 포문이다.
안쪽 포문이 핵심이라 생각한다.
정답의 첫번쨰 자리부터 가장 큰값을 뽑는 범위는 뒤쪽에 남아있는 자리수 만큼
확보가 가능한 최대한 범위까지이다. 즉 맨 뒤에있는 숫자가 가장 크다고 해서
첫번째 자리에 올수 없는것이다. 왜냐면 뒤에 오는 숫자가 없기 때문이다.
이 문제를 해결하고자 maxnum에 초기값을 주었고 b는 최대값을 찾는 범위중 맨 처음 자리,
k+a는 최대한의 범위가 되겠다. 오른쪽으로 탐색해가며 현제 저장되어있는 max값보다 값이
클 경우 값을 바꿔준다. 그리고 maxidx는 그 다음 탐색을 즉, start가 가장 큰값 다음부터
다시 포문을 시작하는데 그 위치를 저장해주는 역할을 한다.

*/
#include <string>
#include <vector>

using namespace std;

string solution(string number, int k) {
    string answer = "";

    int min = number.size() - k;
    char Maxnum = number[0];
    int start = 0;

    for (int a = 0; a < min; a++)
    {
        int maxidx = start;
        Maxnum = number[start];
        for (int b = start; b <= k + a; b++)
        {
            if (Maxnum < number[b])
            {
                Maxnum = number[b];
                maxidx = b;
            }
           
        }
        start = maxidx + 1;
        answer += Maxnum;
    }
    return answer;
}
```


```C++

/////////체육복////////////////
/*
2020/11/15 일
탐욕 알고리즘
n은 총 학생의 수
lost는 체육복을 잃어버린 학생들
reserve는 여분의 체육복을 가지고 있는 학생들이다.
여분의 학생들도 체육복을 잃어버릴수 있다. 이런 경우엔 다른 학생에게 체육복을 빌려주지 못한다.
여분의 체육복을 가지고 있는 학생이 잃어버렸는지 먼저 찾아주고 0으로 초기화 시키고 값을 늘려준다.
그리고 -1과 +1의 값을 비교하여 빌려 줄 수 있는 학생을 탐색하고 값을 정리 한 후 반환한다.
이 문제는 break와 continue에 성패가 달렸었다.
break를 하지 않으면 이어서 다른 값을 중복으로 비교 할 수 있기 때문에 연산이 수 차례 일어난다.
또한 continue를 하지 않으면 0의 값에 -1과 +1을 더한 값을 탐색하기 때문에 예외 처리해주었다.

*/
#include <string>
#include <vector>
#include <iostream>
using namespace std;

int solution(int n, vector<int> lost, vector<int> reserve) {
    int answer = 0;
    int ss = 0;
    
    for (int a = 0; a < lost.size(); a++)
    {
        for (int b = 0; b < reserve.size(); b++)
        {
            if (lost[a] == reserve[b])
            {
                lost[a] = 0;
                reserve[b] = 0;
                ss++;
                break;
            }
        }
    }

    for (int a = 0; a < lost.size(); a++)
    {
        if (lost[a] == 0)
            continue;
        for (int b = 0; b < reserve.size(); b++)
        {
            if (reserve[b] == 0)
                continue;
            if (lost[a] - 1 == reserve[b] || lost[a] + 1 == reserve[b])
            {
                lost[a] = 0;
                reserve[b] = 0;
                ss++;
                break;
            }
        }
    }
    answer = n-lost.size() + ss;
    return answer;
}
```






```C++
///////////크레인인형뽑기게임////////////////////////////////////////////////////////

#include <string>
#include <vector>
#include <stack>
#include <queue>
#include <iostream>

using namespace std;

int solution(vector<vector<int>> board, vector<int> moves) {
    int answer = 0;
    vector <int> list;
    for (int a = 0; a < moves.size(); a++)
    {
        for (int b = 0; b < board[0].size(); b++)
        {
           if(board[b][moves[a]-1] == 0)
               continue;
           else
           {
               list.push_back(board[b][moves[a] - 1]);
               board[b][moves[a] - 1] = 0;
               break;
           }
        }
        for (int c = list.size(); c>0; c--)
        {
            if (list.size() == 1)
                break;
            else
            {
                if (c == 1)
                    break;
                if (list[c- 1] == list[c - 1 - 1])
                {
                    list.pop_back();
                    answer++;
                    list.pop_back();
                    answer++;
                    break;
                }
            }
        }
    }
    return answer;
}
int main()
{
    vector <int>a1;
    vector <int>a2;
    vector <int>a3;
    vector <int>a4;
    vector <int>a5;
    vector <int> m;
    vector<vector< int >> list  ;
    a1.push_back(0);
    a1.push_back(0);
    a1.push_back(0);
    a1.push_back(0);
    a1.push_back(0);

    a2.push_back(0);
    a2.push_back(0);
    a2.push_back(1);
    a2.push_back(0);
    a2.push_back(3);

    a3.push_back(0);
    a3.push_back(2);
    a3.push_back(5);
    a3.push_back(0);
    a3.push_back(1);

    a4.push_back(4);
    a4.push_back(2);
    a4.push_back(4);
    a4.push_back(4);
    a4.push_back(2);

    a5.push_back(3);
    a5.push_back(5);
    a5.push_back(1);
    a5.push_back(3);
    a5.push_back(1);

    list.push_back(a1);
    list.push_back(a2);
    list.push_back(a3);
    list.push_back(a4);
    list.push_back(a5);

    m.push_back(1);
    m.push_back(5);
    m.push_back(3);
    m.push_back(5);
    m.push_back(1);
    m.push_back(2);
    m.push_back(1);
    m.push_back(4);
 
    int ff = solution(list, m);
    cout << ff; 
}
```


```C++
//////////////////////모의고사////////////////////////////////////////////////
#include <string>
#include <vector>
#include <algorithm>
using namespace std;

vector<int> solution(vector<int> answers) {
	vector<int> answer;
	vector<int> count;

	int arr1[5] = { 1,2,3,4,5 };
	int arr2[8] = { 2,1,2,3,2,4,2,5 };
	int arr3[10] = { 3,3,1,1,2,2,4,4,5,5 };

	int score[3] = { 0, };
	int max_score = 0;
	for (int i = 0; i < answers.size(); i++) {
		if (answers[i] == arr1[i % 5]) score[0] += 1;
		if (answers[i] == arr2[i % 8]) score[1] += 1;
		if (answers[i] == arr3[i % 10]) score[2] += 1;
	}
	max_score = max(max(score[0], score[1]), score[2]);
	for (int i = 0; i < 3; i++) {
		if (score[i] == max_score)
			answer.push_back(i + 1);
	}
	return answer;
}

int main()
{
	vector<int> a;
	a.push_back(1);
	a.push_back(2);
	a.push_back(3);
	a.push_back(4);
	a.push_back(5);
	vector<int> b;
	b = solution(a);

}
```

```C++
///////////////////다리를 지나는 트럭///////////////////////
//https:/mungto.tistory.com/4 출처
#include <string>
#include <vector>
#include <queue>
#include <algorithm>
#include <iostream>
using namespace std;

int solution(int bridge_length, int weight, vector<int> truck_weights) {
	int answer = 0;//경과 시간
	int cuweight = 0;//현재 도로에 올라가있는 차 무게
	queue <int> on; //차마다 남은 거리
	queue<int> count; //도로에 올라가있는 차
	while (true)
	{
		int size = on.size();//차가 빠져나가면 계산이 바뀌니까 고정
		for (int a = 0; a < size; a++)
		{
			int len = on.front();
			on.pop();
			if (len <= 1)//도로 남은 길이가 없다면
			{
				cuweight -= count.front();
				count.pop();
				continue;
			}
			on.push(len - 1);
		}
		if (truck_weights.size() > 0 && cuweight + truck_weights.at(0) <= weight)
		{
			count.push(truck_weights.at(0));
			cuweight += truck_weights.at(0);
			on.push(bridge_length);
			truck_weights.erase(truck_weights.begin());
		}
		answer++;
		if (truck_weights.size() == 0 && count.size() == 0)
			break;

	}
	return answer;
}
void print(int bridge_length, int weight, vector<int> truck_weights, int answer) {
	int t = solution(bridge_length, weight, truck_weights);
	cout << t << " , ";
	if (t == answer)
		cout << "정답" << endl;
	else
		cout << "틀림" << endl;
}

int main() {
	print(100, 100, { 10,10,10,10,10,10,10,10,10,10 }, 110);
	print(2, 10, { 7,4,5,6 }, 8);
	print(100, 100, { 10 }, 101);

	return 0;
}
```



```C++
///////////////////////////프린터//////////////////////////
//#include <string>
//#include <vector>
//#include <iostream>
//#include <algorithm>
//#include <queue>

//using namespace std;

//int solution(vector<int> priorities, int location)
//{
//	priority_queue <int> q;
//	queue <pair<int, int>> qp;
//	int answer = 0;
	
//	for (int a = 0; a < priorities.size(); a++)
//	{
//		q.push(priorities[a]);
//		qp.push(make_pair(priorities[a], a));
//	}
//	while (!qp.empty())
//	{
//		int num = qp.front().first;
//		int lo = qp.front().second;
//		qp.pop();
		
//		if (num == q.top())
//		{
//			q.pop();
//			answer++;
//			if (lo == location)
//				break;
//		}
//		else
//		{
//			qp.push(make_pair(num, lo));
//		}
//	}
//	return answer;
//}
#include <string>
#include <vector>
#include <iostream>
#include <algorithm>
using namespace std;

int solution(vector <int> priorities, int location)
{
    int answer = 0;
    int temp = 0;
    int max_num = 0;
    int lo = 0;
    int flag = 0;
    while(!priorities.empty())
    {
        temp = priorities.front();
        max_num = *max_element(priorities.begin(), priorities.end());
        priorities.erase(priorities.begin());
        if(location ==0)
        {
            if (temp == max_num)
            {
                if (answer == 0)
                    answer++;
                break;
            }
            else
            {
                priorities.push_back(temp);
                location = location + priorities.size() - 1;
                for (int b = 0; b < priorities.size(); b++)
                {
                    if (priorities[b] == max_num)
                    {  
                        priorities.erase(priorities.begin() + b);
                        answer++;
                        location--;
                        break;
                    }
                }
            }
        }
        else
        {//lo !=0 
            location--;
            if (temp == max_num)
            {
                answer++;
            }
            else
            {
                if (priorities[location] == max_num)
                {
                    answer++;
                    break;
                }
                priorities.push_back(temp);
                for (int b = 0; b < priorities.size(); b++)
                {
                    if (b == location)
                        flag = 1;
                    if (priorities[b] == max_num)
                    {
                        priorities.erase(priorities.begin() + b);
                        if (flag == 0)
                            location--;    
                        answer++;                       
                        break;
                    }
                }
                flag = 0;
            }
        }
    }
    return answer;
}

int main()
{
    vector<int> a;

    a.push_back(1);
    a.push_back(1);
    a.push_back(1);
    a.push_back(1);

    int z = solution(a, 0);
    cout << z;
}

```
```C++
//////////////////123 나라의 숫자/////////////////
#include <string>
#include <vector>
#include <iostream>
using namespace std;

string solution(int n) {
    string answer = "";
    while (n!= 0)
    {
        if (n % 3 == 0)
        {
            answer.insert(0, "4");
            n = n / 3 - 1;
        }
        else
        {
            answer.insert(0, to_string(n % 3));
            n = n / 3;
        }
    }
    return answer;
}
int main()
{
    string a;
    a = solution(1000);
    cout << a;
}
```

```C++
////////////////////문자열 압축////////////
#include <string>
#include <vector>
#include <iostream>
#include <algorithm>
using namespace std;

int solution(string s) {
    int answer = 0;
    int count = 0;

    vector <int> max;
    for (int a = 1; a <= s.size() / 2 + 1; a++)
    {//자르는 갯수
        string comp;
        vector <string> r;
        count = 0;
        for (int b = 0; b < s.size(); b++)
        {//문자열 자르기
            if (b * a + a > s.size())
            {
                count = s.size() - r.size() * a;
                break;
            }
            comp = s.substr(b * a, a);
            r.push_back(comp);
        }
        int r_size = r.size();
        int z_size = r.size();
        int flag = 0;
        int mul = 0;
        string temp;
        for (int c = 0; c < r_size; c++)
        {
            if (c + 1 >= r_size)
                break;
            if (temp == r[c + 1])
            {
                z_size--;
            }
            else if (r[c] == r[c + 1])
            {
                z_size--;
                count++;
                temp = r[c];
            }
            else
            {
                temp = "";
            }
        }
        max.push_back(z_size * a + count - mul);
    }
    answer = *min_element(max.begin(), max.end());
    return answer;
}
int main()
{
    string s = "BBAABAAAAB";
    int a = solution(s);
    cout << a;


}
```
```C++
/////////////////////괄호 변환/////////////////////////////
#include <string>
#include <vector>
#include <iostream>

using namespace std;
string saperate_2_u(string p)
{
	int left = 0;
	int right = 0;
	int a = 0;
	string re;
	for (a = 0; a < p.size(); a++)
	{
		if (left == right && left != 0)
			break;
		else if (p[a] == '(')
			right++;
		else if (p[a] == ')')
			left++;
	}
	for (int b = 0; b < left + right; b++)
	{
		re += p[b];
	}
	return re;
}
string saperate_2_v(string u, string p)
{
	string v;
	if (u == p)
	{
		v = "";
		return v;
	}
	v = p.substr(u.size(), p.size());
	return v;
}
bool right_string(string u)
{
	int left = 0;
	int right = 0;
	for (int a = 0; a < u.length(); a++)
	{
		if (u[a] == '(')
			right++;
		else if (u[a] == ')')
			right--;
		if (right < 0)
			return false;
	}
	return true;
}
string solution(string p) {
	string answer = "";
	string u, v;
	if (p.empty())//1
		return p;
	if (right_string(p) == true)
	{//string 전체가 옳바른문자열인지 체크
		answer = p;
		return answer;
	}
	else
	{//전체가 옳바르지 않으면
		u = saperate_2_u(p);//2
		v = saperate_2_v(u, p);//2
		if (right_string(u) == true)
		{
			answer += u;
			string temp_u = u;
			string temp_v = v;
			string recul = solution(v);
			answer += recul;
			return answer;
		}
		else if (right_string(u) == false)
		{
			string em;
			string temp;
			em += '(';
			temp = solution(v);
			em += temp;
			em += ')';
			u.erase(u.begin());
			u.pop_back();
			int u_size = u.size();
			for (int z = 0; z < u_size; z++)
			{
				if (u[z] == '(')
					u[z] = ')';
				else if (u[z] == ')')
					u[z] = '(';
				em += u[z];
			}
			answer += em;
		}
	}
	return answer;
}
int main()
{
	string p = "()))((()";
	p = solution(p);
	cout << p;

}
```

```C++
/////오픈채팅방////////
#define _CRT_SECURE_NO_WARNINGS
#include <string>
#include <vector>
#include <iostream>
#include <algorithm>
#include <sstream>
#include <map>

using namespace std;

vector<string> solution(vector<string> record) {
    vector<string> answer;
    vector <string> temp;
    stringstream ss;
    string command, u_id, name;
    map <string, string> nick_name;
    for (int a = 0; a < record.size(); a++)
    {
        ss.str(record[a]);
        ss >> command;
        if (command == "Enter")
        {
            ss >> u_id;
            ss >> name;
            answer.push_back("님이 들어왔습니다.");
            temp.push_back(u_id);
            nick_name[u_id] = name;
        }
        else if (command == "Leave")
        {
            ss >> u_id;
            answer.push_back("님이 나갔습니다.");
            temp.push_back(u_id);
        }
        else
        {//change
            ss >> u_id;
            ss >> name;
            nick_name[u_id] = name;
        }
        ss.clear();
    }
    for (int a = 0; a < temp.size(); a++)
    {
        answer[a] = nick_name[temp[a]] + answer[a];
    }
        return answer;

}
vector<string> solution(vector<string> record) {

    vector<string> answer;
    vector <string> command;
    vector<string> u_id;
    vector<string> nickname;
    vector<string> enter;
    stringstream ss;
    ss.str("abc def");
    string actopm;
    string def;
    string ghi;
    ss >> actopm;
    ss >> def;
    ss >> ghi;
    for (int b = 0; b < record.size(); b++)
    {
        command.push_back("");
        u_id.push_back("");
        nickname.push_back("");
        enter.push_back("");
    }
    for (int a = 0; a < record.size(); a++)
    {
        int flag = 0;
        string temp = record[a];
        char str[MAXSIZE];
        strcpy(str, temp.c_str());
        auto *ptr = strtok(str, " ");
        command[a] = string(ptr);
        u_id[a] = string (ptr = strtok(NULL, " "));
        ptr = strtok(NULL, " ");
        if (ptr != NULL)
            nickname[a] = string(ptr);
        if (command[a] == "Enter")
        {
            enter[a] = u_id[a];
        }
        else if (command[a] == "Leave")
        {
            for (int b = 0; b < u_id.size(); b++)
            {
                if (u_id[b] == u_id[a])
                {
                    u_id[b] = "";
                    flag = 1;
                    break;
                }
            }
        }
    }


        return answer;
}
int main()
{
    vector <string> aa;
    vector <string> re;
    re.push_back("Enter uid1234 Muzi");
    re.push_back("Enter uid4567 Prodo");
    re.push_back("Leave uid1234");
    re.push_back("Enter uid1234 Prodo");
    re.push_back("Change uid4567 Ryan");

    aa = solution(re);

}

```
```C++
/////////자물쇠와 열쇠/////////////
#include <string>
#include <vector>

using namespace std;
bool t_f(vector<vector<int>> key, vector<vector<int>> board)
{
    for (int a = 0; a < board.size()-2; a++)
    {
        for (int b = 0; b < board.size()-2; b++)
        {
            board[a][b] = key[a]
        }

    }
}
bool solution(vector<vector<int>> key, vector<vector<int>> lock) {
   
    int board_size = lock.size() + (key.size() - 1) * 2;
    int key_s = key.size();
    int lock_s = lock.size();
    vector <vector<int>> board(board_size,vector<int>(board_size,0));
    for (int a = key_s-1; a <= board_size - key_s; a++)
    {
        for (int b = key_s-1; b <= board_size - key_s; b++)
        {
            board[a][b] = lock[a - key_s + 1][b - key_s + 1];
        }
    }
    
    
    
    
    bool answer = true;
    return answer;
}

int main()
{
    vector<vector<int>> key(3,vector <int>(3)), lock(3,vector<int>(3));
    key[0].push_back(0);
    key[0].push_back(0);
    key[0].push_back(0);

    key[1].push_back(1);
    key[1].push_back(0);
    key[1].push_back(0);

    key[2].push_back(0);
    key[2].push_back(1);
    key[2].push_back(0);

    lock[0].push_back(1);
    lock[0].push_back(1);
    lock[0].push_back(1);

    lock[1].push_back(1);
    lock[1].push_back(1);
    lock[1].push_back(0);

    lock[2].push_back(1);
    lock[2].push_back(0);
    lock[2].push_back(1);

    bool a = solution(key, lock);

}
```

```C++
////////////////실패율////////////////////////
#include <string>
#include <vector>
#include <map>
#include <iostream>
#include <functional>
using namespace std;

vector<int> solution(int N, vector<int> stages) {
    vector<int> answer;
    vector<int> count(N+2,0);
    multimap <double,int,greater<double>>se;
    for (int a = 1; a <= N+1; a++)
    {
        for (int b = 0; b < stages.size(); b++)
        {
            if (stages[b] == a)
            {
                count[a]++;
            }
        }
    }
    for (int a = 1; a < count.size(); a++)
    {
        int ja = count[a];
        int mo = 0;
        for (int b = a; b< count.size(); b++)
        {
            mo += count[b];
        }
        se.insert(make_pair((double)ja / (double)mo,a));
    }
    for (auto iter = se.begin(); iter != se.end(); ++iter)
    {
        if (iter->second > N)
            continue;
        else
        {
            answer.push_back(iter->second);
        }
    }
    return answer;
}

int main()
{

    vector <int> a;

    vector<int> stage;
    stage.push_back(2);
    stage.push_back(1);
    stage.push_back(2);
    stage.push_back(6);
    stage.push_back(2);
    stage.push_back(4);
    stage.push_back(3);
    stage.push_back(3);
    int N = 5;

    a = solution(N, stage);
}
```
```C++
///////////////////////////더 맵게///////////////////////
#include <string>
#include <vector>
#include <algorithm>
#include <iostream>
using namespace std;

int solution(vector<int> scoville, int K) {
    
    int sco = 0;
    int sco_size = scoville.size();
    int answer = 0;
    int a = 0;
    while (!scoville.empty())
    {
        sort(scoville.begin(), scoville.end());
        sco = scoville[0] + (scoville[1] * 2);
        answer++;
        if (sco < K)
        {
            scoville[1] = sco;
            scoville.erase(scoville.begin());
        }
        else
        {
            scoville.erase(scoville.begin());
        }
    }
    return answer;
}
int main()
{
    vector <int> sco;
    sco.push_back(1);
    sco.push_back(2);
    sco.push_back(3);
    sco.push_back(9);
    sco.push_back(10);
    sco.push_back(12);

    int an = solution(sco, 7);
    cout << an;

}
```
```C++
//////////////타겟 넘버///////////////
#include <string>
#include <vector>
#include <iostream>


using namespace std;
int answer = 0;
vector <int> dd;

void dfs(vector<int> numbers, int target, int sum, int count)
{
    if (count == numbers.size())
    {
        if (sum == target)
        {
            answer++;
        }

        return;
    }
    dfs(numbers, target, sum + numbers[count], count + 1);
    dfs(numbers, target, sum - numbers[count], count + 1);
}

int solution(vector<int> numbers, int target) {

    dfs(numbers, target, 0, 0);
    return answer;
}

int main()
{
    vector <int> dfs;
    dfs.push_back(1);
    dfs.push_back(2);
    dfs.push_back(3);
    dfs.push_back(4);
    dfs.push_back(5);

    int a = solution(dfs,5);
    cout << a;

}
```
```C++
///////////////위장/////////////////////
#include <string>
#include <vector>

using namespace std;

int solution(vector<vector<string>> clothes) {
    int answer = 0;
    return answer;
}

#include <string>
#include <vector>
#include <iostream>
using namespace std;

long long solution(int a, int b) {
    long long answer = 0;
    if (a < -10000000 || b < -10000000 || a>10000000 || b>10000000)
        return 0;
    if (a == b)
        return a;
    else
    {
        if (a > b)
        {
            while (1)
            {
                if (b > a)
                    break;
                answer += b++;
            }
        }
        else
        {
            while (1)
            {
                if (a > b)
                    break;
                answer += a++;
            }
        }
    }
    return answer;
}
int main()
{
    long long a = solution(-10, -20);
    cout << a;

}
```
```C++

////////////////카카오코테 프로그래밍1/////////////
//1단계 new_id의 모든 대문자를 대응되는 소문자로 치환합니다.
//2단계 new_id에서 알파벳 소문자, 숫자, 빼기(-), 밑줄(_), 마침표(.)를 제외한 모든 문자를 제거합니다.
//3단계 new_id에서 마침표(.)가 2번 이상 연속된 부분을 하나의 마침표(.)로 치환합니다.
//4단계 new_id에서 마침표(.)가 처음이나 끝에 위치한다면 제거합니다.
//5단계 new_id가 빈 문자열이라면, new_id에 "a"를 대입합니다.
//6단계 new_id의 길이가 16자 이상이면, new_id의 첫 15개의 문자를 제외한 나머지 문자들을 모두 제거합니다.
//만약 제거 후 마침표(.)가 new_id의 끝에 위치한다면 끝에 위치한 마침표(.) 문자를 제거합니다.
//7단계 new_id의 길이가 2자 이하라면, new_id의 마지막 문자를 new_id의 길이가 3이 될 때까지 반복해서 끝에 붙입니다.
#include <string>
#include <vector>
#include <cctype>
#include <algorithm>
#include <iostream>
#include <sstream>
using namespace std;

string level_1(string id)
{
    for (int a = 0; a < id.size(); a++)
    {
        id[a] = tolower(id[a]);
    }
    return id;
}
string level_2(string id)
{
   string temp ;
    for (int a = 0; a < id.size(); a++)
    {
        if (id[a] == 'a' || id[a] == 'b' || id[a] == 'c' || id[a] == 'd'
            || id[a] == 'e' || id[a] == 'f' || id[a] == 'g' || id[a] == 'h'
            || id[a] == 'i' || id[a] == 'j' || id[a] == 'k' || id[a] == 'l'
            || id[a] == 'm' || id[a] == 'n' || id[a] == 'o' || id[a] == 'p'
            || id[a] == 'q' || id[a] == 'r' || id[a] == 's'
            || id[a] == 't' || id[a] == 'u' || id[a] == 'v' || id[a] == 'w'
            || id[a] == 'x' || id[a] == 'y' || id[a] == 'z' || id[a] == '-'
            || id[a] == '_' || id[a] == '.' || id[a] == '1' || id[a] == '2'
            || id[a] == '3' || id[a] == '4' || id[a] == '5' || id[a] == '6'
            || id[a] == '7' || id[a] == '8' || id[a] == '9' || id[a] == '0'
            )
        {
            temp += id[a];
        }
    }
    return temp;
}
string level_3(string id)
{
    int count = 0;
    string temp;
    char b = '.';
    for (int a = 0; a < id.size(); a++)
    {
        if (id[a] == '.')
        {
            count++;
            if (count == 1)
            {
                temp += id[a];
            }
            else
                continue;
        }
        else
        {
            count = 0;
            temp += id[a];
        }
    }
    return temp;
}
string level_4(string id)
{
    int a = id.size();
    if (id[0] == '.')
    {
        id.erase(id.begin());
    }
    if (id[id.size()-1] == '.')
    {
        id.pop_back();
    }
    return id;
}
string level_5(string id)
{
    if (id.size() == 0)
        id += "a";
    return id;
}
string level_6(string id)
{
    if (id.size() >= 16)
    {
        id.erase(15, id.size() - 15);
    }
    if (id[id.size()-1] == '.')
    {
        id.pop_back();
    }
    return id;
}
string level_7(string id)
{
    if (id.size() <= 2)
    {
        while (id.size() != 3)
        {
            id += id[id.size()-1];
        }
    }
    return id;
}
string solution(string new_id) {
    string answer = "";
    new_id = level_1(new_id);
    new_id = level_2(new_id);
    new_id = level_3(new_id);
    new_id = level_4(new_id);
    new_id = level_5(new_id);
    new_id = level_6(new_id);
    new_id = level_7(new_id);
    answer = new_id;
    return answer;
}
int main()
{

    string a = "abcdefghijklmn.p";
    string b = solution(a);
    cout << b;

}
```
```C++
/////////////////////카카오코테 프로그래밍2///////////////
#include <string>
#include <vector>
#include <iostream>
#include <map>
using namespace std;


vector<string> solution(vector<string> orders, vector<int> course) {

    vector<string> answer;
   map<char, int> m;
   map<char, int> ::iterator iter;
   int c = 1;
    for (int a = 0; a < orders.size(); a++)
	{
		int count = 0;
		for (int b = 0; b < orders[a].size(); b++)
		{
			iter = m.find(orders[a][b]);
			if ( iter != m.end())
			{
			   iter->second++;
			}
			else
			{
				m.insert(pair<char, int>(orders[a][b], c));
			}
		}
	}
	for (int a = 0; a < course.size(); a++)
	{
		for (int b = 0; b < course[a]; b++)
		{
			map<char, int> c = m;
			
		}
	}
	return answer;
}
int main()
{

	vector <string> o;
	vector <int> c;
	o.push_back("ABCFG");
	o.push_back("AC");
	o.push_back("CDE");
	o.push_back("ACDE");
	o.push_back("BCFG");
	o.push_back("ACDEH");
	c.push_back(2);
	c.push_back(3);
	c.push_back(4);
	vector<string> s = solution(o, c);

}
```
```C++
	 /////////////////카카오코테 프로그래밍3/////////////
#include <string>
#include <vector>
#include <sstream>
#include <iostream>
using namespace std;

vector<int> solution(vector<string> info, vector<string> query) {
	vector<int> answer;
	stringstream ss;
	string lan, job, cur, food, point, an_d;
	vector <vector <string>> board;
	vector <vector <string>> board1;
	for (int a = 0; a < info.size(); a++)
	{
		vector <string> person;

		ss.str(info[a]);
		ss >> lan;
		person.push_back(lan);
		ss >> job;
		person.push_back(job);
		ss >> cur;
		person.push_back(cur);
		ss >> food;
		person.push_back(food);
		ss >> point;
		person.push_back(point);

		ss.clear();
		board.push_back(person);
	}

	for (int a = 0; a < query.size(); a++)
	{
		vector <string> person;

		ss.str(query[a]);
		ss >> lan;
		person.push_back(lan);
		ss >> an_d;

		ss >> job;
		person.push_back(job);
		ss >> an_d;

		ss >> cur;
		person.push_back(cur);
		ss >> an_d;

		ss >> food;
		person.push_back(food);

		ss >> point;
		person.push_back(point);

		ss.clear();
		board1.push_back(person);
	}
	int count = 0;
	int baord_size = board1.size();
	int baord_size1 = board.size();
	for (int a = 0; a < baord_size; a++)
	{
		for (int b = 0; b < baord_size1; b++)
		{
			if (board1[a][0] == board[b][0] || board1[a][0] == "-")
			{
				if (board1[a][1] == board[b][1] || board1[a][1] == "-")
				{
					if (board1[a][2] == board[b][2] || board1[a][2] == "-")
					{
						if (board1[a][3] == board[b][3] || board1[a][3] == "-")
						{
							int z = 0;
							int y = 0;
							stringstream ssint1(board1[a][4]);
							ssint1 >> z;
							stringstream ssint(board[b][4]);
							ssint >> y;
							if (z <= y)
								count++;
							else
							{
								ssint.clear();
								ssint1.clear();
								continue;
							}
							ssint.clear();
							ssint1.clear();
						}
					}
				}
			}
		}
		answer.push_back(count);
		count = 0;
	}

	return answer;
}
int main()
{
	vector <string> info;
	info.push_back("java backend junior pizza 150");
	info.push_back("python frontend senior chicken 210");
	info.push_back("python frontend senior chicken 150");
	info.push_back("cpp backend senior pizza 260");
	info.push_back("java backend junior chicken 80");
	info.push_back("python backend senior chicken 50");

	vector <string> query;
	//query.push_back("java and backend and junior and pizza 100");
	//query.push_back("python and frontend and senior and chicken 200");
	//query.push_back("cpp and - and senior and pizza 250");
	//query.push_back("- and backend and senior and - 150");
	//query.push_back("- and - and - and chicken 100");
	query.push_back("- and - and - and - 150");

	vector<int> a = solution(info, query);



}
```
```C++
///////////////////////////라인코테 프로그래밍1////////////////////////////

#include <string>
#include <vector>
#include <algorithm>
using namespace std;

int solution(vector<vector<int>> boxes) {
	int answer = -1;
	vector<int>temp;
	for (int a = 0; a < boxes.size(); a++)
	{
		for (int b = 0; b < boxes[a].size(); b++)
		{
			temp.push_back(boxes[a][b]);
		}
	}
	sort(temp.begin(), temp.end());
	int count=0;
	vector<int> t;
	int s = temp.size();
	for (int a = s-1; a >= 0; a--)
	{
		if (count == 1)
		{
			count = 0;
			continue;
		}
		if (temp[a] == temp[a - 1])
		{
			count++;
		}
		else
		{
			t.push_back(temp[a]);
		}
	}
	answer = t.size() / 2;
	return answer;
}
int main()
{
	vector <int> b1;
	b1.push_back(1);
	b1.push_back(2);
	vector <int> b2;
	b2.push_back(2);
	b2.push_back(1);
	vector <int> b3;
	b3.push_back(3);
	b3.push_back(3);
	vector <int> b4;
	b4.push_back(4);
	b4.push_back(5);
	vector <int> b5;
	b5.push_back(5);
	b5.push_back(6);
	vector <int> b6;
	b6.push_back(7);
	b6.push_back(8);
	vector <vector<int>> b;
	b.push_back(b1);
	b.push_back(b2);
	b.push_back(b3);
	b.push_back(b4);
	b.push_back(b5);
	b.push_back(b6);
	int a = solution(b);

}
```
```C++
//////////////////////라인코테 프로그래밍2//////////////
#include <string>
#include <vector>
#include <queue>
using namespace std;

vector<int> solution(vector<int> ball, vector<int> order) {
	vector<int> answer;
	queue <int> wait;
	while (1)
	{
		if (ball.size() == 0)
			break;
		for (int a = 0; a < order.size(); a++)
		{
			if (order[a] == ball[0])
			{
			
				answer.push_back(ball[0]);
				ball.erase(ball.begin());
				break;
			}
			else if (order[a] == ball[ball.size() - 1])
			{
				
				answer.push_back(ball[ball.size()-1]);
				ball.pop_back();
				break;
			}
		}
	}


	return answer;
}
int main()
{

	vector <int> o;
	vector <int> b;
	b.push_back(1);
	b.push_back(2);
	b.push_back(3);
	b.push_back(4);
	b.push_back(5);
	b.push_back(6);

	o.push_back(6);
	o.push_back(2);
	o.push_back(5);
	o.push_back(1);
	o.push_back(4);
	o.push_back(3);
	vector <int> a = solution(b, o);

}
```
```C++
///////라인코테 프로그래밍3///////////////////
#include <string>
#include <vector>
#include <map>
using namespace std;
map<int,int> way_1(string num)
{
	string temp;
	map <int, int> ans;
	int temp_a = 0, temp_b = 0;
	int count = 0;
	while (1)
	{
		if (stoi(num) < 10)
			break;
		for (int a = 1; a < num.size(); a++)
		{
			if (num[a] == '0')
				count++;
			temp += num[a];
		}
		temp_a = num[0] - '0';
		temp_b = stoi(temp);
		num = to_string(temp_a + temp_b);
		temp.clear();
		count++;
	}
	ans.insert(make_pair(count, stoi(num)));
	return ans;
}
map<int, int> way_2(string num)
{
	string temp;
	string temp1;
	map <int, int> ans;
	int temp_a = 0, temp_b = 0;
	int count = 0;
	while (1)
	{
		if (stoi(num) < 10)
			break;
		if (num.size() == 2)
		{
			temp_a = num[0] - '0';
			temp_b = num[1] - '0';
			num = to_string(temp_a + temp_b);
			count++;
		}
		else
		{
			for (int a = 0; a < num.size(); a++)
			{
				if (a <= 1)
				{
					temp1 += num[a];
				}
				else
				{
					temp += num[a];
					if (num[a] == '0')
						count++;
				}

			}
			temp_a = stoi(temp1);
			temp_b = stoi(temp);
			num = to_string(temp_a + temp_b);
			count++;
		}

		temp.clear();
		temp1.clear();

	}
	ans.insert(make_pair(count, stoi(num)));

	return ans;

}
vector<int> solution(int n) {
	vector<int> answer;
	string num = to_string(n);
	map<int, int> w_1 = way_1(num);
	map<int, int> w_2 = way_2(num);
	if (w_1.begin()->first > w_2.begin()->first)
	{
		answer.push_back(w_2.begin()->first);
		answer.push_back(w_2.begin()->second);
	}
	else if (w_1.begin()->first < w_2.begin()->first)
	{
		answer.push_back(w_1.begin()->first);
		answer.push_back(w_1.begin()->second);
	}
	else
	{
		answer.push_back(w_1.begin()->first);
		answer.push_back(w_1.begin()->second);
	}
	return answer;
}
int main()
{
	vector <int> s = solution(10007);
}
```
```C++
///////////////////////라인코테 프로그래밍4////////////////
#include <string>
#include <vector>

using namespace std;

int solution(vector<vector<int>> maze)
{
	int a=0 , b = 0;
	while (1)
	{
		if (a == maze.size() - 1 && b == maze.size() - 1)
			break;
		for()
	}
	int answer = 0;
	return answer;
}

////라인코테 프로그래밍5////////////////////
#include <string>
#include <vector>

using namespace std;

int solution(vector<int> cards) {
    int answer = -1;
    vector <int> p;
    vector <int> d;
    int flow = 0;
    while (1)
    {
        if (cards.size() == 0)
            break;
        for (int a =0; a< )
        p.push_back(cards[flow]);
        d.push_back(cards[flow+1]);

    }

    return answer;
}
```
```C++
/////////////dfs////////////////////////
#include <iostream>
#include <vector>

using namespace std;

int number = 9;
int visit[9];
vector<int> a[10];

void dfs(int start)
{
	if (visit[start])
		return;
	visit[start] = true;
	cout  << start;

	for (int i = 0; i < a[start].size(); i++)
	{
		int x = a[start][i];
		dfs(x);
	}
}
int main()
{
	a[1].push_back(2);
	a[2].push_back(1);

	a[1].push_back(3);
	a[3].push_back(1);

	a[2].push_back(3);
	a[3].push_back(2);

	a[2].push_back(4);
	a[4].push_back(2);

	a[2].push_back(5);
	a[5].push_back(2);

	a[4].push_back(8);
	a[8].push_back(4);

	a[5].push_back(9);
	a[9].push_back(5);

	a[3].push_back(6);
	a[6].push_back(3);

	a[3].push_back(7);
	a[7].push_back(3);

	dfs(1);
}
```
```C++
//////////////////////////bfs//////////////////
#include <iostream>
#include <vector>
#include <queue>

using namespace std;
vector<int> a[10];
int visit[9];


void bfs(int start)
{
	queue <int> q;
	q.push(start);
	visit[start] = 1;

	while (!q.empty())
	{
	
		int x = q.front();
		
		for (int i = 0; i < a[x].size(); i++)
		{
			if (visit[a[x][i]] == 1)
				continue;
			q.push(a[x][i]);
			visit[a[x][i]] = 1;
		}
		cout << q.front();
		visit[x] = 1;
		q.pop();
		

	}
}
int main()
{
	a[1].push_back(2);
	a[2].push_back(1);

	a[1].push_back(3);
	a[3].push_back(1);

	a[2].push_back(3);
	a[3].push_back(2);

	a[2].push_back(4);
	a[4].push_back(2);

	a[2].push_back(5);
	a[5].push_back(2);

	a[4].push_back(8);
	a[8].push_back(4);

	a[5].push_back(9);
	a[9].push_back(5);

	a[3].push_back(6);
	a[6].push_back(3);

	a[3].push_back(7);
	a[7].push_back(3);

	bfs(1);
```



