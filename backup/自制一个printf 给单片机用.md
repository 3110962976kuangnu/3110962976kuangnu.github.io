```c
#include <stdio.h>
#include "stdint.h"
#include <stdarg.h>

int my_printf(const char *format, ...) {
    staitc char tmp_str[100] = {0};
    va_list args;
    va_start(args, format);
    uint8_t len = vsprintf(tmp_str, format, args);
    va_end(args);

//    长度为 len   内容在 tmp_str中

//    uart_send_buf(串口, tmp_str,len);
    printf("str len->%d str is [%s]\n", len, tmp_str);
    return 0;

}


int main(void) {
    printf("Hello, World!\n");
    my_printf("hello world %d\n",100);
    return 0;
}
``` 