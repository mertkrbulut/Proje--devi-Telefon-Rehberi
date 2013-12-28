#include <stdio.h>
#include <stdlib.h>
#include <string.h>
#include <conio.h>  
#include <Windows.h>  


struct kisi_listesi {   //Telefon bilgileri
	char adi[20];
	char soyadi[20];
	char ceptel_num[12];
	char istel_num[12];
	char evtel_num[12];
	char eposta[30];
	char dogum[12];
};

                        //fonksiyonlar
void anaMenu();
void kisiEkle();
void goruntule();
void guncelle();
void isim_guncelle();
void soyisim_guncelle();
void eposta_guncelle();
void sil();
void arama();
void addan_arama();
void soydan_arama();
void nodan_arama();
void epostadan_arama();
void dogum_arama();
void isten_arama();
void evden_arama();
                        //Ana Menü fonksiyonu
void main()
{
	HWND hWnd = GetConsoleWindow();
 ShowWindow(hWnd,SW_SHOWMAXIMIZED);  
	anaMenu();
	getch();

}
void anaMenu()

{
	int secenek;
while(1)
{
printf("\t\t\t     <<<TELEFON REHBERI>>> \n\n");
printf("1-KISI EKLE\n");
printf("2-REHBER GORUNTULE\n");
printf("3-KISI GUNCELLE\n");
printf("4-KISI SIL\n");
printf("5-KISI ARA\n");
printf("6-CIKIS");


printf("\n\nSecenek giriniz 1<>6 :");
scanf("%d", &secenek);
if(secenek<1 || secenek>6)
		{
			printf("Lutfen 1-6 arasi secim giriniz...\n ");
			continue;
		}
		
else
		{
			if(secenek==1)
				kisiEkle();
			else if(secenek==2)
				goruntule();
			else if(secenek==3)
				guncelle();
			else if(secenek==4)
				sil();
			else if(secenek==5)
				arama();
			else if(secenek==6)
				break;
         }


}

}


//Kişi ekle fonksiyonu
void kisiEkle()
{
	int secenek2;
struct kisi_listesi kisiler;
FILE *ptliste;
ptliste=fopen("mertrehber.txt","a");
if (ptliste == NULL)
{
	printf("Dosya açilmadi !");
}

else
{printf("\t\t\t   <<KISI EKLE>>\n");
printf("\nAD max[20] :");
scanf("%s",kisiler.adi);
printf("\nSOYAD max[20] :");
scanf("%s",kisiler.soyadi);
printf("\nCEP TEL max[11] :");
scanf("%s",kisiler.ceptel_num);
printf("\nIS TEL max[11] :");
scanf("%s",kisiler.istel_num);
printf("\nEV TEL max[11] :");
scanf("%s",kisiler.evtel_num);
printf("\nE-POSTA max[20] :");
scanf("%s",kisiler.eposta);
printf("\nDOGUM TARIHI [gg/aa/yyyy] :");
scanf("%s",kisiler.dogum);
fprintf(ptliste,"%s\t%s\t%s\t%s\t%s\t%s\t%s\n",kisiler.adi,kisiler.soyadi,kisiler.ceptel_num,kisiler.istel_num,kisiler.evtel_num,kisiler.eposta,kisiler.dogum);
printf("\n%s %s kisisini basariyla eklediniz...",kisiler.adi, kisiler.soyadi);
fclose(ptliste);
}


printf("\n\nTekrar kisi eklemek icin 1'e\nAna Menuye donmek icin 2'ye basin.\n\n");
printf("1<>2 :");
scanf("%d", &secenek2);

if(secenek2<1 || secenek2>2)
		{
			printf("1 veya 2'ye basiniz. \n");
		}
		
else
		{
			if(secenek2==1)
				kisiEkle();
			else if(secenek2==2)
				anaMenu();
        }


}

void goruntule()
{
	struct kisi_listesi kisiler;
	FILE *ptliste;
ptliste=fopen("mertrehber.txt","r");

		if (ptliste == NULL)
   {
	printf("Dosya açılmadı !");
   }
		else
		{
		
        while(fscanf(ptliste,"%s\t%s\t%s\t%s\t%s\t%s\t%s\n",kisiler.adi,kisiler.soyadi,kisiler.ceptel_num,kisiler.istel_num,kisiler.evtel_num,kisiler.eposta,kisiler.dogum)!=EOF)
		printf("AD :%s\t SOYAD :%s\t\nCEP TEL :%s\tIS TEL :%s\t\nEV TEL :%s\tE-POSTA :%s\nDOGUM TARIHI :%s\t\n\n",kisiler.adi,kisiler.soyadi,kisiler.ceptel_num,kisiler.istel_num,kisiler.evtel_num,kisiler.eposta,kisiler.dogum);
		fclose(ptliste);

		}
}

