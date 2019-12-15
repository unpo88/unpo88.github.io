---
layout: post_blog
title:  "완주하지 못한 선수"
subtitle: "HASH"
type: "프로그래머스"
blog: true
text: true
author: "Wonsub Choi"
post-header: true
order: 1
---

# 문제 설명 [`문제풀기`](https://www.welcomekakao.com/learn/courses/30/lessons/42576)
수많은 마라톤 선수들이 마라톤에 참여하였습니다. 단 한 명의 선수를 제외하고는 모든 선수가 마라톤을 완주하였습니다.

마라톤에 참여한 선수들의 이름이 담긴 배열 participant와 완주한 선수들의 이름이 담긴 배열 completion이 주어질 때, 완주하지 못한 선수의 이름을 return 하도록 solution 함수를 작성해주세요.

# 제한사항
- 마라톤 경기에 참여한 선수의 수는 1명 이상 100,000명 이하입니다.

- completion의 길이는 participant의 길이보다 1 작습니다.

- 참가자의 이름은 1개 이상 20개 이하의 알파벳 소문자로 이루어져 있습니다.

- 참가자 중에는 동명이인이 있을 수 있습니다.

# 문제 풀이
- unordered_map 이용한 풀이

{% highlight cp %}

#include <string>
#include <vector>
#include <unordered_map>

using namespace std;

string solution(vector<string> participant, vector<string> completion) {
    string answer = "";

    unordered_map<string, int> participants;
    
    for(auto name : participant){
        ++participants[name];
    }
    
    for(auto name : completion){
        --participants[name];
    }
    
    for(auto pair : participants){
        if(pair.second > 0){
            answer = pair.first;
            return answer;
        }
    }
    
    return answer;
}

{% endhighlight %}

- 정렬을 이용한 풀이

{% highlight cp %}

#include <string>
#include <vector>
#include <algorithm>

using namespace std;

string solution(vector<string> participant, vector<string> completion) {
    string answer = "";

    sort(participant.begin(), participant.end());
    sort(completion.begin(), completion.end());
    
    for(int idx = 0; idx < participant.size(); idx++){
        if(participant[idx] != completion[idx]){
            answer = participant[idx];
            return answer;
        }
    }
    
    return answer;
}

{% endhighlight %}