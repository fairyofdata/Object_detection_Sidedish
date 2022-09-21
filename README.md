# <div align="center">Project : 건우네반찬</div>
### <div align="center">도마 위의 식재료를 객체 인식 후, <br>추출된 식재료 리스트를 기반으로 적절한 레시피를 추천 하는 서비스</div>

### <div align="right">Team Name <br> 오늘뭐먹조</div>
#### <div align="right">Team Member <br> 고기원(DS), 백지헌(DS) 이은평(DS), 이지원(DS) <br> 김건우(DE/조장), 계은서(DE), 정현식(DE)</div>
___

### <div align="center">발표자료 및 자세한 내용은 아래 프레젠테이션 PDF 참조
<div align="center">https://github.com/rjs6418/KDT_FinalProject_1/blob/master/KDT-MC-FinalProject-1%EC%A1%B0.pdf</div>
<br>
<div align="center">서비스 시연 영상</div>
<div align="center">https://kuno-techblog.tistory.com/4</div>

<br><br>
## <div align="center">프로젝트 기획 배경 및 목표</div>
> <div align="center">코로나19 이후 비대면 및 재택근무 추이가 증가하기도 하면서 집에 머무는 시간이 크게 증가하였고,</div> 
> <div align="center">여러가지 사회 이슈로 인한 소비자 물가 상승과 외식물가가 크게 올랐다.</div> 
> <br>
> <div align="center">동시에, 사람들의 요리 레시피 컨텐츠에 대한 관심도 증가와 '무소비', '무지출', '냉장고파먹기'라는 단어의 언급 빈도가 증가하면서</div>
> <div align="center">이와 같은 서비스가 소비자들에게 필요로 할 것이라 판단되었다.</div>
> <div align="center">현재, 비슷한 서비스 중 가장 높은 점유율을 차지하고 있는 '만개의 레시피'에서 부족하거나 더 필요로 하는 기능을 기획하였다.</div>
<br><br>


### 서비스 중심의 전체 파이프라인 구성도
![image](https://user-images.githubusercontent.com/101792115/190885374-eec94646-0a68-4753-82b0-8f6c1da2df11.png)
> 프로젝트를 진행하면서 중심이 되었던 구조도이다.
>
> 구성도 중 중심에서 가장 길게 뻗어있는 파이프가 메인서비스의 데이터 파이프라인인데,
> 사용자로 부터 받은 식재료 사진을 받아 객체인식을 한 후, 인식된 식재료 리스트에 필요한 식재료를 추가하여 다시 전송,
> 조리가능한 레시피를 추천 순으로 정렬하고, 해당 레시피 정보를 응답한다.
> (이때, 응답하는 레시피는 완전히 조리가가능한 레시피와, 식재료가 1~2개 부족한 레시피를 나누어 추천한다.)
>
> 가장 하단의 라인은 부가적인 서비스로, 부족한 식재료를 유저간 교환할 수 있게끔 매칭기능을 구현 하였다.  
> 
> 메인 파이프라인 위쪽에 해당하는 영역은 서비스 이용에 필요하거나 서비스 이용 시 발생하는 데이터를 관리하는 파이프라인이다.
<br><br>

### 객체인식 모델

![image](https://user-images.githubusercontent.com/101792115/191442571-aad74ff0-124d-4802-bea5-e303617ec471.png)
<br>![image](https://user-images.githubusercontent.com/101792115/191442639-fc916833-777c-49b1-b526-ca4b27712381.png)

> 객체인식 모델은 Yolo v5 모델을 사용했다. 
>
> 현재, 객체인식 모델 중 가장 뛰어난 성능을 보이며, 
> 
> **비교군이었던 EfficientDet보다도 높은 성능을 보이는 것으로 확인되었다.



### 데이터 수집 및 전처리

![image](https://user-images.githubusercontent.com/101792115/191443688-11fcc908-7260-40d9-b435-e12a7de01c24.png)

> 캐글에서 다운로드, 구글의 검색 이미지 크롤링으로 데이터를 수집 한 후, 

![image](https://user-images.githubusercontent.com/101792115/191444097-07c46a04-538a-4f53-ab10-48c0f5ebe9da.png)

>모델 학습을 위한 라벨링 작업을 실시하였다.
>다만, 이미지 하나당 하나의 객체만이 들어가 있는 단일 객체 이미지의 경우, 자동으로 라벨링을 해주는 코드를 작성하여 사용하였다.


## 향후 추가 개선계획

### 웹구현-Flask의 경우 다소 짜임새 없이 작성되었음 -> 추가 공부 후 개선 
### 설계상 카프카에서 몇가지 문제가 확인 되었다 -> 구현 방향 수정 필요
### 기술 및 시간 상의 문제로 원하는 방식과 수준의 추천시스템을 구현하지 못함
곧 원리를 설명하는 내용을 블로그에 기획안 형식으로 게재 예정
