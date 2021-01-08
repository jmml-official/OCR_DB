## DB 소개
* OCR 데이터 셋 (Text Localization, Word Recognition)
* 인스턴스(Instance) 구분 : 단어(Word)
* 대상 언어
	* 한글
	* 영어 (소문자/대문자)
	* 숫자
	* 특수문자 (키보드로 입력 가능한 특수문자)

## DB 구성
* 이미지 파일 : 3000장 (JPG), 1920x1080
* 어노테이션 파일 : 1개 (JSON)

### 파일 위치
```bash
OCR_DB
├── annotations
│   └── annotations.json
└── images
    ├── 0518_S00003.jpg
    ├── 0518_S00005.jpg
    └── ...
```

### annotation.json
```json
{
	"image": [
		{
			"id": "00000",
			"name": "0518_S00003.jpg",
			"objects": [
				{
					"id": "00000",
					"class": "sign",
					"points": [
						"1873.10",
						"230.58",
						"1893.46",
						"229.17",
						"1900.01",
						"232.35",
						"1898.59",
						"242.44",
						"1893.46",
						"247.93",
						"1869.74",
						"250.23"
					],
					"Description": "H",
					"Reading Direction": "Horizontal",
					"Text Direction Index": "0",
					"Art Characters": "false",
					"Special Characters": "false",
					"occlusion": "true",
					"Don't Care": "false"
				},
				{
					"id": "00001",
					"class": "...",
					"..."
				}
			]
		},
		{
			"..."
		},
		"..."
	]
}
```

* **id**: 이미지 고유 id
* **name**: 이미지 파일명
* **Objects**: 인스턴스 별 어노테이션 정보
	
	| **속성** | **속성값** | **info** |
	|  :---:  |  :---:  |  :---:  | 
	| "id" | 해당 이미지에서의 instance id | 5 digit number |
	| "class" | class 이름  | "sign" |
	| "points" | Polygon 좌표 | [x1, y1, x2, y2, ... , xn, yn] |
	| "Description" | instance의 글자 정보 | 유니코드 |
	| "Reading Direction" | 글자 진행 방향 | Horizontal / Vertical |
	| "Text Direction Index" | 글자 진행 방향 | 0 ~ 7 |
	| "Art Character" | 타이포그래피 여부 | true / false |
	| "Special Characters" | 특수문자 여부 | true / false |
	| "occlusion" | 가려진 글자인지에 대한 정보 | true / false |
	| "Don't care" | Don't care | true / false |

* **Text Direction Index** : 글자 각도 인덱스 = {0, 1, 2, ..., 7}
	
	| **N=0** | **N=1** | **N=2** | **N=3** | **N=4** | **N=5** | **N=6** | **N=7** |
	|  :---:  |  :---:  |  :---:  |  :---:  |  :---:  |  :---:  |  :---:  |  :---:  |
	| <p align="center"> <img src="pic/n0.PNG"> </p> | <p align="center"> <img src="pic/n1.PNG"> </p> | <p align="center"> <img src="pic/n2.PNG"> </p> | <p align="center"> <img src="pic/n3.PNG"> </p> | <p align="center"> <img src="pic/n4.PNG"> </p> | <p align="center"> <img src="pic/n5.PNG"> </p> | <p align="center"> <img src="pic/n6.PNG"> </p> | <p align="center"> <img src="pic/n7.PNG"> </p> |

## DB 다운로드
* 다운로드 [링크](https://drive.google.com/file/d/1AYEpejAB5jd2zi-vWayCQmDkQN-kKrvN/view?usp=sharing) (압축버전)
* 다운로드 [링크](https://kor01.safelinks.protection.outlook.com/?url=https%3A%2F%2Fdrive.google.com%2Fdrive%2Ffolders%2F11frxzBLp-2_krbjVLSozXXurbmuh40A8%3Fusp%3Dsharing&data=04%7C01%7Cjaemyunglee%40ncsoft.com%7Cfa5107f91fa14d8976cf08d8b2e9ec9f%7C91856527a4464990b48e37ca10f2ee8d%7C0%7C0%7C637456065049643905%7CUnknown%7CTWFpbGZsb3d8eyJWIjoiMC4wLjAwMDAiLCJQIjoiV2luMzIiLCJBTiI6Ik1haWwiLCJXVCI6Mn0%3D%7C1000&sdata=9hP6MzZwdKSPD0Tk34N2cr3jELakiIYbhhaIiH7bzNw%3D&reserved=0) (미리보기 가능)

## 감사의 글 (Acknowledgement)
이 데이터는 2020년도 정부(과학기술정보통신부)의 재원으로 정보통신기획평가원의 지원을 받아 수행된 연구의 결과물임 (No.1711117050, 디지털 콘텐츠 분석 효율화를 위한 문자 검출 및 인식 기술 개발)

This work was supported by Institute of Information & communications Technology Planning & Evaluation (IITP) grant funded by the Korea government(MSIT) (No.1711117050, Text Localization and Recognition for Efficient Digital Contents Analysis)