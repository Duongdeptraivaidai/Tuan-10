# Buổi 1
### Bài 1: (Liệt kê số chính phương) Nhập số nguyên dương n (n>0). Liệt kê n số chính
phương đầu tiên.
Ví dụ:
Hay nhap so nguyen duong: 5. 5 so chinh phuong dau tien: 4 9 16 25 36
```c
#include<iostream>
#include<cmath>
using namespace std;

int TinhSoChinhPhuong(int n);
int TinhSoChinhPhuong(int n) {
	int num = 1;
	while (n > 0) {
		int can = sqrt(num);
		if (can * can == num) {
			cout << num << " ";
			n--;
		}
		num++;
	}
	return 0;
}

int main() {
	int n;
	cout << "Nhap vao mot so nguyen duong: ";
	cin >> n;
	
	TinhSoChinhPhuong(n);

}
```
#### Bài 2: (Đếm số lượng số hoàn hảo) Nhập số nguyên dương n (n>0). Cho biết có bao
nhiêu số hoàn thiện nhỏ hơn n.
Ví dụ:
Hay nhap so nguyen duong:
3
So luong so hoan hao nho hon 3: 0
Hay nhap so nguyen duong:
36
So luong so hoan hao nho hon 36: 2
```c
#include<iostream>
using namespace std;
int dem(int n, int count);

bool KtSoHoanHao(int num) {
	int sum = 0;
	for (int i = 1; i <= num / 2; i++) {
		if (num % i == 0) {
			sum += i;
		}
	}return sum == num;
}
int dem(int n, int count) {
	for (int i = 2; i < n; i++) {
		if (KtSoHoanHao(i)) {
			count++;
		}
	}return count;
}

int main() {
	int n,count=0;
	cout << "Hay nhap vao mot so nguyen duong: "; cin >> n;
	cout << "So luong so hoan hao nho hon " << n << " la: " << dem(n, count);
	return 0;
}
```
#### Bài 3: (Tam giác) Nhập vào tọa độ 3 điểm A, B, C và kiểm tra xem chúng có phải là 3
đỉnh của một tam giác hay không? Nếu có hãy tính diện tích, chiều dài mỗi đường cao
của tam giác và in kết quả ra màn hình.
Công thức tính diện tích 𝑠 = 𝑝(𝑝 − 𝑎)(𝑝 − 𝑏)(𝑝 − 𝑐)
Công thức tính các đường cao: ℎa= 2s/a ; hb = 2s/b ; hc = 2s/c
(Với ) 𝑝 = (𝑎+𝑏+𝑐)/2: là nữa chu vi của tam giác a,b,c là chiều dài 3 cạnh.
```c
#include<iostream>
#include<cmath>
using namespace std;

bool TamGiac(float a, float b, float c) {
	if (a + b > c && a + c > b && b + c > a) return 1;
	else return 0;
}

void TinhToan(int a, int b, int c, int& p, int& S, int& ha, int& hb, int& hc) {
	p = (a + b + c) / 2;
	S = sqrt(p * (p - a) * (p - b) * (p - c));
	ha = (2 * S) / a;
	hb = (2 * S) / b;
	hc = (2 * S) / c;
}

int main() {
	float a, b, c;
	cout << "Nhap vao do dai ba canh tam giac: " << endl;
	cout << "Canh A: "; cin >> a;
	cout << "Canh B: "; cin >> b;
	cout << "Canh C: "; cin >> c;

	int p, S, ha, hb, hc;
	if (TamGiac(a, b, c))  TinhToan(a, b, c, p, S, ha, hb, hc);
	else return 1; 
	
	cout << "Dien tich tam giac la: " << S << endl;
	cout << "Nua chu vi tam giac la: " << p << endl;
	cout << "Duong cao ha la: " << ha << endl;
	cout << "Duong cao hb la: " << hb << endl;
	cout << "Duong cao hc la: " << hc;
	return 0;
}
```
#### Bài 4: (Tìm ước chung và bội chung) Viết chương trình nhập vào 2 số nguyên dương a
và b. Tìm ước số chung lớn nhất và bội số chung nhỏ nhất của 2 số vừa nhập.
```c
#include<iostream>
using namespace std;

int gcd(int a, int b) {
	while (b != 0) {
		int temp = b;
		b = a % b;
		a = temp;
	}
	return a;
}

int lcm(int a, int b) {
	return a / gcd(a, b) * b;
}
int main() {
	int a, b;
	cout << "Nhap hai so: ";
	cin >> a >> b;
	int gcdresult = gcd(a, b);
	int lcmresult = lcm(a, b);
	cout << "Uoc chung lon nhat: " << gcdresult << endl;
	cout << "Boi chung nho nhat: " << lcm << endl;
	return 0;
}
```
#### Bài 5: Viết hàm trả về số lớn nhất trong 2 số nguyên bất kỳ. Dùng hàm này tìm số lớn
nhất trong:
a. 3 số nhập vào.
b. 4 số nhập vào.
```c
#include<iostream>
using namespace std;

int Solonnhat(int a, int b) {
	return (a > b) ? a : b;
	
}
int main() {
	int a, b;
	cout << "Nhap vao 2 so a,b: ";
	cin >> a >> b;

	int max = Solonnhat(a, b);
	cout << "So lon nhat la: " << Solonnhat(a, b);
	return 0;
}
```
#### Bài 6: Viết hàm kiểm tra số n có phải số nguyên tố hay không? Dùng hàm này để thực
hiện lần lượt các công việc sau:
Nhập vào số nguyên k, cho biết k có phải số nguyên tố không?
Xuất lên màn hình các số nguyên tố thuộc đoạn từ 1 đến k
Xuất k số nguyên tố đầu tiên
Ví dụ: Nhap 8, Xuat 8 khong phai so nguyen to
Cac so nguyen to tu 1-8: 2 3 5 7
8 so nguyen to dau tien la: 2 3 5 7 11 13 17 19
```c
#include <iostream>

using namespace std;

int primes[10000001];

void sievePrime() {
  //coi tat ca so deu la so nguyen to
  //primes [i] = 1; la so nt
  //primes [i] = 0; khong la so nt
  for (int i = 0; i <= 1000000; i++) {
    primes[i] = 1;
  }
  primes[0] = primes[1] = 0;
  for (int i = 2; i <= 1000; i++) {
    //neu i la so nt 
    if (primes[i]) {
      //duyet cac boi cua i va cho la 0
      for (int j = i*i; j <= 1000000; j+=i) {
        primes[j] = 0; // j khong con la so nt
      }
    }
  }
}

int main() {
  sievePrime();
  int n;
  cin >> n;

  if (primes[n]) cout << n << " la so nguyen to";
  else cout << n << " khong phai la so nguyen to";

  cout << "\nCac so nguyen to tu 1 - " << n << ": ";
  for (int i = 0; i <= n; i++) {
    if (primes[i]) cout << i << " ";
  }

  cout << endl << n << " so dau tien la: ";
  int count = 0;
  for (int i = 0; i <= 1000000; i++) {
    if (primes[i]) {
      cout << i << " ";
      count++;
    }
    if(count == n) break;
  }
  return 0;
}
```


