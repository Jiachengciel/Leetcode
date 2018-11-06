 代码：
 ===
 **carte.h**
 ===
    #pragma once
    #include <iostream>

    using namespace std;

    class Carte{

    private:
        int numero;

    public:
        static int nbreDeCartes;
        Carte();
        int getNumero() const;
        virtual void affiche(ostream& s) const=0;
    };

    ostream & operator<<( ostream &s , Carte const & _carte);

    bool carteEstPoint100(Carte* carte);
    bool carteEstPoint50(Carte* carte);
**carte.cpp**
===
    #include "Carte.h"
    #include <iostream>
    #include "EstPoint.h"
    #include "Point.h"


    using namespace std;

    int Carte::nbreDeCartes = 0;

    Carte::Carte(){
        std::cout << "nbre de la carte: " << nbreDeCartes << endl;
        nbreDeCartes++;
        numero = nbreDeCartes;
    }

    int Carte::getNumero() const{
        return numero;
    }

    ostream & operator<<( ostream &s , Carte const & _carte){
        _carte.affiche(s);
        return s;
    }

    bool carteEstPoint100 (Carte* carte)
    {
        EstPoint estPoint;
        if(estPoint(carte))
        {
            Point* point = dynamic_cast<Point*>(carte);
            return (point->getPoints()==100);
        }
        else
        {
            return false;
        }
    }

    bool carteEstPoint50 (Carte* carte)
    {
        EstPoint estPoint;
        if(estPoint(carte))
        {
            Point* point = dynamic_cast<Point*>(carte);
            return (point->getPoints()==50);
        }
        else
        {
            return false;
        }
    }