void guncelle()
{
	int secenek5;
		
printf("\t\t\t     <<<GUNCELLEME MENUSU>>> \n\n");
printf("1-ISMI GUNCELLE\n");
printf("2-SOYISIMI GUNCELLE\n");
printf("3-EPOSTA ADRESINI GUNCELLE\n");
printf("4-MENUYE DON\n");


printf("\n\nSecenek giriniz 1<4 :");
scanf("%d", &secenek5);
if(secenek5<1 || secenek5>4)
		{
			printf("Lutfen 1-4 arasi secim giriniz...\n ");
			
		}
		
switch(secenek5)
		{
			case 1:
				isim_guncelle();
				break;
			case 2:
				soyisim_guncelle();
				break;
			case 3:
				eposta_guncelle();
                break;
			case 4:
				anaMenu();
				break;
			default:
				guncelle();
				break;
}

}

void isim_guncelle()
{
	char guntel_num[12];
	char ad[20];
	struct kisi_listesi kisiler;
	FILE *ptliste;
	FILE *ptliste2;
	ptliste2=fopen("mertrehberguncel.txt","a");
	ptliste=fopen("mertrehber.txt","r");
	
	if(ptliste==NULL)
		printf("Dosya bulunamadi.");
	else
	{
		printf("Bilgilerini yenilemek istediginiz numarayi giriniz:");
		scanf("%s",&guntel_num);
		 
			printf("Yeni adi giriniz:");
			flushall();
			gets(ad);

			while(fscanf(ptliste,"%s\t%s\t%s\t%s\t%s\t%s\t%s\n",kisiler.adi,kisiler.soyadi,kisiler.ceptel_num,kisiler.istel_num,kisiler.evtel_num,kisiler.eposta,kisiler.dogum)!=EOF)
			{
				if(strcmp(kisiler.ceptel_num,guntel_num)!=0)
				{
					fprintf(ptliste2,"%s\t%s\t%s\t%s\t%s\t%s\t%s\n",kisiler.adi,kisiler.soyadi,kisiler.ceptel_num,kisiler.istel_num,kisiler.evtel_num,kisiler.eposta,kisiler.dogum);
				}
				else
				{
					strcpy(kisiler.adi,ad);
					fprintf(ptliste2,"%s\t%s\t%s\t%s\t%s\t%s\t%s\n",kisiler.adi,kisiler.soyadi,kisiler.ceptel_num,kisiler.istel_num,kisiler.evtel_num,kisiler.eposta,kisiler.dogum);
					printf("\n\n%s Numarali kisinin ismini %s olarak degistirdiniz.\n", kisiler.ceptel_num, kisiler.adi);
			
				}
			}	

	}
	
					fclose(ptliste);
					fclose(ptliste2);
					remove("mertrehber.txt");
					rename("mertrehberguncel.txt","mertrehber.txt");			
	
	}

void soyisim_guncelle()
{
	char guntel_num[12];
	char soyad[20];
	struct kisi_listesi kisiler;
	FILE *ptliste;
	FILE *ptliste2;
	ptliste2=fopen("mertrehberguncel.txt","a");
	ptliste=fopen("mertrehber.txt","r");
	
	if(ptliste==NULL)
		printf("Dosya bulunamadi.");
	else
	{
		printf("Bilgilerini yenilemek istediginiz numarayi giriniz:");
		scanf("%s",&guntel_num);

			printf("Yeni soyadi giriniz:");
			flushall();//verileri doğrudan diske yazma
			gets(soyad);

			while(fscanf(ptliste,"%s\t%s\t%s\t%s\t%s\t%s\t%s\n",kisiler.adi,kisiler.soyadi,kisiler.ceptel_num,kisiler.istel_num,kisiler.evtel_num,kisiler.eposta,kisiler.dogum)!=EOF)
			{
				if(strcmp(kisiler.ceptel_num,guntel_num)!=0)
				{
					fprintf(ptliste2,"%s\t%s\t%s\t%s\t%s\t%s\t%s\n",kisiler.adi,kisiler.soyadi,kisiler.ceptel_num,kisiler.istel_num,kisiler.evtel_num,kisiler.eposta,kisiler.dogum);
				}
				else
				{
					strcpy(kisiler.soyadi,soyad);
					fprintf(ptliste2,"%s\t%s\t%s\t%s\t%s\t%s\t%s\n",kisiler.adi,kisiler.soyadi,kisiler.ceptel_num,kisiler.istel_num,kisiler.evtel_num,kisiler.eposta,kisiler.dogum);
					printf("\n\n%s Numarali kisinin soyismini %s olarak guncellediniz.\n",kisiler.ceptel_num,kisiler.soyadi);
			
				}
			}	

	}
	
					fclose(ptliste);
					fclose(ptliste2);
					remove("mertrehber.txt");
					rename("mertrehberguncel.txt","mertrehber.txt");			
	
	}

