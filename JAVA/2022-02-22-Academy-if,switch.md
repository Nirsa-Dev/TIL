# 조건문
프로그램 수행 흐름을 바꾸는 역할을 하는 제어문 중 하나로 조건에 따라 다른 문장이 수행되도록 합니다.   
   
간단히 설명하여 어떤 조건을 만들어 놓고 성립하면 코드 A 실행, 다른 추가적인 조건에 부합한다면 코드 B 실행, 모든 조건에 만족하지 않는다면 코드 C 실행과 같이 조건에 따라 코드를 제어할 수 있다.   
#
> ## if문
1. if(조건식1)의 결과가 true일 경우 중괄호안에 있는 코드를 실행   
2. if(조건식1)의 결과가 false이고 else if(조건식2,3 ...)의 결과가 true일 경우 중괄호안에 있는 코드를 실행   
3. if, else if의 모든 결과가 false일 경우 else의 중괄호안에 있는 코드를 실행   
   
```java
if(조건식1) {
  수행될 문장;
} else if(조건식2) {
  수행될 문장;
} else if(조건식3) {
  수행될 문장;
} else {
  수행될 문장;
}
```
    
> #### Q1. 나이를 입력받고 어린이, 청소년, 성인을 판단하기 (실습)
* 아래 코드 작성 시 import, class, method 제외
* 0~13 어린이
* 14~19 청소년
* 20~ 성인
```java
Scanner sc = new Scanner(System.in);
System.out.println("나이를 입력 해주세요 : ");
int age = sc.nextInt();

if(age<0) {
	System.out.println("잘못 입력 하셨습니다. 양수로 입력 하세요.");
}
else {
	if(age<14) {
		System.out.println("어린이 입니다.");
	} else if(age<20) {
		System.out.println("청소년 입니다.");
	} else {
		System.out.println("성인 입니다.");
	}
}
```
   
> #### Q2. 국영수 점수를 입력받고 과목40점 이하와 평균 60점 이하는 불합격, 초과는 합격 처리 하세요.
```java
Scanner sc = new Scanner(System.in);
System.out.println("국어 점수를 입력 하세요 : ");
int kor = sc.nextInt();
	
System.out.println("영어 점수를 입력 하세요 : ");
int eng = sc.nextInt();
	
System.out.println("수학 점수를 입력 하세요 : ");
int mat = sc.nextInt();
	
int sum = kor+eng+mat;
double avg = sum/3;
	
if((kor<=40 || eng<=40 || mat<=40) || (avg<=60)) {
	System.out.println("불합격 입니다.");
} else if(avg>=60) {
	System.out.println("국어점수 : "+kor);
	System.out.println("수학점수 : "+mat);
	System.out.println("영어점수 : "+eng);
	System.out.println("합계 : "+sum);
	System.out.println("평균 : "+avg);
	System.out.println("축하합니다, 합격입니다!");
} 
```
   
> #### Q3. 간단한 로그인 기능을 만들어 보세요.
* 기존 등록되어있는 ID : user
* 기존 등록되어있는 PW : 1234
* ID와 PW를 입력받고 기존 등록되어있는 ID, PW와 비교하여 둘 다 동일하면 "로그인 성공", ID가 틀리면 "ID가 틀렸습니다.", PW가 틀리면 "PW가 틀렸습니다"를 출력하세요.
```java
Scanner sc = new Scanner(System.in);
		
System.out.println("아이디 입력 : ");
String userId = sc.nextLine();

System.out.println("비밀번호 입력 : ");
String userPw = sc.nextLine();
		
// 데이터베이스에 등록되어 있는 아이디와 비밀번호 (회원가입이 되어있는 회원정보)
String id = "user";
String pw = "user11";
		
if(userId.equals(id) && userPw.equals(pw)) {
	System.out.println(id+"님 로그인 성공");
} else {
	System.out.println("로그인 실패");
	if(!userId.equals(id)) {
		System.out.println("ID가 틀렸습니다.");
	} else if (!userPw.equals(pw)) {
		System.out.println("PW가 틀렸습니다.");
	}
}
```

#
> ## swtich문
조건식 하나로 많은 경우의 수를 처리할 때 사용하며 이 때 조건식의 결과는 정수 또는 문자, 문자열 조건식의 결과 값과 일치하는 case문으로 이동   
default문은 일치하는 case문이 없을 때 수행(= if문의 else)
```java
switch(조건식) {
case 값1:
  수행될 문장;
  break;
case 값2:
  수행될 문장;
  break;
default:
  수행될 문장;
}
```
   
