---
title: 프로그래머스(해시) - 완주하지 못한 선수
author: 서동섭
date: 2021-08-20 22:11:00 +0800
categories: [Coding-test, Tutorial]
tags: [coding-test, hash, programmers]
pin: false
---

## 문제1 - 완주하지 못한 선수

<a target="_blank" href="https://programmers.co.kr/learn/courses/30/lessons/42576">문제링크</a>

수많은 마라톤 선수들이 마라톤에 참여하였습니다. 단 한 명의 선수를 제외하고는 모든 선수가 마라톤을 완주하였습니다.

마라톤에 참여한 선수들의 이름이 담긴 배열 participant와 완주한 선수들의 이름이 담긴 배열 completion이 주어질 때, 완주하지 못한 선수의 이름을 return 하도록 solution 함수를 작성해주세요.


## 제한사항

- 마라톤 경기에 참여한 선수의 수는 1명 이상 100,000명 이하입니다.
- completion의 길이는 participant의 길이보다 1 작습니다.
- 참가자의 이름은 1개 이상 20개 이하의 알파벳 소문자로 이루어져 있습니다.
- 참가자 중에는 동명이인이 있을 수 있습니다.

## 입출력 예

participant	| completion | return
["leo", "kiki", "eden"] | ["eden", "kiki"] | "leo"
["marina", "josipa", "nikola", "vinko", "filipa"] |	["josipa", "filipa", "marina", "nikola"] | "vinko"
["mislav", "stanko", "mislav", "ana"] | ["stanko", "ana", "mislav"]	| "mislav"

## 입출력 예 설명

예제 #1
"leo"는 참여자 명단에는 있지만, 완주자 명단에는 없기 때문에 완주하지 못했습니다.

예제 #2
"vinko"는 참여자 명단에는 있지만, 완주자 명단에는 없기 때문에 완주하지 못했습니다.

예제 #3
"mislav"는 참여자 명단에는 두 명이 있지만, 완주자 명단에는 한 명밖에 없기 때문에 한명은 완주하지 못했습니다.

## 내 풀이

- 두 배열 각각 정렬
- 순차적으로 다를때까지 비교
- 다른경우 break 후 리턴

```javascript
function solution(participant, completion) {
    var answer = '';
    participant.sort();
    completion.sort();
    for(var i = 0; i < participant.length; i++){
        if(participant[i] != completion[i]){
            answer = participant[i];
            break;
        }        
    }
    return answer;
}
```

## 느낀점

몇년만에 코딩 연습 첫번째 문제...<br/>
한시간 반이상 걸렸다...<br/>
반성하며 앞으로 효율성을 생각하며 코딩해야겠다...<br/>
모든 문제 다푸는 그날까지 화이팅!