void eposta_guncelle()
{
	char guntel_num[12];
	char e_posta[25];
	struct kisi_listesi kisiler;
	FILE *ptliste;
	FILE *ptliste2;
	ptliste2=fopen("mertrehberguncel.txt","a");
	ptliste=fopen("mertrehber.txt","r");
	
	if(ptliste==NULL)
		printf("Dosya bulunamadi.");
	else
	{
		printf("Bilgilerini yenilemek istediginiz numarayi giriniz:");
		scanf("%s",&guntel_num);

			printf("Yeni e-postayi giriniz:");
			flushall();
			gets(e_posta);

			while(fscanf(ptliste,"%s\t%s\t%s\t%s\t%s\t%s\t%s\n",kisiler.adi,kisiler.soyadi,kisiler.ceptel_num,kisiler.istel_num,kisiler.evtel_num,kisiler.eposta,kisiler.dogum)!=EOF)
			{
				if(strcmp(kisiler.ceptel_num,guntel_num)!=0)
				{
					fprintf(ptliste2,"%s\t%s\t%s\t%s\t%s\t%s\t%s\n",kisiler.adi,kisiler.soyadi,kisiler.ceptel_num,kisiler.istel_num,kisiler.evtel_num,kisiler.eposta,kisiler.dogum);
				}
				else
				{
					strcpy(kisiler.eposta,e_posta);
					fprintf(ptliste2,"%s\t%s\t%s\t%s\t%s\t%s\t%s\n",kisiler.adi,kisiler.soyadi,kisiler.ceptel_num,kisiler.istel_num,kisiler.evtel_num,kisiler.eposta,kisiler.dogum);
					printf("\n\n%s Numarali kisinin epostasini %s\nolarak guncellediniz.\n", kisiler.ceptel_num, kisiler.eposta);
			
				}
			}	

	}
	
					fclose(ptliste);
					fclose(ptliste2);
					remove("mertrehber.txt");
					rename("mertrehberguncel.txt","mertrehber.txt");			
	
	}


void addan_arama()
{
	struct kisi_listesi kisiler;
	FILE *ptliste;
	int i=0;
	char aranan[15];
	ptliste=fopen("mertrehber.txt","r");
	printf("ARANACAK KISININ ADI :\n");
	scanf("%s", &aranan);
	while(!feof(ptliste))
	{
	fscanf(ptliste,"%s\t%s\t%s\t%s\t%s\t%s\t%s\n",kisiler.adi,kisiler.soyadi,kisiler.ceptel_num,kisiler.istel_num,kisiler.evtel_num,kisiler.eposta,kisiler.dogum);
	i++;
	if(strcmp(aranan, kisiler.adi)== 0)
	{
	printf("AD :%s\t SOYAD :%s\t\nCEP TEL :%s\tIS TEL :%s\t\nEV TEL :%s\tE-POSTA :%s\nDOGUM TARIHI :%s\t\n\n",kisiler.adi,kisiler.soyadi,kisiler.ceptel_num,kisiler.istel_num,kisiler.evtel_num,kisiler.eposta,kisiler.dogum);
	}
	else
	{
	
	}
	
	
	}
	fclose(ptliste);
}

void soydan_arama()
{
struct kisi_listesi kisiler;
	FILE *ptliste;
	int i=0;
	char soyaranan[15];
	ptliste=fopen("mertrehber.txt","r");
	printf("ARANACAK KISININ SOYADI :\n");
	scanf("%s", &soyaranan);
	while(!feof(ptliste))
	{
	fscanf(ptliste,"%s\t%s\t%s\t%s\t%s\t%s\t%s\n",kisiler.adi,kisiler.soyadi,kisiler.ceptel_num,kisiler.istel_num,kisiler.evtel_num,kisiler.eposta,kisiler.dogum);
	i++;
	if(strcmp(soyaranan, kisiler.soyadi)== 0)
	{
	printf("AD :%s\t SOYAD :%s\t\nCEP TEL :%s\tIS TEL :%s\t\nEV TEL :%s\tE-POSTA :%s\nDOGUM TARIHI :%s\t\n\n",kisiler.adi,kisiler.soyadi,kisiler.ceptel_num,kisiler.istel_num,kisiler.evtel_num,kisiler.eposta,kisiler.dogum);
	}
	else{
	
	}
	
	
	}
	fclose(ptliste);
}


