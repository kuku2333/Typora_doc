# xzdtx代码编写规范

## 变量名

1. 模块名用大写。
2. 下划线分割每个词，驼峰。
3. 命名要说清楚功能或者作用，太长就写缩写，在上写注释，解释意思。

## 函数参数

1. 小写。
2. 要分隔。

```c
int32_t AT24C02_Write(uint8_t word_addr, uint8_t *buf, uint8_t len)
```

## 函数体（复合语句）

1. 各种变量定义在函数开头。

2. 不同功能语句块，要隔行。

3. 需要注释的语句块，在其上用/**/进行编写，同时也可以在语句后面用//写，以补充解释。

   ```c
   /*	手册描述：当SCL为高电平时SDA的下降沿（高到低）
   	叫做起始条件。
   	所以，先把两根线都置高，表示空闲状态，再让数据
   	线置低，这时时钟线还是高，就是在告诉从机开始了，
   	最后再做一个时钟线置低操作。
   */
   SDA_W(Bit_SET);//数据线高
   SCL_W(Bit_SET);//时钟线高
   Delay_us(5);
   ```

   

4. 异常处理的语句，必须紧跟产生源。

   ```c
   //等待从机的应答
   ack = IIC_Wait_Slave_Ack();
   if(ack)
   {
       printf("word address fail\r\n");
   
       return -2;
   }
   ```

5. 运算符和操作数要以空格分开。

   ```c
   ack = IIC_Wait_Slave_Ack();
   ```

6. for循环的变量在括号里声明&定义。

   ```c
   for(int32_t i = 0; i < len - 1; i++)
   {
   	buf[i] = IIC_Recv_Byte();
   	printf("buf[%d]:%d\r\n", i, buf[i]);
   }
   ```

7. 函数的括号要对齐。

   ```c
   void mian(void)
   {
   	return 0;
   }
   ```

8. 要把if和else的括号都写好。

   ```c
   if(ack)
   {
   	SDA_W(Bit_SET);
   }
   else
   {
   	SDA_W(Bit_RESET);
   }
   ```

   不要这样写：

   ```c
   if(ack) return ack;
   else return !ack;
   ```

9. 

10. 

11. 

12. 

13. 

14. 

15. 

    

