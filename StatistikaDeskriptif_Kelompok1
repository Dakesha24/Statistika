#include<stdio.h>
#include<stdlib.h>
#include<math.h>

//Prosedur untuk Mengurutkan data
void bubbleSort(int nilai[], int n) {
	int i,j,temp;
    for (i = 0; i < n-1; i++) {
        for (j = 0; j < n-i-1; j++) {
            if (nilai[j] > nilai[j+1]) {
                temp = nilai[j];
                nilai[j] = nilai[j+1];
                nilai[j+1] = temp;
            }
        }
    }
}

//Fungsi untuk menghitung rata-rata
double hitungRataRata(int nilai[], int n) {
    int i;
	double total = 0;
    for (i = 0; i < n; i++) {
        total += nilai[i];
    }
    return total/n;
}

//Fungsi untuk menghitung median
double hitungMedian(int nilai[], int n) {
	if (n==0) {
		return 0;
	}
    if (n % 2 == 0) {
        return (nilai[n / 2 - 1] + nilai[n / 2]) / 2.0;
    }else {
        return nilai[n / 2];
    }
}

//Fungsi untuk menghitung modus
int hitungModus(int nilai[], int n) {
    int modus = 0;
    int banyakKemunculan = 0;
	int i, j;
    for (i = 0; i < n; i++) {
        int temp = nilai[i];
        int hitungKemunculan = 0;

        for (j=0; j < n; j++) {
            if (nilai[j] == temp) {
                hitungKemunculan++;
            }
        }
        if (hitungKemunculan > banyakKemunculan) {
        	banyakKemunculan=hitungKemunculan;
        	modus=temp;
		}
    }
    return modus;
}

//Fungsi untuk menghitung variansi
double hitungVariansi(int nilai[], int n) {
	int i;
	if(n==0){
		return 0;
	}
    double mean = hitungRataRata(nilai, n);
    double jumlah = 0;
    for (i = 0; i < n; i++) {
        jumlah += pow(nilai[i] - mean, 2);
    }
    return jumlah / (n-1);
}

//Fungsi untuk menghitung simpangan baku
double hitungSimpanganBaku(int data[], int n) {
    return sqrt(hitungVariansi(data, n));
}

//Fungsi untuk mencari desil
double cariDesil(int nilai[], int n, double desil, double* letakData) {
    int posisi = (int)(desil * (n + 1) / 10);
    double selisih = desil * (n + 1) / 10 - posisi;
    if (posisi == 0) {
        *letakData = 1.0;
        return nilai[0] + selisih * (nilai[1] - nilai[0]);
    } else if (posisi == n) {
        *letakData = n;
        return nilai[n - 1] + selisih * (nilai[n - 1] - nilai[n - 2]);
    } else {
        *letakData = posisi + selisih;
        return nilai[posisi - 1] + selisih * (nilai[posisi] - nilai[posisi - 1]);
    }
}

//Fungsi untuk mencari persentil
double cariPersentil(int nilai[], int n, double persentil, double* letakData) {
    int posisi = (int)(persentil * (n + 1) / 100);
    double selisih = persentil * (n + 1) / 100 - posisi;
    if (posisi == 0) {
        *letakData = 1.0;
        return nilai[0] + selisih * (nilai[1] - nilai[0]);
    } else if (posisi == n) {
        *letakData = n;
        return nilai[n - 1] + selisih * (nilai[n - 1] - nilai[n - 2]);
    } else {
        *letakData = posisi + selisih;
        return nilai[posisi - 1] + selisih * (nilai[posisi] - nilai[posisi - 1]);
    }
}

int main() {
    int n;
    printf("Masukkan jumlah data: ");
    scanf("%d", &n);

    int nilai[n];
    printf("Masukkan data:\n");
    int i;
    for (i = 0; i < n; i++) {
        scanf("%d", &nilai[i]);
    }
    
    // Mengurutkan data
    bubbleSort(nilai, n);
    
    //print data yang telah diurutkan
    printf("\n\nData yang sudah diurutkan: \n");
    for (i = 0; i < n; i++) {
        printf("%d ", nilai[i]);
    }
    printf("\n\n");

    //Menghitung dan menampilkan hasil
    double rataRata = hitungRataRata(nilai, n);
    double median = hitungMedian(nilai, n);
    int modus = hitungModus(nilai,n);
    double simpanganBaku = hitungSimpanganBaku(nilai, n);
    double variansi = hitungVariansi(nilai, n);
    double desil;
    double persentil;
    
    printf("HASIL\n\n");

    printf("Rata-rata: %.2lf\n", rataRata);
    printf("Median: %.2lf\n", median);
    printf("Modus: %d\n\n", modus);
    
    printf("Variansi: %.2lf\n", variansi);
	printf("Simpangan Baku: %.2lf\n\n\n", simpanganBaku);
    
	//mencari desil
	printf("Masukkan desil yang ingin Anda cari (0-9): ");
	scanf("%lf", &desil);
	if (desil >= 0 && desil <= 9) {
	    double letakDataDesil;
	    double hasilDesil;
		hasilDesil = cariDesil(nilai, n, desil, &letakDataDesil);
	    printf("\nDesil ke %.1lf \n(Letak data %.1lf) = %.2lf\n", desil, letakDataDesil, hasilDesil);
	} else {
	    printf("Desil harus dalam rentang 0 hingga 9.\n");
	}
    printf("\n\n");
    
    //mencari persentil
	printf("Masukkan persentil yang ingin Anda cari (0-100): ");
	scanf("%lf", &persentil);
	if (persentil >= 0 && persentil <= 100) {
	    double letakDataPersentil;
	    double hasilPersentil = cariPersentil(nilai, n, persentil, &letakDataPersentil);
	    printf("\nPersentil ke %.1lf \n(Letak data %.1lf) = %.2lf\n", persentil, letakDataPersentil, hasilPersentil);
	} else {
	    printf("Persentil harus dalam rentang 0 hingga 100.\n");
	}

    return 0;
}