void nodan_arama()
{
struct kisi_listesi kisiler;
	FILE *ptliste;
	int i=0;
	char noaranan[15];
	ptliste=fopen("mertrehber.txt","r");
	printf("ARANACAK KISININ NUMARASI :\n");
	scanf("%s",&noaranan);
	while(!feof(ptliste))
	{
	fscanf(ptliste,"%s\t%s\t%s\t%s\t%s\t%s\t%s\n",kisiler.adi,kisiler.soyadi,kisiler.ceptel_num,kisiler.istel_num,kisiler.evtel_num,kisiler.eposta,kisiler.dogum);
	i++;
	if(strcmp(noaranan, kisiler.ceptel_num)== 0)
	{
	printf("AD :%s\t SOYAD :%s\t\nCEP TEL :%s\tIS TEL :%s\t\nEV TEL :%s\tE-POSTA :%s\nDOGUM TARIHI :%s\t\n\n",kisiler.adi,kisiler.soyadi,kisiler.ceptel_num,kisiler.istel_num,kisiler.evtel_num,kisiler.eposta,kisiler.dogum);
	}
	else{
	
	}
	
	
	}
	fclose(ptliste);
}

void evden_arama()
{
struct kisi_listesi kisiler;
	FILE *ptliste;
	int i=0;
	char evaranan[15];
	ptliste=fopen("mertrehber.txt","r");
	printf("ARANACAK KISININ EV NUMARASI :\n");
	scanf("%s",&evaranan);
	while(!feof(ptliste))
	{
	fscanf(ptliste,"%s\t%s\t%s\t%s\t%s\t%s\t%s\n",kisiler.adi,kisiler.soyadi,kisiler.ceptel_num,kisiler.istel_num,kisiler.evtel_num,kisiler.eposta,kisiler.dogum);
	i++;
	if(strcmp(evaranan, kisiler.evtel_num)== 0)
	{
	printf("AD :%s\t SOYAD :%s\t\nCEP TEL :%s\tIS TEL :%s\t\nEV TEL :%s\tE-POSTA :%s\nDOGUM TARIHI :%s\t\n\n",kisiler.adi,kisiler.soyadi,kisiler.ceptel_num,kisiler.istel_num,kisiler.evtel_num,kisiler.eposta,kisiler.dogum);
	}
	else{
	
	}
	
	
	}
	fclose(ptliste);
}

void isten_arama()
{
struct kisi_listesi kisiler;
	FILE *ptliste;
	int i=0;
	char isaranan[15];
	ptliste=fopen("mertrehber.txt","r");
	printf("ARANACAK KISININ IS NUMARASI :\n");
	scanf("%s",&isaranan);
	while(!feof(ptliste))
	{
	fscanf(ptliste,"%s\t%s\t%s\t%s\t%s\t%s\t%s\n",kisiler.adi,kisiler.soyadi,kisiler.ceptel_num,kisiler.istel_num,kisiler.evtel_num,kisiler.eposta,kisiler.dogum);
	i++;
	if(strcmp(isaranan, kisiler.istel_num)== 0)
	{
	printf("AD :%s\t SOYAD :%s\t\nCEP TEL :%s\tIS TEL :%s\t\nEV TEL :%s\tE-POSTA :%s\nDOGUM TARIHI :%s\t\n\n",kisiler.adi,kisiler.soyadi,kisiler.ceptel_num,kisiler.istel_num,kisiler.evtel_num,kisiler.eposta,kisiler.dogum);
	}
	else{
	
	}
	
	
	}
	fclose(ptliste);
}

void epostadan_arama()
{
struct kisi_listesi kisiler;
	FILE *ptliste;
	int i=0;
	char epostaaranan[15];
	ptliste=fopen("mertrehber.txt","r");
	printf("ARANACAK KISININ EPOSTA ADRESİ :\n");
	scanf("%s",&epostaaranan);
	while(!feof(ptliste))
	{
	fscanf(ptliste,"%s\t%s\t%s\t%s\t%s\t%s\t%s\n",kisiler.adi,kisiler.soyadi,kisiler.ceptel_num,kisiler.istel_num,kisiler.evtel_num,kisiler.eposta,kisiler.dogum);
	i++;
	if(strcmp(epostaaranan, kisiler.eposta)== 0)
	{
	printf("AD :%s\t SOYAD :%s\t\nCEP TEL :%s\tIS TEL :%s\t\nEV TEL :%s\tE-POSTA :%s\nDOGUM TARIHI :%s\t\n\n",kisiler.adi,kisiler.soyadi,kisiler.ceptel_num,kisiler.istel_num,kisiler.evtel_num,kisiler.eposta,kisiler.dogum);
	}
	else{}
	
	
	}
	fclose(ptliste);
}

