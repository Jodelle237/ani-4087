1. Comprendre les trois fonctions

* Avant = direction vers les z négatifs → (0, 0, -1)
* Haut = direction y positif → (0, 1, 0)
* Droite = direction x positif → (1, 0, 0)

Chaque fonction doit retourner un vecteur unitaire, c’est-à-dire un vecteur dont la longueur vaut 1.

2. Ce que le programme doit faire
il doit :

1. Lit trois nombres réels : x, y et z.
2. Les considère comme un point ou vecteur :
    P=(x,y,z)
3. Calcule :
    * P · Avant()
    * P · Haut()
    * P · Droite()
4. Affiche les résultats sur trois lignes, avec quatre chiffres après la virgule.

#include <iostream>
#include <iomanip>
using namespace std;

struct Vecteur3 {
    double x;
    double y;
    double z;
};

// Direction vers l'avant : axe z négatif
Vecteur3 Avant() {
    return {0.0, 0.0, -1.0};
}

// Direction vers le haut : axe y positif
Vecteur3 Haut() {
    return {0.0, 1.0, 0.0};
}

// Direction vers la droite : axe x positif
Vecteur3 Droite() {
    return {1.0, 0.0, 0.0};
}

// Produit scalaire de deux vecteurs
double ProduitScalaire(Vecteur3 a, Vecteur3 b) {
    return a.x * b.x + a.y * b.y + a.z * b.z;
}

int main() {
    Vecteur3 point;

    cin >> point.x >> point.y >> point.z;

    cout << fixed << setprecision(4);

    cout << ProduitScalaire(point, Avant()) << endl;
    cout << ProduitScalaire(point, Haut()) << endl;
    cout << ProduitScalaire(point, Droite()) << endl;

    return 0;
}