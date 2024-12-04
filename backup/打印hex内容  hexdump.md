```c
void hexdump(uint8_t *buf, uint32_t len)
{
    int i = 0;

    printf("----------------------hexdump------------------------");
    for(i = 0; i < len; i++) {
        printf("%02x ", buf[i]);
        if( (i+1) % 16 == 0) {
            printf("\n");
        }
    }

    if(i%16 != 0) {
        printf("\n");
    }

    printf("---------------------hexdump-------------------------\n");
}

``` 