#include <stdio.h>
#include "LPC17xx.H" /* LPC17xx definitions */
#include "GLCD.h"
#include "Serial.h"
#define __FI 1 /* Font index 16x24 */
void ZigbeeMeshTX_Init(void)
{
/*user may configure zigbee by entering below AT commands in any serial terminal 
using RS232 cable*/
/*To check whether Zigbee is configured or not you can use hyperterminal or any serial 
port/terminals by entering the commands in tx in serial window of PC to zigbee using RS232 
cable*/
SER_SendString("+++"); /* To enter AT command mode */
SER_SendString("ATNDA00003000\r"); /* This 
command sets the Destination address as 00003000 */
SER_SendString("ATGWR\r"); /* Write to flash */
SER_SendString("ATNUD00002000\r"); /* This 
command sets the Source address as 00002000 */
SER_SendString("ATGWR\r"); /* Write to flash */
SER_SendString("ATNCHF\r"); 
/* This command sets the CHANNEL as 0F */
SER_SendString("ATSBD3\r"); 
/* This command sets the baud as 9600 */
SER_SendString("ATGWR\r"); /* Write to flash */
 
SER_SendString("ATNPI00001111\r"); /* This 
command sets the Personal Area Network ID/address as 00001111 */
SER_SendString("ATGWR\r"); 
/* Write to flash */
SER_SendString("ATGEX\r"); /* To Exit AT command mode*/
}
/*----------------------------------------------------------------------------
 Main Program
*----------------------------------------------------------------------------*/
int main (void) {
LPC_SC->PCONP|=(1<<15);
 SER_Init(); /* UART Initialization */
LPC_GPIO0->FIODIR |= 0x007f8000;
ZigbeeMeshTX_Init();
#ifdef __USE_LCD
 GLCD_Init(); /* Initialize graphical LCD */
 GLCD_Clear(White); /* Clear graphical LCD display */
 GLCD_SetBackColor(Blue);
 GLCD_SetTextColor(White);
 GLCD_DisplayString(0, 0, __FI, " MCB1700 Demo ");
 GLCD_DisplayString(1, 0, __FI, " Zigbee Mesh TX ");
 GLCD_DisplayString(2, 0, __FI, " www.keil.com ");
 GLCD_SetBackColor(White);
 GLCD_SetTextColor(Blue);
 GLCD_DisplayString(5, 0, __FI, "Tx character:");
GLCD_DisplayString(3, 0, __FI, "Press RESET to ");
GLCD_DisplayString(4, 0, __FI, "TRANSMIT");
#endif
 SysTick_Config(SystemCoreClock/100); /* Generate interrupt each 10 ms */
 while (1) 
{ /* Loop forever */
GLCD_DisplayChar(7, 4, __FI,SER_PutChar('G'));
}
}
