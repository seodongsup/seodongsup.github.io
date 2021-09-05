---
title: 프로그래머스(해시) - 베스트 앨범
author: 서동섭
date: 2021-09-04 22:11:00 +0800
categories: [Coding-test, Tutorial]
tags: [coding-test, hash, programmers]
pin: false
---

## 문제2 - 위장

<a target="_blank" href="https://programmers.co.kr/learn/courses/30/lessons/42579">문제링크</a>

# 문제 설명

스트리밍 사이트에서 장르 별로 가장 많이 재생된 노래를 두 개씩 모아 베스트 앨범을 출시하려 합니다. 노래는 고유 번호로 구분하며, 노래를 수록하는 기준은 다음과 같습니다.

- 속한 노래가 많이 재생된 장르를 먼저 수록합니다.
- 장르 내에서 많이 재생된 노래를 먼저 수록합니다.
- 장르 내에서 재생 횟수가 같은 노래 중에서는 고유 번호가 낮은 노래를 먼저 수록합니다.
- 노래의 장르를 나타내는 문자열 배열 genres와 노래별 재생 횟수를 나타내는 정수 배열 plays가 주어질 때, 베스트 앨범에 들어갈 노래의 고유 번호를 순서대로 return 하도록 solution 함수를 완성하세요.

# 제한사항

- genres[i]는 고유번호가 i인 노래의 장르입니다.
- plays[i]는 고유번호가 i인 노래가 재생된 횟수입니다.
- genres와 plays의 길이는 같으며, 이는 1 이상 10,000 이하입니다.
- 장르 종류는 100개 미만입니다.
- 장르에 속한 곡이 하나라면, 하나의 곡만 선택합니다.
- 모든 장르는 재생된 횟수가 다릅니다.

# 입출력 예

genres  |	plays   |	return
["classic", "pop", "classic", "classic", "pop"]	|[500, 600, 150, 800, 2500] |   [4, 1, 3, 0]

# 입출력 예 설명

classic 장르는 1,450회 재생되었으며, classic 노래는 다음과 같습니다.

- 고유 번호 3: 800회 재생
- 고유 번호 0: 500회 재생
- 고유 번호 2: 150회 재생

pop 장르는 3,100회 재생되었으며, pop 노래는 다음과 같습니다.

- 고유 번호 4: 2,500회 재생
- 고유 번호 1: 600회 재생

따라서 pop 장르의 [4, 1]번 노래를 먼저, classic 장르의 [3, 0]번 노래를 그다음에 수록합니다.

※ 공지 - 2019년 2월 28일 테스트케이스가 추가되었습니다.

## 내 풀이

```java

import java.util.*;
import java.util.stream.Stream;

class Info{
    
    private String genres;
    private int order;
    private int plays;
    
    public void setGenres(String genres){this.genres = genres;} 
    public void setOrder(int order){this.order = order;} 
    public void setPlays(int plays){this.plays = plays;}     
    public String getGenres() {return genres;}
    public int getOrder() {return order;}
    public int getPlays() {return plays;}
    
}

class Solution {
    public int[] solution(String[] genres, int[] plays) {
        
        // 장르별 노래의 정렬을 위한 리스트
        List<Info> list = new ArrayList<Info>();  
        
        // 장르별 정렬을 위한 총합 
        Map<String, Integer> genresSum = new HashMap<String, Integer>();
        
        // 데이터 셋팅
        for( int i = 0; i < genres.length; i++){
            
            Info _info = new Info();
            _info.setOrder(i);
            _info.setGenres(genres[i]);
            _info.setPlays(plays[i]);
            list.add(_info);
           
            genresSum.put(genres[i], genresSum.getOrDefault(genres[i], 0 ) + plays[i]); 
            
        }
        
        // 장르별 총합 정렬
        List<String> keySetList = new ArrayList<>(genresSum.keySet());
        Collections.sort(keySetList, (o1, o2) -> (genresSum.get(o2).compareTo(genresSum.get(o1))));           
        
        // 결과 값
        List<Integer> answer = new ArrayList();
        
        // 1. 속한 노래가 많이 재생된 장르 부터 셋팅
        for(String key : keySetList) {            
            
            // 해당 장르만 불러오기
            Stream<Info> genres_list = list.stream().filter(oo-> oo.getGenres().equals(key) );
            
            // 해당 장르 정렬 ( 정렬 순서 : 재생 횟수 desc / 고유 번호 asc )
            Comparator<Info> _sort = Comparator.comparing(Info::getPlays).reversed().thenComparing(Info::getOrder);          
            
            // 해당 장르의 노래를 정렬된 순서로 최대 2개 까지만 불러오기
            genres_list.sorted(_sort).limit(2).forEach(s -> {                  
                answer.add(s.getOrder());         
            });            
            
		}   
        
        // 결과 세팅
        int[] result = answer.stream().mapToInt(i->i).toArray();        
        return result;

    }
}
```

## 느낀점

다른 사람의 풀이에 보면 좋아요가 많이 눌린 풀이를 보면, 대부분 짧고 간결한 코드들이다.
나 또한 그렇다. 짧은 코드가 깔끔하고 가독성이 좋다. 다만 이해도가 요구된다.
이번 풀이는 평소에 잘 안쓰던 내부클래스로 vo를 선언해서 풀어봤다.
