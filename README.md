# -  #include <iostream>
#include <stdlib.h>
#include <math.h>

int main()
{
	system("chcp 1251");
	system("cls");

	int max = 0;
	int min = 0;
	int n = 0;
	int count = 0;

	double num = 0;
	int res = 0;

	double sum = 0;

	double* mas;

	do {
		int ch=0;
		printf("Введите размер массива: ");
		count = scanf_s("%d", &n);
		while (ch = getchar() != '\n');
	} while ((count < 1)||(n<0)||(n==0));

	mas = (double*)malloc(n * sizeof(double));

	do {
		do {
			int ch = 0;
			printf("Введите минимальную границу: ");
			count = scanf_s("%d", &min);
			while (ch = getchar() != '\n');
		} while (count < 1);

		do {
			int ch = 0;
			printf("Введите максимальную границу: ");
			count = scanf_s("%d", &max);
			while (ch = getchar() != '\n');
		} while (count < 1);
	} while ((min > max)||(min==max));
	
	for (int i = 0; i < n; i++)
	{
		mas[i] = (((double)rand()) / RAND_MAX) * (max - min) + min;
	}

	for (int i = 0; i < n; i++) {
	  num = ((mas[i] - trunc(mas[i])) * pow(10, 6));
	  res = (int)num;
	  while (res % 10 == 0) res = res / 10;

	  for (int j = 0; j < n; j++) {
		  if (res == j) {
			  sum = sum - mas[i];
			  mas[i] = 0;
		  }

	  }
	}

	for (int i = 0; i < n; i++)
		sum = sum + mas[i];

	printf_s("%f", sum);

	free(mas);

	return 0;
}