void dogum_arama()
{
struct kisi_listesi kisiler;
	FILE *ptliste;
	int i=0;
	char dogumaranan[15];
	ptliste=fopen("mertrehber.txt","r");
	printf("ARANACAK DOGUM TARIHI [gg/aa/yyyy] :\n");
	scanf("%s",&dogumaranan);
	while(!feof(ptliste))
	{
	fscanf(ptliste,"%s\t%s\t%s\t%s\t%s\t%s\t%s\n",kisiler.adi,kisiler.soyadi,kisiler.ceptel_num,kisiler.istel_num,kisiler.evtel_num,kisiler.eposta,kisiler.dogum);
	i++;
	if(strcmp(dogumaranan, kisiler.dogum)== 0)
	{
	printf("AD :%s\t SOYAD :%s\t\nCEP TEL :%s\tIS TEL :%s\t\nEV TEL :%s\tE-POSTA :%s\nDOGUM TARIHI :%s\t\n\n",kisiler.adi,kisiler.soyadi,kisiler.ceptel_num,kisiler.istel_num,kisiler.evtel_num,kisiler.eposta,kisiler.dogum);
	}
	else{
	
	}
	
	
	}
	fclose(ptliste);
}

void arama()
{
	int secenek4;
		
printf("\t\t\t     <<<ARAMA MENUSU>>> \n\n");
printf("1-ISIMLE ARA\n");
printf("2-SOYISIMLE ARA\n");
printf("3-CEP NUMARAYLA ARA\n");
printf("4-EV NUMARAYLA ARA\n");
printf("5-IS NUMARAYLA ARA\n");
printf("6-E-POSTAYLA ARA\n");
printf("7-DOGUM TARIHIYLE ARA\n");
printf("8-MENUYE DON\n");


printf("\n\nSecenek giriniz 1<8 :");
scanf("%d", &secenek4);
if(secenek4<1 || secenek4>8)
		{
			printf("Lutfen 1-8 arasi secim giriniz...\n ");
			
		}
		
switch(secenek4)
		{
			case 1:
				addan_arama();
				break;
			case 2:
				soydan_arama();
				break;
			case 3:
				nodan_arama();
                break;
			case 4:
				evden_arama();
                break;
			case 5:
				isten_arama();
                break;
			case 6:
				epostadan_arama();
                break;
				case 7:
				dogum_arama();
                break;
			case 8:
				anaMenu();
				break;
			default:
				arama();
				break;
}
}

void sil()
{
	struct kisi_listesi kisiler;
FILE *ptliste;
FILE *ptliste3; //dosya işaretçileri tanımlama
char silinen[20];

printf("SILINECEK KISININ ADI :");
scanf("%s",&silinen);

ptliste=fopen("mertrehber.txt","r"); //bilgiler dosyadan okunacak.
ptliste3=fopen("silmemertrehber.txt","w"); //yeni bilgiler bu dosyaya yazılacak.

   while(!feof(ptliste)){

      fscanf(ptliste,"%s\t%s\t%s\t%s\t%s\t%s\t%s\n",kisiler.adi,kisiler.soyadi,kisiler.ceptel_num,kisiler.istel_num,kisiler.evtel_num,kisiler.eposta, kisiler.dogum);

      if(strstr(kisiler.adi,silinen)){//Silinecek ad bulununca dosyadan 1 kayıt daha okunur ve silinedek kayıt atlanmış olur.
      //strstr(rehber.ad,aranan) yerine strcmp(rehber.ad,aranan)==0 yazabiliriz.

           fscanf(ptliste,"%s\t%s\t%s\t%s\t%s\t%s\t%s\n",kisiler.adi,kisiler.soyadi,kisiler.ceptel_num,kisiler.istel_num,kisiler.evtel_num,kisiler.eposta, kisiler.dogum);

      }//silinecek ad bulunana kadar alt satırdaki fprintf okunan veriyi yeni dosyaya yazar.

      fprintf(ptliste3,"%s\t%s\t%s\t%s\t%s\t%s\t%s\n",kisiler.adi,kisiler.soyadi,kisiler.ceptel_num,kisiler.istel_num,kisiler.evtel_num,kisiler.eposta, kisiler.dogum);
   }

fclose(ptliste);
fclose(ptliste3);

remove("mertrehber.txt");
rename("silmemertrehber.txt","mertrehber.txt");

}



