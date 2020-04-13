# sps-parser
H.264 sequence param parser (sps) written in pure C with no dependencies.

usage:

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
