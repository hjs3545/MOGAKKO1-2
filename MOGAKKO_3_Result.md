1.조건문
1.1 if문

1.2 if-else문

1.3 중첩 if문

if (조건식1) {
		// 조건식1의 연산결과가 참일 때 수행될 문장들을 적는다.
    if (조건식2){    
    		// 조건식1과 조건식2가 모두 참일 때 수행될 문장들	
	} else {
		// 조건식1이 참이고, 조건식2가 거짓일 때 수행되는 문장들
	}
} else {
		// 조건식1이 거짓일 때 수행되는 문장들
}
 

1.4 switch문

 

2.반복문
2.1 for문

for (초기화;조건식;증감식){
	// 조건식이 참일 때 수행될 문장들을 적는다.
}
2.2 while문

while(조건식){
	//조건식의 연산결과가 참(0이 아닌 값)인 동안, 반복될 문장들을 적는다.
}

while문의 조건식은 생략 할 수 없다.
2.3 do-wihle문

do {
	// 조건식의 연산결과가 참일 때 수행될 문장들을 적는다.
} while(조건식) ;

do while문은 최소한 한 번은 수행될 것이 보장된다.
2.4 break문

2.5 continue문

2.6 goto문

goto문은 실행흐름을 지정된 곳으로 이동시킨다. break문과 continue문은 switch문이나 반복문 내에서만 사용가능하다는 조건이 있지만, goto문은 함수의 블럭{} 안이라면 어디서든 쓸 수 있다. goto문의 형식은 다음과 같다.

goto 레이블이름;  //지정된 레이블로 이동

goto문으로 이동할 곳의 위치는 '레이블(label)'로 지정하며 다음과 같은 형식을 사용한다.

레이블이름 :
 goto문 연습

#include <stdio.h>                                                           
#include <stdlib.h>                                                          
#include <time.h>                                                            
                                                                             
int main(void) {                                                             
	int num1, num2;                                                      
	int sum = 0;                                                         
                                                                             
	srand(time(NULL)); // 난수를 초기화                                      
                                                                             
 roll_again:                                                                  
	num1 = rand() % 6 + 1;   // 1~6범위의 임의의 수를 얻어서 num1에 저장          
	num2 = rand() % 6 + 1;                                               
                                                                             
	printf("num1=%d, num2=%d \n", num1, num2);                           
                                                                             
	sum += num1 + num2;                                                  
                                                                             
	if (num1==num2)     	// num1과 num2의 값이 같으면 다시 주사위를 굴린다.             
		goto roll_again; // roll_again이란 이름의 레이블로 이동             
                                                                             
	printf("sum=%d\n", sum);                                             
                                                                             
	return 0;                                                            
}
중첩 반복문 벗어나기

#include <stdio.h>                                                                                         
#include <math.h>                                                                                          
                                                                                                           
int main(void) {                                                                                           
	int menu;                                                                                          
	int num;                                                                                           
                                                                                                           
	while(1) {                                                                                         
		printf("(1) square\n");                                                                    
		printf("(2) square root\n");                                                               
		printf("(3) log\n");                                                                       
		printf("원하는 메뉴(1~3)를 선택하세요.(종료:0)>");                                                 
		scanf("%d", &menu);                                                                        
                                                                                                           
		if(menu==0) {  // if(!menu) {                                                              
			printf("프로그램을 종료합니다.\n");                                                      
			break;                                                                             
		} else if (!(1<= menu && menu <= 3)) {                                                     
			printf("메뉴를 잘못 선택하셨습니다.(종료는 0)\n");                                          
			continue;		                                                           
		}                                                                                          
                                                                                                           
                                                                                                           
		for(;;) {                                                                                  
			printf("계산할 값을 입력하세요.(계산 종료:0, 전체 종료:-1)>");                                
			scanf("%d", &num);                                                                 
                                                                                                           
			if(num==0)  break;      // 계산 종료. for문을 벗어난다.                                  
			if(num==-1) goto exit;  // 전체 종료. for문과 while문을 모두 벗어난다.                      
                                                                                                           
			switch(menu) {                                                                     
				case 1: printf("result=%d\n",  num*num);	break;                     
				case 2: printf("result=%lf\n", sqrt((double)num)); break;                  
				case 3: printf("result=%lf\n", log((double)num));  break;                  
			}                                                                                  
		} // for(;;)                                                                               
	}                                                                                                  
                                                                                                           
	exit:                                                                                              
	return 0;                                                                                          
}