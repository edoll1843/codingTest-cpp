#프로그래머스

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
#include <string>
#include <vector>
#include <iostream>
#include <algorithm>
#include <queue>

using namespace std;

int solution(vector<int> priorities, int location)
{
	priority_queue <int> q;
	queue <pair<int, int>> qp;
	int answer = 0;
	
	for (int a = 0; a < priorities.size(); a++)
	{
		q.push(priorities[a]);
		qp.push(make_pair(priorities[a], a));
	}
	while (!qp.empty())
	{
		int num = qp.front().first;
		int lo = qp.front().second;
		qp.pop();
		
		if (num == q.top())
		{
			q.pop();
			answer++;
			if (lo == location)
				break;
		}
		else
		{
			qp.push(make_pair(num, lo));
		}
	}
	return answer;
}
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

```
```C++

```