> #### Q1. 사용자에게 구마핼 과일의 이름을 입력받아 각 과일의 가격을 출력할 것
* 아래 코드 작성 시 import, class, method 제외
* 사과 1000원
* 오렌지 2000원
* 망고 5000원
   
```java
Scanner sc = new Scanner(System.in);
System.out.println("구매할 과일을 입력하세요 (사과, 오렌지, 망고)");
String fruit = sc.nextLine();

int price = 0;
switch(fruit) {
		
case "사과" : price=1000; // System.out.println("사과의 가격은 "+price+" 입니다.");
break;

case "오렌지" : price=2000; // System.out.println("오렌지의 가격은 "+price+" 입니다.");
break;

case "망고" : price=5000; // System.out.println("망고의 가격은 "+price+" 입니다.");
break;

default : System.out.println("판매하고 있는 과일이 입니다");

System.out.printf("%s의 가격은 %d원 입니다.", fruit, price);
```
   
> #### Q2. 사용자에게 월을 입력 받고 계절을 출력하세요. 
* 12 ~ 2 : 겨울
* 3 ~ 5 : 봄
* 6 ~ 8 : 여름
* 9 ~ 11 : 가을
* 그 외 다른 입력 시 "해당하는 계절이 없습니다"를 출력
```java
Scanner sc = new Scanner(System.in);
System.out.println("월을 입력 해주세요 : ");
int month = sc.nextInt();
		
switch(month) {
case 12 :
case 1 :
case 2 :
	System.out.println("겨울");
	break;
case 3 :
case 4 :
case 5 :
	System.out.println("봄");
	break;
case 6 :
case 7 :
case 8 :
	System.out.println("가을");
	break;
case 9 :
case 10 :
case 11 :
	System.out.println("가을");
	break;
default : System.out.println("해당하는 계절이 없습니다.");
}
```

> #### Q3. 연산 프로그램 만들기
* 사용자로부터 피연산자1,2,연산자를 입력받아 계산을 출력해줍니다.
* 음수는 "잘못 입력하셨습니다. 프로그램을 종료합니다."를 출력 합니다.

```java
Scanner sc = new Scanner(System.in);
		
System.out.println("피연산자1 입력 : ");
Double num1 = sc.nextDouble();

System.out.println("피연산자2 입력 : ");
Double num2 = sc.nextDouble();

sc.nextLine();
		
System.out.println("연산자를 입력(+,-,*,/,%) : ");
String op = sc.nextLine();
		
// if문
if(num1>0 && num2>0) {
if(op.equals("+")) {
		System.out.printf("%f %s %f = %f", num1, op, num2, num1+num2);
	} else if(op.equals("-")) {
		System.out.printf("%f %s %f = %f", num1, op, num2, num1-num2);
	} else if(op.equals("*")) {
		System.out.printf("%f %s %f = %f", num1, op, num2, num1*num2);
	} else if(op.equals("/")) {
		System.out.printf("%f %s %f = %f", num1, op, num2, num1/num2);
	} else if(op.equals("%")) {
		System.out.printf("%f %s %f = %f", num1, op, num2, num1%num2);
	} else {
		System.out.println("잘못 입력하셨습니다. 프로그램을 종료합니다.");
	}
} else {
	System.out.println("잘못 입력하셨습니다. 프로그램을 종료합니다.");
}

  // switch문
//if(num1>0 && num2>0) {
//	switch(op) {
//	case "+" : 
//		System.out.printf("%f %s %f = %f", num1, op, num2, num1+num2); break;
//	case "-" : 
//		System.out.printf("%f %s %f = %f", num1, op, num2, num1-num2); break;
//	case "*" : 
//		System.out.printf("%f %s %f = %f", num1, op, num2, num1*num2); break;
//	case "/" : 
//		System.out.printf("%f %s %f = %f", num1, op, num2, num1/num2); break;
//	case "%" : 
//		System.out.printf("%f %s %f = %f", num1, op, num2, num1%num2); break;
//	default : 
//		System.out.println("잘못 입력하셨습니다. 프로그램을 종료합니다.");
//	} else {
//		System.out.println("잘못 입력하셨습니다. 프로그램을 종료합니다.");
//}
```


#
> ### switch문과 if문의 차이점
1. if : 조건식을 복잡하게 기술 가능, 값의 범위를 설정 가능
2. switch : 조건식 불가, 확실한 값만 기술 가능 (동등 비교만 수행)
