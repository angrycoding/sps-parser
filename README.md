#  💜If you like my projects, you can support me.

| Coin/Symbol | Network | Adress |
|------|---------|--------|
| Bitcoin (BTC) | BTC | 1LU7DtLiKkWe3aAXbhRhNAMUFdrapWuAHW |
| Tether (USDT) | TRC20 | TK7f7TXozWVbkHxdArAJd2rELu725q1Ac5 |
| Tether (USDT) | TON | UQDI4e7xm_B7O_REaYd5CoyEz1Ki08t0EPlUim022_K9B2xa |


# sps-parser
H.264 sequence param parser (sps) written in pure C with no dependencies.
Sequence parameter set is decribed somewhere in here: https://tools.ietf.org/html/rfc3984 (see below for more detailed format description).
Primary use is for obtaining stream dimensions, but you can take it as a boilerplate and extract anything you need (fps and god knows what else is there).  Usage:

```c
int main(int argc , char *argv[]) {
	uint8_t buffer[] = "J00AH41qBQBboQAAAwABAAADADKE";
	uint32_t dimensions = sps_parser(buffer);
	// 1280x720
	printf("width = %d\nheight = %d\n", dimensions >> 16, dimensions & 0xFFFF);

	strcpy(buffer, "J00AH41qCwEmhAAAAwAEAAADAMoQ");
	dimensions = sps_parser(buffer);
	// 704x576
	printf("width = %d\nheight = %d\n", dimensions >> 16, dimensions & 0xFFFF);

	strcpy(buffer, "J00AH41qCwPaEAAAAwAQAAADAyhA");
	dimensions = sps_parser(buffer);
	// 704x480
	printf("width = %d\nheight = %d\n", dimensions >> 16, dimensions & 0xFFFF);
}
```

![SPS in details](https://raw.githubusercontent.com/angrycoding/sps-parser/master/sps.png)

