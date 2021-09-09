---
title: 프로그래머스(스택/큐) - 주식가격
author: 서동섭
date: 2021-09-08 22:11:00 +0800
categories: [Coding-test, programmers]
tags: [coding-test, stack, queue, programmers]
pin: false
---

## 출처

<a target="_blank" href="https://programmers.co.kr/learn/courses/30/lessons/42584">문제링크</a>

## 문제 설명

초 단위로 기록된 주식가격이 담긴 배열 prices가 매개변수로 주어질 때, 가격이 떨어지지 않은 기간은 몇 초인지를 return 하도록 solution 함수를 완성하세요.

## 제한사항

- prices의 각 가격은 1 이상 10,000 이하인 자연수입니다.
- prices의 길이는 2 이상 100,000 이하입니다.

## 입출력 예

prices	|	return
[1, 2, 3, 2, 3]	|	[4, 3, 1, 1, 0]

## 입출력 예 설명

- 1초 시점의 ₩1은 끝까지 가격이 떨어지지 않았습니다.
- 2초 시점의 ₩2은 끝까지 가격이 떨어지지 않았습니다.
- 3초 시점의 ₩3은 1초뒤에 가격이 떨어집니다. 따라서 1초간 가격이 떨어지지 않은 것으로 봅니다.
- 4초 시점의 ₩2은 1초간 가격이 떨어지지 않았습니다.
- 5초 시점의 ₩3은 0초간 가격이 떨어지지 않았습니다.

## 내 풀이

```java

import java.util.*;
class Solution {
    public int[] solution(int[] prices) {
        
        Queue<Integer> queue = new LinkedList<>();
        for(int i = 0; i < prices.length; i++){
            queue.offer(prices[i]);        
        }      
       
        List<Integer> result = new ArrayList<Integer>();
        
        while(!queue.isEmpty()){
        
            if(queue.size() == 1) { result.add(0); break;}
            int first = queue.poll();            
            int time = 0;             
            for(int next : queue){                
                time++;
                if( first > next){ break; }                
            }                       
            result.add(time);
            
        }        
        
        return result.stream().mapToInt(i->i).toArray();
    }
}
```

## 느낀점

비슷한 문제 4번째다 보니 이번건 이전에 비하면 금방 품...같은 레벨2인데...ㅠㅠ
화이팅 !!!
