# abasParser
CreditCard, Bank Transaction SMS/Push Notification Parser


1. Test Endpoint

POST  http://52.79.69.105/billzi/ns/payMessage/parsePayMessage

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
