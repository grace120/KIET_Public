# bsi

[제조업경기조사 부표 만들기]

1. 통계 업체서 받은 원자료 파일을 bsi 폴더에 옮김

2. bsi.R 열어서 '0. what do you need' 파트의 다음 항목 수정

 - YEAR : 연도
 - QUARTER : 분기
 - FILE : 결과표 엑셀 파일

3. 전부 실행 (ctrl+a, ctrl+enter)

4. bsi 폴더에 'YYYY-QQ' 식으로 새로운 폴더, 더불어 엑셀 파일이 생성

5. 엑셀 파일로 보도자료 부표, 보고서 부표, 산자부용 주관식 정리 만들면 됨

 - 부표에 붙여넣기 전, '휴먼명조, 9pt, 가운데 정렬' 처럼 엑셀에서 글꼴을 일괄 바꿔주는 게 편함
 - 샘플 폴더에 작업분을 올려두었으니 참고
 - 중국 bsi 보고서 부표는 보도자료 부표를 옮겨 작업 (22.04.18 기준)

# chinacheck

[중국진출기업 응답 정합성 체크]

1. 검증용 raw data 파일을 열어서, 첫 번째 row(한글로 된 문항 설명)는 삭제하고 저장

 - 공란이 많아서 R에서 직접 로드 시 다소 번잡함

2. bsi_chinacheck.R 열어서 '0. what do you need' 파트의 다음 항목 수정

 - YEAR : 연도
 - QUARTER : 분기
 - FILE : 검증용 raw data 엑셀 파일

3. 전부 실행 (ctrl+a, ctrl+enter)

4. bsi_chinacheck 폴더에 'YYYY-QQ' 식으로 새로운 폴더, 더불어 엑셀 파일이 생성

5. 엑셀 파일 열고, FALSE는 전부 제거

 - ctrl+f - '바꾸기' 탭 - '찾을 내용'을 'FALSE', '바꿀 내용'을 ' ' 공란으로 지정 - 모두 바꾸기

6. TRUE가 있는 부분은 오류, 이에 기반해 원자료에 정합성 체크 결과 표시(오류 색칠)

 - 샘플 폴더에 작업분을 올려두었으니 참고

<에러 구분>

 - error1 : 세 지역 사업비율 합계 100 아님
 - error2-5 : 해당 지역에서 사업을 한다고 답했으나, 판매 실적(현황)을 적지 않음
 - error6-8 : 판매 실적(현황)과 전망을 함께 적어야 하나, 미비한 부분이 있음
 - error9-14 : 기타 질문에서 실적/전망 응답이 대칭적이지 않음 (error6-8과 같은 맥락)

# dobby

[자동퇴근 프로그램]

1. dobby 폴더 내 다음 파일들이 있는지 확인 (크롤링 도구)

 - chromedriver.exe (크롬브라우저와 버전 같아야 함, 아래 자세히 설명)
 - geckodriver.exe
 - selenium-server-standalone-4.0.0-alpha-1.jar

2. dobby.R 열어서 '0. what do you need' 파트의 다음 항목 수정

 - WHEN : 퇴근체크 예정 시각, 실제로는 지정한 것보다 1-2분 늦게 찍힘
 - ID : 포털 아이디
 - PW : 포털 비밀번호
 - SHUTDOWN : 컴퓨터 종료 여부, 'YES'로 적어야만 전원 꺼짐

3. 전부 실행 (ctrl+a, ctrl+enter)

 - 퇴근 시까지, RStudio Console(왼쪽 하단) 창에 5분마다 진행 상황이 표시됨

<chromedriver.exe 관련>

 - 크롬브라우저가 업데이트되면, chromedriver.exe 도 같은 버전으로 대체해줘야 함
 - 크롬브라우저 버전 확인 : 설정 - Chrome 정보 - 'Chrome이 최신 버전입니다.' 아래 숫자 체크
 - chromedriver.exe 다운로드 : 구글에 'chrome driver' 검색 - 맨 처음 결과(chromedriver.chromium.org) 접속 - 같은 버전 클릭, 다운로드

# kosis

[통계청 Open API 기반 데이터 수집]

현재 야무지게 작업 중

# news

[민위원님 전용 뉴스 가판대]

1. news 폴더 내 다음 파일들이 있는지 확인 (크롤링 도구)

 - chromedriver.exe (크롬브라우저와 버전 같아야 함, 아래 자세히 설명)
 - geckodriver.exe
 - selenium-server-standalone-4.0.0-alpha-1.jar

2. news.R 열어서 '0. what do you need' 파트의 다음 항목 수정

 - PERIOD : 몇 시간 전 기사까지 스크랩할지 지정 (default = 12, 필요에 따라 조정)

3. 전부 실행 (ctrl+a, ctrl+enter)

4. RStudio Console(왼쪽 하단) 창에 제공되는 간단한 summary 확인

5. news 폴더에 'YYYY-MM-DD 뉴스' 식으로 새로운 엑셀 파일 생성

 - 같은 날 여러 번 실행할 수 있음을 고려, overwrite 기능을 켜두었으니, 이전 파일이 삭제되길 원치 않다면 폴더 밖으로 옮겨둬야 함

6. 엑셀 파일 열고, 관심 있는 제목의 기사 링크를 통해 페이지 접속

 - 링크가 담긴 셀을 더블 클릭하면 하이퍼링크(파란색, 클릭 시 인터넷 연결) 기능이 활성화되니 참고

<제공 뉴스 목록>

 - 연합인포맥스 (전체)
 - 산업경제신문 (전체)
 - 뉴스핌 (글로벌)
 - 글로벌이코노믹 (국제)
 - 연합뉴스 (세계)
 - 뉴시스 (국제최신)
 - 뉴스1 (국제)
 - 산업일보 (전체) : 추가 예정

<chromedriver.exe 관련>

 - 크롬브라우저가 업데이트되면, chromedriver.exe 도 같은 버전으로 대체해줘야 함
 - 크롬브라우저 버전 확인 : 설정 - Chrome 정보 - 'Chrome이 최신 버전입니다.' 아래 숫자 체크
 - chromedriver.exe 다운로드 : 구글에 'chrome driver' 검색 - 맨 처음 결과(chromedriver.chromium.org) 접속 - 같은 버전 클릭, 다운로드

# psi

[전문가경기조사 부표 만들기]

1. 통계 업체서 받은 원자료 파일을 psi 폴더에 옮김

2. psi.R 열어서 '0. what do you need' 파트의 다음 항목 수정

 - YEAR : 연도
 - MONTH : 월
 - FILE : 누적시계열 엑셀 파일

3. 전부 실행 (ctrl+a, ctrl+enter)

4. psi 폴더에 'YYYY-MM' 식으로 새로운 폴더, 더불어 엑셀 파일이 생성

5. 엑셀 파일로 보도자료 부표 만들면 됨

 - 부표에 붙여넣기 전, '휴먼명조, 9pt, 가운데 정렬' 처럼 엑셀에서 글꼴을 일괄 바꿔주는 게 편함
 - 샘플 폴더에 작업분을 올려두었으니 참고