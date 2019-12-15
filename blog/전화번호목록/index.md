---
layout: post_blog
title:  "전화번호 목록"
subtitle: "HASH"
type: "프로그래머스"
blog: true
text: true
author: "Wonsub Choi"
post-header: true
order: 2
---

# 문제 설명 [`문제풀기`](https://www.welcomekakao.com/learn/courses/30/lessons/42577)
전화번호부에 적힌 전화번호 중, 한 번호가 다른 번호의 접두어인 경우가 있는지 확인하려 합니다.

전화번호가 다음과 같을 경우, 구조대 전화번호는 영석이의 전화번호의 접두사입니다.

구조대 : 119

박준영 : 97 674 223

지영석 : 11 9552 4421

전화번호부에 적힌 전화번호를 담은 배열 phone_book 이 solution 함수의 매개변수로 주어질 때, 어떤 번호가 다른 번호의 접두어인 경우가 있으면 false를 그렇지 않으면 true를 return 하도록 solution 함수를 작성해주세요.

# 제한사항
- phone_book의 길이는 1 이상 1,000,000 이하입니다.

- 각 전화번호의 길이는 1 이상 20 이하입니다.

# 문제 풀이

{% highlight cp %}

#include <string>
#include <vector>
#include <algorithm>

using namespace std;

bool solution(vector<string> phone_book) {
    bool answer = true;
    
    sort(phone_book.begin(), phone_book.end());
    
    for(int idx = 0; idx < phone_book.size() - 1; idx++){
        if(phone_book[idx] == phone_book[idx + 1].substr(0, phone_book[idx].size())){
            answer = false;
            return answer;
        }
    }
    return answer;
}

{% endhighlight %}