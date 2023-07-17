# qn-4-part-2-program digital IOs to control seven segment interface
#include "stm32f4xx_hal.h" 
void Init_Pushbutton(void);
void Init_leds(void);
int main(void)
{
   void Init_Pushbutton();
   void Init_leds();
   while(1)
   {
     if(HAL_GPIO_ReadPin(GPIOA,GPIO_PIN_0))
     {
HAL_GPIO_WritePin(GPIOD,GPIO_PIN_12|GPIO_PIN_13|GPIO_PIN_14|GPIO_PIN_15,GPIO_PIN_SET);
      }
      else
HAL_GPIO_WritePin(GPIOD,GPIO_PIN_12|GPIO_PIN_13|GPIO_PIN_14|GPIO_PIN_15,GPIO_PIN_RESET);
    }
  }

void Init_Pushbutton(void){
        	__HAL_RCC_GPIOA_CLK_ENABLE();
        	GPIO_InitTypeDef pushbutton;
        	pushbutton.Pin = GPIO_PIN_0;
        	pushbutton.Mode = GPIO_MODE_INPUT;
        	pushbutton.Pull = GPIO_NOPULL;
        	HAL_GPIO_Init(GPIOA, &pushbutton);
}
 
void Init_leds(void){
  __HAL_RCC_GPIOD_CLK_ENABLE();
  GPIO_InitTypeDef ledpins;
  ledpins.Pin = GPIO_PIN_12|GPIO_PIN_13|GPIO_PIN_14|GPIO_PIN_15;
  ledpins.Mode = GPIO_MODE_OUTPUT_PP;
  HAL_GPIO_Init(GPIOD, &ledpins);
}
