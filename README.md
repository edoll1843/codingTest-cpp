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

```C++
#include <string>
int num = stoi(str)					<--- string형을 int로 바꾸는 함수
string str = to_string(num)				<--- int형을 string으로 바꾸는 함수
string a = "0123456789abcdefghij"			<--- 문자열 선언
string sub1 = a.substr(10)				<--- a[10]부터 끝까지 저장
string sub2 = a.substr(5,3)				<--- a[5]부터 3개 저장
string sub3 = a.substr(a.size()-3 , 50)			<--- 두번째 인자가 사이즈보다크면 끝까지 저장
```


```C++
#include <algorithm>

pair<자료형1, 자료형2> 변수				<--- pair의 선언
변수 = make_pair(자료형1,자료형2)			<--- make_pair로 값을 넣어줘도 된다.

sort(a.begin, a.end())					<--- 벡터 처음부터 끝까지 정렬
sort(a.begin, a.end(),cmp)				<--- cmp를 이용하여 정렬. cmp()괄호는 뺴야한다.

unique(arr.begin(),arr.end())				<--- 배열의 연속된 값을 제거한다. 전체 중복 숫자 지우는거 아님. 
arr.erase(unique(arr.begin(),arr.end()),arr.end()) 	<--- 뒤에 남기 떄문에 지워줘야한다.전체 중복을 지우고 싶으면 sort하고 이 코드 실행

reverse(arr.begin(). arr.end())				<--- 벡터를 거꾸로 한다.

next_permutation()					<--- 순열을 구하는 함수. 최소값부터 나온다 정렬 도됨
do{
}while(next_permutation(v.begin(),v.end()));

pair<int,int> a1 = minmax(10,200);			<--- 최소값 first, 최대값 second로 들어간다
auto a2 = minmax(10,200);				<--- auto로해도 pair형식으로 들어간다.
pair<int,int> b1 = minmax({10,9,1,2,5,4,7,5,8})		<--- <1,10>이 반환된다.
auto b2 = minmax({10,9,1,2,5,4,7,5,8})			<--- 똑같이 반환된다.
auto max= max_element(v.begin(),v.end())		<--- 그냥 이렇게 쓰는게 나을거같다.
auto min= min_element(v.bigin(),v_end())
```

```C++
#include <set>
set <자료형> 변수				  <---set은 중복이 안된다. 오름차순으로 정렬을 해준다.
multiset <자료형> 변수			  <--- 중복이 허용되며 오름차순으로 정렬된다. 
변수.insert()				     <--- multiset/set의 삽입
변수.begin()
변수.end()
```

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
```C++
조건 ? A : B				       <--- 삼항연산자 조건이 참이면 A, 거짓이면 B를 반환한다.
48~57('0'~'9')65~90('A'~'Z')97~122('a'~'z') 	<--- 아스키 코드 
알파벳 대문자 - 32 == 알파벳 소문자		     <--- 'A' + 32 = 'a'
```


# 프로그래머스
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



