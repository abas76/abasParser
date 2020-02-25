# abasParser
CreditCard , Bank Transaction SMS Push Notification Parser

신용 카드 , 은행 문자 푸시 알림 메세지 파싱 


# 20200201 현재 지원가능 금융사
1. 카드 사용

 . 삼성페이, 카카오뱅크카드, 케이뱅크카드 
 . 신한카드, 우리카드, 하나카드, 삼성카드, BC카드, 롯데카드 
   현대카드, 국민카드, 씨티카드, IBK기업은행카드, NH농협카드, MG새마을금고카드, KDB산업은행카드
   전북은행카드, 광주은행카드, 우체국카드, 신협카드, 수협카드, 현대백화점카드 
   
2. 은행 입출금

. KB국민은행,신한은행,우리은행,하나은행,케이뱅크,카카오뱅크,NH농협은행,수협은행,MG새마을,SC제일은행,씨티은행,KDB산업은행,IBK기업은행,대구은행,BNK부산은행,BNK경남은행,광주은행,전북은행,제주은행


# Test 방법

Test Endpoint : POST  http://52.79.69.105/billzi/ns/payMessage/parsePayMessage

Header : Content-Type , application/json

Body Sample :

- SMS Request

{

	"inputCd":"S",	                // 'S'ms , 'P'ush
	"msgInputKey": "15993333",	// 문자받은전화번호
	"rawTitle":"",			
	"rawText":"[카카오뱅크] 이*신(9999) 12/11 15:42 출금 7,250원 세븐일레븐 가평목동 잔액 4,123,123원"
	
}

- SMS Response

{

    "resultVO": {
        "resultCode": "0",
        "resultMessage": "SUCCESS",
        "httpStatusCode": "OK"
    },
    "inputCd": "S",
    "msgInputKey": "15993333",
    "rawTitle": "",
    "rawText": "[카카오뱅크] 이*신(9999) 12/11 15:42 출금 7,250원 세븐일레븐 가평목동 잔액 4,123,123원",
    "parsedVO": {
        "cmpnyCd": "06",
        "cmpnyName": "카카오뱅크",
        "typeCd": "B",
        "inputCd": "S",
        "crdNo": "9999",
        "tranType": "출금",
        "name": "이*신",
        "date": "20191211",
        "time": "1542",
        "storeName": "세븐일레븐 가평목동",
        "payAmt": "7250",
        "accumType": "잔액",
        "accumAmt": "4123123",
        "currency": "KRW",
        "tranLocationCd": 1,
        "ownerTypeCd": 1,
        "accumTypeCd": "02",
        "tranTypeCd": "05",
        "validationSuccess": true,
        "patternMatchSuccess": true,
        "parsingSuccess": true
    },
    "parsingSuccess": true
    
}


- Push Request

{

	"inputCd":"P",			            // 'S'ms , 'P'ush
	"msgInputKey":"com.shinhan.smartcaremgr",   // 노티받은 앱패키지명
	"rawTitle":"SOL알리미",			    // 노티메세지 타이틀
	"rawText":"신한카드(7912)승인 홍*동 10,000원(일시불)02/07 17:21 감성타코강남역점 누적 5,123,1234원"
	
}

- Push Response 

{

    "resultVO": {
        "resultCode": "0",
        "resultMessage": "SUCCESS",
        "httpStatusCode": "OK"
    },
    "inputCd": "P",
    "msgInputKey": "com.shinhan.smartcaremgr",
    "rawTitle": "SOL알리미",
    "rawText": "신한카드(7912)승인 홍*동 10,000원(일시불)02/07 17:21 감성타코강남역점 누적 5,123,1234원",
    "parsedVO": {
        "cmpnyCd": "62",
        "cmpnyName": "신한카드",
        "typeCd": "C",
        "inputCd": "A",
        "crdNo": "7912",
        "tranType": "승인",
        "name": "홍*동",
        "date": "20200207",
        "time": "1721",
        "paySchedule": "일시불",
        "storeName": "감성타코강남역점",
        "payAmt": "10000",
        "accumType": "누적",
        "accumAmt": "51231234",
        "currency": "KRW",
        "tranLocationCd": 1,
        "ownerTypeCd": 1,
        "accumTypeCd": "01",
        "tranTypeCd": "01",
        "validationSuccess": true,
        "patternMatchSuccess": true,
        "parsingSuccess": true
    },
    "parsingSuccess": true
    
}

# 문의사항 : abas@softlunch.co.kr

