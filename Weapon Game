#include <iostream>
#include <string>

class Oyuncu; 

class Silah {
    public:
        int mermiSayisi;
        int hasar;

        virtual void atesEt(Oyuncu& hedef) = 0;

        void oyunBasliyor() {
            std::cout << "Oyun basliyor..." << std::endl;
        }
};

class Aex : public Silah {
    public:
        Aex() {
            mermiSayisi = 30;
            hasar = 15;
            std::cout << "Aex silahi alindi." << std::endl;
        }

        void atesEt(Oyuncu& hedef) override;
};

class Trin : public Silah {
    public:
        Trin() {
            mermiSayisi = 10;
            hasar = 25;
            std::cout << "Trin silahi alindi." << std::endl;
        }

        void atesEt(Oyuncu& hedef) override;
};

class Zaow : public Silah {
    public:
        Zaow() {
            mermiSayisi = 50;
            hasar = 5;
            std::cout << "Zaow silahi alindi." << std::endl; 
        }

        void atesEt(Oyuncu& hedef) override;
};

class Oyuncu {
    public:
        std::string isim;
        int yas;
        std::string cinsiyet;
        int can = 100;

        Silah* silah = nullptr;

        void bilgiAl() {
            std::cout << "Oyuncunun ismini giriniz: ";
            std::cin >> isim;

            std::cout << "Yasinizi giriniz: ";
            std::cin >> yas;

            if (yas > 15) {
                std::cout << "Cinsiyetinizi giriniz (Erkek - E / Kadin - K): ";
                std::cin >> cinsiyet;
            }
            /*
            if (yas < 15) {
                std::cout << "Yasiniz 15'ten kucuk, oyuna katilamazsiniz!" << std::endl;
            } else {
                std::cout << "Oyuncu bilgileri alindi." << std::endl;
            }
            */
        }
    
        void silahSec() {
            std::cout << isim << " isimli oyuncu silah secimi yapacak (1 - Aex, 2 - Trin, 3 - Zaow): ";
            int secim;

            while (true) {
                std::cin >> secim;

                if (std::cin.fail()) {
                    std::cin.clear(); 
                    std::cin.ignore(10000, '\n'); 
                    std::cout << "Gecersiz giris! Lutfen sayi giriniz (1 - Aex, 2 - Trin, 3 - Zaow): ";
                    continue;
                }

                if (secim == 1){
                    silah = new Aex();
                    break;
                } else if (secim == 2){
                    silah = new Trin();
                    break;
                } else if (secim == 3){
                    silah = new Zaow();
                    break;
                } else {
                    std::cout << "Gecersiz secim! Lutfen 1 ya da 2 ya da 3 giriniz: ";
                }
            }   
        }

        ~Oyuncu() {
            delete silah;
        }
};

void Aex::atesEt(Oyuncu& hedef) {
    if (mermiSayisi <= 0) {
        std::cout << "Mermi kalmadi!" << std::endl;
        return;
    }

    std::cout << hedef.isim << " kisisine Aex ile ates edildi!" << std::endl;

    hedef.can -= hasar;
    if (hedef.can < 0) hedef.can = 0;

    std::cout << hedef.isim << " kisinin kalan cani: " << hedef.can << std::endl;

    mermiSayisi--;
}

void Trin::atesEt(Oyuncu& hedef) {
    if (mermiSayisi <= 0){
        std::cout << "Mermi kalmadi!" << std::endl;
        return;
    }

    std::cout << hedef.isim << " kisisine Trin ile ates edildi!" << std::endl;

    hedef.can -= hasar;
    if (hedef.can < 0) hedef.can = 0;   

    std::cout << hedef.isim << " kisinin kalan cani: " << hedef.can << std::endl;   

    mermiSayisi--;
}

void Zaow::atesEt(Oyuncu& hedef) {
    if (mermiSayisi <= 0){
        std::cout << "Mermi kalmadi!" << std::endl;
        return;
    }

    std::cout << hedef.isim << " kisisine Zaow ile ates edildi!" << std::endl;

    hedef.can -= hasar;
    if (hedef.can < 0) hedef.can = 0;   

    std::cout << hedef.isim << " kisinin kalan cani: " << hedef.can << std::endl;   

    mermiSayisi--;
}

int main() {

    Oyuncu oyun_baclangici;
    oyun_baclangici.silah->oyunBasliyor();

    Oyuncu oyuncu_1;
    Oyuncu oyuncu_2;

    oyuncu_1.bilgiAl();
    if (oyuncu_1.yas < 15) {
        std::cout << "Oyuncunun yasi 15'ten kucuk oldugu icin oyuna katilamaz." << std::endl;
        return 0;
    }
    oyuncu_2.bilgiAl();
    if (oyuncu_2.yas < 15) {
        std::cout << "Oyuncunun yasi 15'ten kucuk oldugu icin oyuna katilamaz." << std::endl;
        return 0;
    }

    oyuncu_1.silahSec();
    oyuncu_2.silahSec();

    // oyuncu_1.silah->atesEt(oyuncu_2);
    // oyuncu_2.silah->atesEt(oyuncu_1);

    while (oyuncu_1.can > 0 && oyuncu_2.can > 0) {
        oyuncu_1.silah->atesEt(oyuncu_2);

        if (oyuncu_2.can == 0) {
            std::cout << oyuncu_2.isim << " oldu!" << std::endl;
            break;
        }

        oyuncu_2.silah->atesEt(oyuncu_1);

        if (oyuncu_1.can == 0) {
            std::cout << oyuncu_1.isim << " oldu!" << std::endl;
            break;
        }
    }

    if (oyuncu_1.can == 0 && oyuncu_2.can == 0) {
        std::cout << "Berabere!" << std::endl;
    } else if (oyuncu_1.can == 0) {
        std::cout << oyuncu_2.isim << " kazandi!" << std::endl;
    } else {
        std::cout << oyuncu_1.isim << " kazandi!" << std::endl;
    }

    std::cout << "Oyun bitti." << std::endl;


    return 0;
}
