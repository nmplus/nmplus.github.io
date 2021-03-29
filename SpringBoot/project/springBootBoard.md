---
sort: 2
---
# Spring Boot Project 게시판 

## 게시판 service, repository 분리하기

## dto 생성 및 작성
![dtoPackage](https://user-images.githubusercontent.com/39661858/110294065-b480eb80-8032-11eb-8c27-e198e5a66e41.png)  
![boardDto1](https://user-images.githubusercontent.com/39661858/110294073-b77bdc00-8032-11eb-8933-46408ffd9f42.png)  
![boardDto2](https://user-images.githubusercontent.com/39661858/110294080-b9de3600-8032-11eb-91ec-de58689c1a14.png)  

## 게시글 작성 구현
게시글 작성 페이지 writeBoardForm.html  
![writeBoardForm](https://user-images.githubusercontent.com/39661858/110294107-c498cb00-8032-11eb-8a73-71eba5343136.png)  
![homeControllerWriteBoardForm](https://user-images.githubusercontent.com/39661858/110294111-c5c9f800-8032-11eb-9806-15afb6f8a4a5.png)  
![index](https://user-images.githubusercontent.com/39661858/110294119-c8c4e880-8032-11eb-8d53-d52933f70092.png)  
![runIndex](https://user-images.githubusercontent.com/39661858/110294124-c9f61580-8032-11eb-8c38-17f58d1942a6.png)  
![runWriteBoardForm](https://user-images.githubusercontent.com/39661858/110294127-cb274280-8032-11eb-92df-4dffd61064b6.png)  
writeBoardForm.html 내용 글 작성 폼으로 수정  
![writeBoardForm2](https://user-images.githubusercontent.com/39661858/110294139-cebac980-8032-11eb-9f8c-7efd8b859f70.png)  
![runWriteBoardForm2](https://user-images.githubusercontent.com/39661858/110294144-d0848d00-8032-11eb-8b29-a743c3ff9a29.png)  
![repositoryPackage](https://user-images.githubusercontent.com/39661858/110294152-d2e6e700-8032-11eb-9494-879eba04021a.png)  
![boardRepositoryInterface1](https://user-images.githubusercontent.com/39661858/110294158-d5e1d780-8032-11eb-82c3-3681c2457383.png)  
![boardRepositoryInterface2](https://user-images.githubusercontent.com/39661858/110294159-d7130480-8032-11eb-8645-7b6218054900.png)  
controller 게시글 작성 완료 시 리스트로 이동하게 수정  
![homeControllerBefo](https://user-images.githubusercontent.com/39661858/110294162-d8443180-8032-11eb-8233-f22bda1f4955.png)  
![homeControllerAft](https://user-images.githubusercontent.com/39661858/110294169-da0df500-8032-11eb-87d4-acaf2208ab17.png)  
게시글 리스트 페이지 boardList.html  
![boardList1](https://user-images.githubusercontent.com/39661858/110294205-e72ae400-8032-11eb-95bb-573ed2e2c883.png)  
![boardList2](https://user-images.githubusercontent.com/39661858/110294210-e8f4a780-8032-11eb-88b4-9ce39a67deba.png)  
![runBoardList](https://user-images.githubusercontent.com/39661858/110294236-f0b44c00-8032-11eb-9231-f176d8614cbc.png)  
![homeController](https://user-images.githubusercontent.com/39661858/110294242-f1e57900-8032-11eb-9e87-02a1eb77a305.png)  
![writeBoardForm](https://user-images.githubusercontent.com/39661858/110294271-fb6ee100-8032-11eb-940b-192c36704765.png)  
실행 화면  
![runWriteBoardForm](https://user-images.githubusercontent.com/39661858/110294217-ea25d480-8032-11eb-9110-d74f1292dd98.png)  
![runWriteBoardForm2](https://user-images.githubusercontent.com/39661858/110294236-f0b44c00-8032-11eb-9231-f176d8614cbc.png)  
![db](https://user-images.githubusercontent.com/39661858/110294280-fdd13b00-8032-11eb-903f-3d9304b54e4f.png)  

## 게시글 리스트 구현
![homeController](https://user-images.githubusercontent.com/39661858/110296538-c9ab4980-8035-11eb-858c-79a6111c849a.png)  
boardList.html 내용 게시글 리스트로 수정  
![boardList](https://user-images.githubusercontent.com/39661858/110296554-cf089400-8035-11eb-8e95-faaed0b927e4.png)  
![runBoardList](https://user-images.githubusercontent.com/39661858/110296573-d334b180-8035-11eb-994e-7bb8fe4c228c.png)  

## 게시글 상세보기, 수정 구현
![homeController](https://user-images.githubusercontent.com/39661858/110296835-20188800-8036-11eb-9d11-8d765940e65d.png)  
![runBoardList](https://user-images.githubusercontent.com/39661858/110296847-23137880-8036-11eb-9011-dad17a9d7b44.png)  
![boardDetail](https://user-images.githubusercontent.com/39661858/110296861-273f9600-8036-11eb-8453-2d46b42d630a.png)  
![boardUpdate](https://user-images.githubusercontent.com/39661858/110296866-2870c300-8036-11eb-84b5-727abaf0733b.png)  
![boardList](https://user-images.githubusercontent.com/39661858/110296894-30306780-8036-11eb-9ac2-ff3b4b656ed1.png)  
![db](https://user-images.githubusercontent.com/39661858/110296895-31619480-8036-11eb-8e6f-8ef6d841e71a.png)  

## 게시글 삭제 구현
![writeBoardForm](https://user-images.githubusercontent.com/39661858/110296991-5229ea00-8036-11eb-8ae8-0e5bbb665879.png)  
![homeController](https://user-images.githubusercontent.com/39661858/110297003-548c4400-8036-11eb-880a-8da6112ca8cf.png)  
![runDelete](https://user-images.githubusercontent.com/39661858/110297011-57873480-8036-11eb-9705-cc5033c63515.png)  
![runDeleteBoardList](https://user-images.githubusercontent.com/39661858/110297016-5950f800-8036-11eb-84b5-bb83f6279e6e.png)  
![db](https://user-images.githubusercontent.com/39661858/110297023-5a822500-8036-11eb-8d98-7ef63807cab3.png)  

## 비밀번호 입력 및 비교 구현
![validatorPackage](https://user-images.githubusercontent.com/39661858/110297184-8a312d00-8036-11eb-8e71-aa255beacaa4.png)  
![BoardValidator1](https://user-images.githubusercontent.com/39661858/110297189-8d2c1d80-8036-11eb-80bc-6d875ba4efb7.png)  
![BoardValidator2](https://user-images.githubusercontent.com/39661858/110297199-91f0d180-8036-11eb-9797-67e204e45209.png)  
![HomeController](https://user-images.githubusercontent.com/39661858/110297226-974e1c00-8036-11eb-8652-98cf60ac4fb7.png)  
![runValidator1](https://user-images.githubusercontent.com/39661858/110297231-9a490c80-8036-11eb-8346-235767f6b690.png)  
![runValidator2](https://user-images.githubusercontent.com/39661858/110297242-9c12d000-8036-11eb-905a-7e176faa9013.png)  

## 조회수 구현
![homeController](https://user-images.githubusercontent.com/39661858/110297351-b9e03500-8036-11eb-8d58-e869d492fe7c.png)  
![runHitcount1](https://user-images.githubusercontent.com/39661858/110297358-bba9f880-8036-11eb-8378-5f69ecae81d6.png)  
![runHitcount2](https://user-images.githubusercontent.com/39661858/110297363-bd73bc00-8036-11eb-9770-abf22be2b893.png)  

## 페이징 구현
![homeController](https://user-images.githubusercontent.com/39661858/110297420-cebcc880-8036-11eb-9632-afeae69b4b35.png)  
![boardList](https://user-images.githubusercontent.com/39661858/110297430-d0868c00-8036-11eb-983e-cc7e996e6c6c.png)  
![runboardList1](https://user-images.githubusercontent.com/39661858/110297442-d3817c80-8036-11eb-9b85-488e3331dffa.png)  
![runboardList2](https://user-images.githubusercontent.com/39661858/110297444-d4b2a980-8036-11eb-9d2f-7fc504b4c01c.png)  