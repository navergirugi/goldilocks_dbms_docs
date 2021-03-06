# Goldilocks - SquirrelSQL 연동 가이드

## 1. 개요

#### 1 - 1. GOLDILOCKS JDBC DRIVER 를 이용하여 SquirrelSQL 과 연동하는 방법을 설명한다.

#### 1 - 2. 이 문서는 http://www.squirrelsql.org/ 에서 제공하는 툴을 기준으로 설명한다.


###### [ 테스트 환경 ]

<h6>

    OS Server   : LINUX 3.10.0-327.el7.x86_64
    DATABASE    : GOLDILOCKS 3.1.0 r22655
    JDBC DRIVER : goldilocks6.jar

    CLIENT OS   : WINDOWS 7
    JAVA        : 1.8.0_131
    SquirrelSQL : 3.8.0

</h6>

## 2. SquirrelSQL 다운로드

#### 2 - 1. http://www.squirrelsql.org/ 사이트에 접속한다.

#### 2 - 2. 화면 좌측상단 Menu 의 Download and Installation 을 클릭한다.

#### 2 - 3. Plain zips the latest release for Windows/Linux/MacOS X/others 를 클릭한다.

![squirrelsql_01](https://user-images.githubusercontent.com/9734988/33247149-359eb0c8-d35f-11e7-86e4-4abcd8bf9f6f.jpg)

#### 2 - 4. squirrelsql-<version>-optional.zip 을 누른뒤 다운로드를 진행한다.

![squirrelsql_02](https://user-images.githubusercontent.com/9734988/33247142-2e26e950-d35f-11e7-99c5-16b5a9af6737.jpg)

## 3. SquirrelSQL 설치

#### 3 - 1. 다운로드 받은 zip 파일을 압축해제한다.

#### 3 - 2. 인코딩을 UTF-8 로 하려는 경우 Squirrel-sql.bat 파일의 내용을 수정한다.


###### [ 수정 내용 ] 내용 가장 하단 start 부분의 줄에 다음의 내용을 추가한다.

<h6>

    -Dfile.encoding=UTF-8 -Dsun.jnu.encoding=UTF-8

</h6>

![squirrelsql_07](https://user-images.githubusercontent.com/9734988/33247179-763e7fe6-d35f-11e7-98e9-21291ee6f13d.JPG)

#### 3 - 3. Squirrel-sql.bat 파일을 실행한다.

## 4. GOLDILOCKS JDBC DRIVER 등록

#### 4 - 1. 실행된 SquirrelSQL의 좌측 Drivers 탭을 선택한다.

#### 4 - 2. + 모양의 Create a New Driver 를 선택한다.

#### 4 - 3. Extra Class Path 에서 Add 버튼을 선택한 뒤, goldilocks6.jar 파일을 등록한다.

#### 4 - 4. Driver 에 값을 입력한다.

###### [ 기입 값 ]

<h6>

    Name        : 원하는 명(문서에서는 Goldilocks)을 입력한다.
    Example URL : GOLDILOCKS JDBC URL 을 입력한다.
                  GOLDILOCKS JDBC URL 은 jdbc:goldilocks://Server IP:Listener Port/DBName 로 구성된다.
                    DBName 은 아무 문자열이나 입력하면 되나 null 은 허용하지 않는다.
                    예) SERVER IP 가 192.168.0.50 이고 Listener Port 가 22581 인 경우 URL 구성
                      jdbc:goldilocks://192.168.0.50:22581/goldilocks
    Class Name  : GOLDILOCKS JDBC DRIVER NAME 을 입력한다.
                  GOLDILOCKS JDBC DRIVER NAME 은 sunje.goldilocks.jdbc.GoldilocksDriver 이다.

</h6>

#### 4 - 6. OK 버튼을 클릭하여 Driver 를 등록한다.

![squirrelsql_04](https://user-images.githubusercontent.com/9734988/33247210-aae57eb6-d35f-11e7-8aa7-168184106a2f.jpg)

## 5. GOLDILOCKS Connection 등록

#### 5 - 1. SquirrelSQL의 좌측 Alias 탭을 선택한다.

#### 5 - 2. + 모양의 Create a New Alias 를 선택한다.

#### 5 - 3. Alias 에 값을 입력한다.

###### [ 기입 값 ]

<h6>

    Name        : 원하는 명(문서에서는 Goldilocks)을 입력한다.
    Driver      : Drivers탭의 Name에서 입력한 명(문서에서는 Goldilocks)을 선택한다.
    URL         : Drivers의 Example URL의 내용으로 자동으로 입력되나, 수정할 부분이 있다면 수정한다.
    UserName    : 데이터베이스 사용자 아이디를 입력한다.
    Password    : 데이터베이스 사용자 비밀번호를 입력한다.

</h6>

#### 5 - 4. Test 버튼을 클릭한 뒤, Connect 버튼을 눌러 연동이 되는지 확인한다.

###### [ 연동이 되지 않는 경우 ]

<h6>

    데이터베이스 서버가 구동중인지 확인한다.
    리스너가 구동중인지 확인한다.
    기입한 IP 와 PORT 를 이용하여 클라이언트에서 서버로 통신이 가능한지 확인한다.

</h6>

#### 5 - 5. OK 버튼을 눌러 Database 에 접속한다.

![squirrelsql_05](https://user-images.githubusercontent.com/9734988/33247215-aedc3fdc-d35f-11e7-9b69-88a406852b15.jpg)

## 6. GOLDILOCKS 쿼리 수행

#### 6 - 1. 쿼리를 입력한 뒤 수행하여 결과를 받아온다.

![squirrelsql_06](https://user-images.githubusercontent.com/9734988/33247216-b0d6d48c-d35f-11e7-98d6-d2d729699f3e.jpg)
