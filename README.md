# Embedded-Systems-
Lab 2

# Question 2
#include <msp430.h> 


/**
 * main.c
 */

int main(void)
{
    WDTCTL = WDTPW | WDTHOLD;   // stop watchdog timer



   int a = 0b1000111100;
   int b = 0b1000100001;

   int d = sum(a,b);

   //while(1)
   //return(0)

}


int sum (int x, int y){
    int z;

    z = x+y;

    return z;
}

#QUESTION 3

;-------------------------------------------------------------------------------
; Main loop here
;-------------------------------------------------------------------------------
			mov.b #0001h, R4;
            mov.b #0001h, R5;
            mov.b #0001h, R6;

            and R6, R4;
            and R6, R5;

            cmp R4, R6;
            jeq R4eqR6;
            jmp $;


R4eqR6:
            cmp R5, R6;
            jeq R5eqR6;
            jmp $;


R5eqR6:
            mov.w #0ff0h, R9;
            jmp $;
            
            
# QUESTION 5

mov.w #0004h, R4
			mov.w #0005h, R5
			cmp R5,R4

			jl less
			jge greater

			jmp $

less:
			call #less_function
			jmp $

greater:
			call #greater_function
			jmp $

less_function:

			mov.w #000Ah, &2000h
            mov.w #9h , &2002h
            mov.w #8h , &2004h
            mov.w #7h , &2006h
            mov.w #6h , &2008h
            sub #1h,R4
            ret;




greater_function:

			mov.w #0001h , &2010h
            mov.w #2h ,  &2002h
            mov.w #3h , &2004h
            mov.w #4h , &2006h
            mov.w #5h , &2008h
			sub #1h,R4


			ret
      
      
 #Question 6
 
 			mov.w #2D97h, R3
            mov.w #6239h, R4
            mov.w #0001h, R5

            call #and_or



and_or:
    bic.b R3, R4
    bis R4, R5
    mov.w R5, &203Ch
    ret;
